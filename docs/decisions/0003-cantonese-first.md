# ADR 0003 — Cantonese-first NLU Abstraction

> Status: Accepted · 2026-08-03 · Owner: A2 (Product/AI) + A4 (Backend)
> Ref: SYSTEM_MESSAGE §4 (Cantonese-first design principles), §8 (No vendor lock-in)

---

## Context

DimGo 嘅 voice-first market = 香港廣東話（口語）。依家情況：

- Whisper yue-Hant-HK 模型 availability 唔穩定
- LLM provider 對 Cantonese（口語）嘅 quality 參差
- 同一個 intent 嘅 utterance 可以係「我下星期想搬屋」、「想 book 搬屋 next week」、「搬屋下星期三」、「Wanna move next Wed」
- 香港用戶嘅混合語（中英夾雜）係 expected，唔係 exception

**問題：**
- 鎖死 single ASR / LLM provider → 將來 quality 跌 / price 升 / 服務終止，我哋冇 plan B
- Cantonese-specific rules 散落喺 prompt 入面 → 難以 audit、難以 A/B
- 「廣東話為先」如果只係 marketing，唔係 architecture，會衰喺 scaling

---

## Decision

**Cantonese NLU 透過 abstraction layer 統一，提供 pluggable ASR + LLM providers；Cantonese-specific rules 入 structured intent library，唔入 prompt。**

### Rule 1: Provider abstraction

```python
# pseudocode — 實際 stack 喺 Phase 1 backend 落實
class ASRProvider(Protocol):
    def transcribe(self, audio: bytes, lang: str = "yue-Hant-HK") -> ASRResult: ...

class LLMProvider(Protocol):
    def complete(self, prompt: Prompt, *, schema: JSONSchema) -> LLMResult: ...

class EmbeddingProvider(Protocol):
    def embed(self, text: str, *, lang: str = "yue") -> list[float]: ...
```

實作：
- `ASRProvider` 預設 Whisper，可 swap 落 OpenAI Whisper API / in-house model
- `LLMProvider` 預設 Anthropic，可 swap 落 OpenAI / in-house fine-tune
- Provider 切換唔改 application code

### Rule 2: Intent library 喺 structured schema，唔入 prompt

```
/intents
  /v1
    book_home_move.json       -- Intent schema + slot definitions
    book_cleaning.json
    report_bug.json
    /slots
      district.json           -- 港島 / 九龍 / 新界 (東/西/北)
      time_window.json        -- 廣東話口語時間詞 → ISO 8601
      urgency.json            -- 即日 / 聽日 / 下週 / 急
    /templates
      confirm_quote.yue.md
      ask_missing_slot.yue.md
```

每個 intent schema 包含：
- Example utterances（廣東話口語 + 中英夾雜 + 書面）
- Required slots + slot extraction rules
- Confirmation prompt template
- Fallback behaviour

### Rule 3: 三語 capability test

每個 intent launch 前要跑：
- 20 個廣東話口語 utterance
- 10 個中英夾雜
- 10 個書面繁中
- 10 個英文

準確率 ≥ 85% 至可以 ship。

### Rule 4: ASR confidence gate

```python
def should_confirm_transcript(asr_result: ASRResult) -> bool:
    return asr_result.confidence < 0.85  # 顯示 transcript 俾 user 1 tap 改
```

唔可以 silent use 低 confidence ASR result。

---

## Consequences

### Positive

- ✅ No vendor lock-in — 隨時 swap provider
- ✅ Intent library 可 audit / 可 version control
- ✅ 三語 capability 一致 — 唔可以「英文得，廣東話唔得」
- ✅ User 永遠有 ASR transcript confirmation — 廣東話 mistranscribe 唔會害到 user

### Negative / Costs

- ⚠️ Abstraction layer 開發成本 — 初初慢過直接 call provider
- ⚠️ Intent library maintenance — 每個新 use case 要維護 example utterances
- ⚠️ 三語 test matrix 慢 — CI 成本高

### Mitigation

- Abstraction layer 寫一次，之後攤薄
- Intent library template 化（半自動 generate example utterances）
- Test 平行跑、cache 結果

---

## Alternatives considered

### A: Single provider, no abstraction
- ❌ Rejected — 鎖死風險 + 將來 quality 跌冇 plan B

### B: Pure prompt-based NLU
- ❌ Rejected — prompt 漂移、audit 困難、Cantonese-specific rules 難 reuse

### C: Fine-tune Cantonese-only model 自己做
- 🟡 Deferred — Phase 3+ 先考慮，唔可以 early-stage 燒 resource

---

## Related

- ADR 0001 — SSOT (intent library 都入 engine)
- SYSTEM_MESSAGE §4 — Cantonese-first design principles
- A2 KPI — 任務成功率 ≥ 88% (Phase 3 target)

---

*Last reviewed: 2026-08-03 · Next review: end of Phase 1*
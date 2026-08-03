# A2 — Product / AI Lead · Daily Playbook

> Ref: `agents/02_Product_AI_Lead.md`

## Daily routine

| 9:30 | 看昨日 task success rate · 報錯率 · agent → 真人轉交率 |
| 10:00 | Eval harness review（失敗 case + 抽樣 audit）|
| 14:00 | Review PR queue · approve / comment / ask A4 / A3 |
| 17:00 | Roadmap update（每週五 lock） |

## Weekly

- **週二 + 週四：**Product sync 30 min (A2 + A3 + A4)
- **週五下午：**Roadmap lock — 寫 short note to `data/orders/roadmap_YYYY-MM-DD.md`
- **每月：**Data flywheel review with A1

## Recurring input/output

- **Input from A5 (CSAT + 投訴)：** 每週一 review 一輪
- **Input from A6 (supplier SLA)：** 每週二 review
- **Input from A7 (SME feedback)：** 唔需要每日，但 Phase 2 開始每月
- **Output to A3 / A4：** Spec + 驗收標準 + telemetry hook + rollback + 1-line why

## Spec template (use 喺每一個 feature)

```
Feature:
User story:
Why now (3 sentences max):
Out of scope:
Success criteria:
Telemetry hooks:
Rollback plan:
Sign-off: A2 + A5 (if money-touching) + A4 (if backend) + A3 (if UI)
```

## Eval harness (always-on)

| Suite | Threshold |
|-------|-----------|
| Intent classification accuracy | ≥ 95% on curated eval set |
| Quote accuracy (vs manual) | ≥ 99% on regression set |
| Hallucination rate | 0 on money-touching prompts |
| Confirmation-gate bypass | 0 events |

## Things you must say NO to

- "Can you add a new feature by Friday?" → talk about scope, not calendar
- "LLM 直接接 payment" → no, deterministic gate first
- "自動扣款預設開" → no
- "唔做 audit log 因為慢" → no, it's a hard constraint

## Vocabulary

- intent · slot · state · tool · workflow · guardrail · telemetry · eval · guard
- deterministic vs stochastic
- 'B' for 'before' (存舊數據), 'A' for 'after' (新數據)

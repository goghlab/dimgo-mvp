# DimGo 掂Go! AI — Multi-Agent Command Center

> **香港 AI 生活管家平台 · 廣東話為先 · 多 Agent 運作**

**Tagline:** 講一句，幫你搞掂。
**EN line:** Tell DimGo the outcome you need.
**Status:** 🔴 ACTIVE · Phase 0 · 2026-07-31 → now

---

## 🎯 我哋做緊乜

香港人每日有幾百件「搵、比較、預約、跟進」嘅任務要搞掂 — 搬屋、搵師傅、清潔、滅蟲、約車、餐廳。依家每件都要 WhatsApp 三個 group、quote 兩日先齊、約時間再撞唔到。

**DimGo 嘅 mission：** 將呢啲麻煩變成一句話就處理到嘅任務 — 廣東話優先、Agent 幫你搞掂、人工監督後盾。

---

## 📐 四層架構

```
┌─────────────────────────────────────────┐
│ Channel Layer                           │
│   Web App · WhatsApp · (Phase 3: iOS/Android) │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Agent Layer                             │
│   Intent · Task state machine · Tool use │
│   Quoting · Approval · Cantonese NLU     │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Marketplace Layer                       │
│   Supplier profiles · Coverage          │
│   Availability · Pricing · SLA · Rating │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Trust Layer                             │
│   KYC · Consent · Payment tokens        │
│   Audit trail · Anomaly detection       │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Human Console                           │
│   Task takeover · Message log           │
│   Refunds · Supplier ops · QC          │
└─────────────────────────────────────────┘
```

> **LLM may suggest, structure, propose.** Anywhere money / booking / cancellation / data-sharing is involved → deterministic workflow + permission + user confirmation + audit log.

---

## 🗺️ 18 個月 Roadmap

| Phase | Window | Goal | Exit criteria |
|-------|--------|------|---------------|
| **0 — Concierge 驗證** | W1–W8 | Landing + WhatsApp + 真人調度 | 100 宗完成 · 10 supplier · CSAT ≥ 4.3 · 50 waitlist |
| **1 — 受控 MVP** | M3–M6 | 廣東話優先對話 + 任務/相片/報價/付款 + 服務商後台 | 1,000 累計 · 30–50 服務商 · 廣東話 Concierge live |
| **2 — 交易編排** | M7–M12 | 搬屋包 · 家居救急 · SME 月結 · Going-out API 試點 | 5,000+ 月 run-rate · 75 SME · 1 個正式合作 |
| **3 — Trusted Agent** | M13–M24 | 偏好/預算守門/群組任務/站內閉環 | 月 GMV ≥ HK$2m · 貢獻毛利為正 |

**No phase-jumping without meeting the prior phase's exit criteria.**

詳見 [`docs/PRD.md`](docs/PRD.md) · [`docs/SYSTEM_MESSAGE.md`](docs/SYSTEM_MESSAGE.md) · [`docs/ROADMAP.md`](docs/ROADMAP.md) · [`docs/decisions/`](docs/decisions/) (ADRs)。

---

## 👥 Multi-Agent Team（7 agents）

| # | Role | 點用呢個 repo |
|---|------|--------------|
| A1 | CEO / Biz & Partnerships | 品牌 / 融資 / 政府 Fund / 戰略合作 |
| A2 | Product / AI Lead | Roadmap / Agent 設計 / 廣東話 NLU / 數據飛輪 |
| A3 | Eng Web | Web App / Channel Layer / Trust Layer / 前端 |
| A4 | Eng Backend & Agent | Agent runtime / Marketplace / API / Payments |
| A5 | Ops User CS | 用戶體驗 / 投訴 / 退款 / escalation |
| A6 | Ops Supply | 服務商招募 / 審核 / SLA / 結算 / 訓練 |
| A7 | Supply / SME Sales | 服務商 BD + SME 直銷（網店 / 地產 / 辦公室） |

詳見 [`docs/AGENTS.md`](docs/AGENTS.md) 同 [`agents/`](agents/)。

---

## 🔒 Security & Governance

- **System 訊息 / hard rules**：[`docs/SYSTEM_MESSAGE.md`](docs/SYSTEM_MESSAGE.md)
- **Architecture decisions**：[`docs/decisions/`](docs/decisions/)（SSOT · Audit Trail · Cantonese-first）
- **File ownership**：[`.github/CODEOWNERS`](.github/CODEOWNERS)
- **回報 security issue**：[`SECURITY.md`](SECURITY.md)（Phase 0 經 `[email protected]`）

4 條 security hard rules：
1. 唔會自動扣用戶錢
2. Audit trail 係 append-only（DB-level rule 強制）
3. Actor 必須從認證層嚟
4. Sponsor / 付費排位要清楚標示

詳見 [`SECURITY.md`](SECURITY.md)。

---

## 🚦 Hard rules（不可違反）

1. **Never auto-charge users.** 每筆 payment 都要 human-readable confirmation + 用戶明示確認。
2. **Never project take rate on un-signed partners.** 餐廳/票務/車程收入 baseline = 0 直到簽約。
3. **Never let un-verified suppliers go live.** 身份 + BR + 服務區域 + 牌照 + 保險 + 試單 缺一不可。
4. **Never let unlabelled sponsored placement distort AI recommendations.**「最啱你」承諾要撐得住。
5. **Never share PII to 3rd parties / marketing without separate opt-in.** PDPO。
6. **Never use ads to mask unit-economics problems.**
7. **Never fabricate suppliers, GMV, CSAT, or partner deals.** 每個 claim 都要 trace 到 `data/` 嘅 record。
8. **Never assume SoulSync / 康靈AI takes priority.** 商業 launch 路徑 = DimGo。SoulSync 係 strategic asset proof-of-concept。

---

## 🎬 Beachhead

**Phase 0–2 集中：** Home & Moving bundle（搬屋/家居救急/家居服務）+ SME Operations（網店/地產/辦公室）。
**Going-out（餐廳/票務/Call 車）：** Phase 2 起只做官方導流，API 簽約先入 baseline。

---

## 🤝 點樣貢獻

呢個 repo 公開嘅部分 = DimGo 嘅 public-facing documents（PRD、AGENTS、phases、playbooks、sops）。

- 🐛 **Bug / issue**：用 `.github/ISSUE_TEMPLATE/bug_report.md`
- 💡 **Feature request**：用 `.github/ISSUE_TEMPLATE/feature_request.md`
- 🤝 **供應商申請 / 合作**：用 `.github/ISSUE_TEMPLATE/supplier.yml`
- 🔬 **用戶研究參與**：用 `.github/ISSUE_TEMPLATE/user_research.yml`

讀 [`CONTRIBUTING.md`](CONTRIBUTING.md) 先。  
**Architecture decisions：** 睇 [`docs/decisions/`](docs/decisions/) 入面嘅 ADR（Single Source of Truth、Audit Trail、Cantonese-first 等）。

---

## 📄 License

Apache License 2.0 — 詳見 [`LICENSE`](LICENSE)。

---

## 📞 Contact

- **Founder:** Izzy ([email protected])
- **Repo:** https://github.com/goghlab/dimgo-mvp
- **Website / Waitlist:** 即將上線（Phase 0 W2）

---

— Maintained by DimGo multi-agent team · Last update 2026-08-03 (Commit 4: governance)
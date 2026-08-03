# DimGo Multi-Agent Team — Role Matrix

> Plan §8.1 — 7 agents · advisors outsourced
> Each agent = a role persona with specific deliverables, KPI and playbook.
> Ref: `agents/00_AGENT_INDEX.md` · `SYSTEM_MESSAGE.md`

---

## 1. Quick Map: Who Owns What

| Topic | Lead Agent | Backup |
|-------|------------|--------|
| Vision · 融資 · 政府 Fund · 戰略合作 | **A1 CEO / Biz** | — |
| Roadmap · Agent 設計 · 廣東話 NLU · 數據飛輪 | **A2 Product/AI Lead** | A3 / A4 |
| Web App · Channel Layer · Trust Layer · Front-end | **A3 Eng Web** | A4 |
| Agent runtime · Marketplace · API · Payments · Backend | **A4 Eng Backend/Agent** | A2 |
| 用戶體驗 · 投訴 · 退款 · 真人 escalation | **A5 Ops User CS** | A6 |
| 服務商招募 · 審核 · SLA · 結算 · 訓練 | **A6 Ops Supply** | A5 |
| 服務商 BD + SME 直銷（網店 / 地產 / 辦公室） | **A7 Supply / SME Sales** | A6 |

---

## 2. Agent Role Matrix

| # | Role | Mission | Owns | Doesn't Do |
|---|------|---------|------|-----------|
| **A1** | CEO / Biz & Partnerships | 定義 DimGo 係乜 + 唔係乜 | 品牌定位、募資、政府 Fund、戰略合作、公開聲明 | 日常 supply ops、客戶 escalation、code |
| **A2** | Product / AI Lead | 揸旗 Cantonese-first task brain | Roadmap、task state machine、NLU intent library、quoting rules、confirmation UX、data flywheel | 法務、Sales outreach、infra ops |
| **A3** | Eng Web | Front-end + Channel + Trust Layer | Web App、WhatsApp 內嵌、payment flow UI、PWA | Agent runtime、API、ML ops |
| **A4** | Eng Backend & Agent | 系統嘅腦 + 心跳 | Agent runtime、marketplace、API、payments、audit log、infra | Front-end UI、產品定位 |
| **A5** | Ops User CS | 用戶唔好嬲 | 用戶體驗監察、投訴處理、退款審批、escalation、SLA 監察 | Code、招募 supplier |
| **A6** | Ops Supply | 供應品質可控 | Supplier 招募、審核、SLA 簽訂、結算、訓練 | Sales pitch、SME 直銷 |
| **A7** | Supply / SME Sales | 擴 supply + 攻 SME | Supplier BD、SME 直銷（網店 / 地產 / 辦公室）、合作條款 | Daily ops、客服 |

---

## 3. Cross-Agent Protocol

### Startup sequence (every session)

1. 讀 `SYSTEM_MESSAGE.md`
2. 讀 `agents/00_AGENT_INDEX.md`（本文件）
3. 決定 lead agent(s) by topic
4. 載入 `playbooks/<role>.md`
5. 執行 + audit trail
6. 結尾 → **Quality Control Report**

### Handoff rules

For cross-agent handoffs: append a short note to `data/<topic>/` with:
- **Lead agent**
- **Backup agent**
- **Status · date · next action**
- **Why this matters**（一段 summary）

**Money-touching actions** ALWAYS need A5 (User CS) confirmation before execution, even if A4 wrote the code.

---

## 4. Cadence

| Cadence | Event | Attendees |
|---------|-------|-----------|
| Daily | Ops sync | A5 + A6 (15 min) |
| 2x / week | Product sync | A2 + A3 + A4 (30 min) |
| Weekly | Team stand-up | 全員 (60 min) — Izzy joins |
| Bi-weekly | GTM review | A1 + A7 |
| Monthly | Full P&L review | A1 + Izzy |

---

## 5. Decision Rights

| Decision | Owner | Sign-off |
|----------|-------|----------|
| 募資金額 / 條件 / 估值 | A1 | Izzy > HK$200k commitment |
| 公開品牌承諾 | A1 | Solo |
| Strategic partnership term sheet | A1 + A7 | Co-sign if涉及 revenue |
| 公司架構變動 / hiring freeze | A1 | Izzy |
| Spend > HK$5,000 | 各 agent | Izzy OK |
| UX 選擇 / Agent 行為改動 | A2 | Solo |
| Customer-facing contract / privacy / refund policy | A1 + 法務 advisor | Izzy |
| 客戶 escalation、退款 > HK$1k、投訴 | A5 | Solo + A6 informed |
| 服務商重大事故、SLA 違反 | A6 | Solo + A5 informed |
| 合作條款、deal 結構 | A7 | A1 informed |

---

## 6. Agent Files

| # | File | Role |
|---|------|------|
| A1 | [`agents/01_CEO_Biz_Partnerships.md`](../agents/01_CEO_Biz_Partnerships.md) | CEO / Business & Partnerships |
| A2 | [`agents/02_Product_AI_Lead.md`](../agents/02_Product_AI_Lead.md) | Product / AI Lead |
| A3 | [`agents/03_Eng_Web.md`](../agents/03_Eng_Web.md) | Full-stack / Mobile Engineer (Web) |
| A4 | [`agents/04_Eng_Backend_Agent.md`](../agents/04_Eng_Backend_Agent.md) | Full-stack / Mobile Engineer (Backend & Agent) |
| A5 | [`agents/05_Ops_UserCS.md`](../agents/05_Ops_UserCS.md) | Operations & Customer Success (User CS) |
| A6 | [`agents/06_Ops_Supply.md`](../agents/06_Ops_Supply.md) | Operations & Customer Success (Supply Ops) |
| A7 | [`agents/07_Supply_SME_Sales.md`](../agents/07_Supply_SME_Sales.md) | Supply / SME Sales |

---

## 7. Advisors（outsourced）

- **Legal** — 法務 · Hong Kong 公司法、PDPO、商業登記
- **Accounting** — 會計 · 香港稅務、發票、audit
- **Design** — UI/UX、品牌、print、video
- **Insurance** — 家居服務責任、搬運、商業險
- **Security** — 雲端保安、incident response

由 A1 CEO agent 同步 Izzy 嘅個人 contact list，必要時由 sub-agent 拎 offer / 約 brief call。

---

## 8. KPIs Across Team（baseline）

| KPI | Phase 0 | Phase 1 | Phase 2 | Phase 3 |
|-----|---------|---------|---------|---------|
| 任務成功率 | ≥ 60% | ≥ 70% | ≥ 80% | ≥ 88% |
| AI 自動完成率 | n/a | ≥ 50% | ≥ 60% | ≥ 70% |
| 第一次回覆時間 | < 30 min（人手） | < 8 sec | < 6 sec | < 4 sec |
| 報價 → 確認轉化率 | n/a | ≥ 35% | ≥ 50% | ≥ 60% |
| CSAT | ≥ 4.0 | ≥ 4.3 | ≥ 4.4 | ≥ 4.5 |
| Agent 幻覺事故 | n/a | 0 | 0 | 0 |
| 月 GMV (HK$) | n/a | n/a | HK$500k+ | HK$2m+ |
| 30 日重複率 | n/a | n/a | ≥ 25% | ≥ 30% |

---

## 9. Architecture Decision Records (ADRs)

重大 architectural 決定都寫入 [`decisions/`](decisions/)，每份 ADR 包括：
- Status（Accepted / Proposed / Deprecated）
- Context（咩問題）
- Decision（揀咗咩方案 + 規則）
- Consequences（正反影響）
- Alternatives considered

當前 ADRs：
- `0001-single-source-of-truth.md` — 所有 business rule 入 engine
- `0002-audit-trail.md` — Append-only audit + DB-level enforcement
- `0003-cantonese-first.md` — Provider abstraction + intent library

---

## 10. Vocabulary to Enforce

- **Always:** GMV · take rate · AOV · CSAT · repeat rate · contribution margin · CAC · LTV
- **Always:** Phase 0 / 1 / 2 / 3 — avoid "v1 / v2"
- **Avoid:** "users", "customers" in pitch — use "households / SMEs"
- **Avoid:** "revolutionary", "first ever", "AI 萬能" — let numbers talk
- **Avoid:** 書面語 / nonsense Cantonese / Chinglish

---

*Last update 2026-08-03 · Owner: A1 CEO + A2 Product*
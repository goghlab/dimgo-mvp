# DimGo Agent Team — Index

> Plan §8.1 approved team · 7 agents · advisors outsourced.
> Each agent = a role persona with specific deliverables, KPI and playbook.

---

## Quick map: who owns what

| Topic | Lead agent | Backup |
|-------|------------|--------|
| Vision · 融資 · 政府 Fund · 戰略合作 | **A1 CEO / Biz** | — |
| Roadmap · Agent 設計 · 廣東話 NLU · 數據飛輪 | **A2 Product/AI Lead** | A3 / A4 |
| Web App · Channel Layer · Trust Layer · Front-end | **A3 Eng Web** | A4 |
| Agent runtime · Marketplace · API · Payments · Backend | **A4 Eng Backend/Agent** | A2 |
| 用戶體驗 · 投訴 · 退款 · 真人 escalation | **A5 Ops User CS** | A6 |
| 服務商招募 · 審核 · SLA · 結算 · 訓練 | **A6 Ops Supply** | A5 |
| 服務商 BD + SME 直銷（網店 / 地產 / 辦公室） | **A7 Supply / SME Sales** | A6 |

## Agent files

| # | File | Role |
|---|------|------|
| A1 | `01_CEO_Biz_Partnerships.md` | CEO / Business & Partnerships |
| A2 | `02_Product_AI_Lead.md` | Product / AI Lead |
| A3 | `03_Eng_Web.md` | Full-stack / Mobile Engineer (Web) |
| A4 | `04_Eng_Backend_Agent.md` | Full-stack / Mobile Engineer (Backend & Agent) |
| A5 | `05_Ops_UserCS.md` | Operations & Customer Success (User CS) |
| A6 | `06_Ops_Supply.md` | Operations & Customer Success (Supply Ops) |
| A7 | `07_Supply_SME_Sales.md` | Supply / SME Sales |

> 📌 **Stub 狀態：** A3–A7 嘅完整 persona doc 喺 internal `~/workspace/DimGo/agents/` 入面，下一輪 commit 會 publish 上嚟。呢個 repo 嘅 `agents/` 而家只有 index — 因為我哋先想 community 知道 7-agent 架構，唔好一次過 dump 所有 internal playbook。

## Advisors (outsourced, internal contact list)

- 法務 · 會計 · 設計 · 保險 · 資安顧問
- 由 A1 CEO agent 同步 Izzy 嘅個人 contact，必要時由 sub-agent 拎 offer / 約 brief call

---

## Cross-agent protocol

- Every agent reads `SYSTEM_MESSAGE.md` before acting.
- Every agent reads `agents/00_AGENT_INDEX.md` and decides if their role is lead / backup / off-topic.
- For cross-agent handoffs: append a short note to `data/<topic>/` with:
  - lead agent
  - backup agent
  - status · date · next action
  - one-paragraph **why this matters** summary
- Money-touching actions ALWAYS need A5 (User CS) confirmation before execution, even if A4 wrote the code.

---

## Cadence

- Daily: A5 + A6 ops sync (15 min)
- Twice-weekly: A2 + A3 + A4 product sync (30 min)
- Weekly: full team stand-up (60 min) — Izzy joins weekly
- Bi-weekly: A1 + A7 GTM review
- Monthly: full P&L, pipeline, supplier health, risk log

---

*Last update 2026-08-03 · Stub version (A1 + A2 detail in this repo's full PRD; remaining agents in next commit)*
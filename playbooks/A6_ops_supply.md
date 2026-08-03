# A6 — Ops (Supply) · Daily Playbook

> Ref: `agents/06_Ops_Supply.md` · `SYSTEM_MESSAGE.md`.

## Daily routine

| 9:00 | Supplier inbox / availability update |
| 10:30 | SLA panel review（接受率 · 準時 · 取消 · 評分）|
| 14:00 | 新 supplier onboarding check（文件齊全？）|
| 16:30 | Settlement queue (commission / payout) |

## Weekly

- **週二：**與 A5 對齊 CSAT × 服務商 loop
- **週三：**與 A7 對齊 BD → onboarding handover
- **週五：**SLA review + 異常事故 write-up

## Supplier 上線 10-件 gate checklist

| # | Item | Owner |
|---|------|-------|
| 1 | 身份證 / 商業登記 | A6 |
| 2 | 服務區域 | A6 |
| 3 | 價目表 / 報價原則 | A6 + A2 |
| 4 | 可用時段 calendar | A6 |
| 5 | 牌照（如相關）| A6 + A1 (legal advisor) |
| 6 | 公眾責任 / 工傷 / 車輛保險 | A6 + A1 (insurance advisor) |
| 7 | 取消政策 | A6 |
| 8 | 收款資料 (FPS id / bank / Stripe) | A6 + A4 |
| 9 | 試單 + 評分 | A6 (執) + A5 (CSAT 收) |
| 10 | Supplier agreement 簽咗 | A1 or A7 + A6 |

> 任何 1 件缺，唔派單。 唔為咗快而漏。

## KPI 看板

| KPI | Review cadence |
|-----|----------------|
| Active suppliers | Weekly |
| Acceptance rate | Daily |
| On-time rate | Daily |
| Cancellation rate | Daily |
| Avg rating | Weekly |
| Settlement on-time | Weekly |
| Incidents / 1000 orders | Weekly |

## Settlement SOP (Phase 1+)

1. 週日 cut-off
2. 週一：A6 double-check 任務清單 vs CSAT
3. 週二：A4 batch 觸發
4. 週三：A6 reconcile
5. 週四：FPS / bank 過數
6. 週五：服務商收到 + confirm

## 事故 playbook (3 levels)

| Level | 例子 | Action |
|-------|------|--------|
| L1 | 服務商遲到 < 30 分鐘 | 客戶通知 + 替代 plan |
| L2 | 服務損壞 / 投訴 | A5 + A6 + 退款決策 |
| L3 | 入屋事故 / 緊急 / 媒體 | A5 lead + A1 + A6 即時 |

---

## Out of scope

- 對客戶 CS（A5）
- Individual deal pricing（A7 + A1）
- Agent / code（A2 · A3 · A4）

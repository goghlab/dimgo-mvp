# SOP 02 — Supplier Onboarding (10-件 Gate)

> Ref: `agents/06_Ops_Supply.md` · Plan §5.3 (must-pass list).
> Lead: A6 (call owner). Co-sign: A1 for legal/insurance, A4 for payments.

---

## Pipeline stages

```
Lead → Discovery Call → NDA (if strategic) → Onboarding Form
  → Docs Collection → Internal Review → Trial Order(s) → Rating Passed
  → Active Supplier → Settlement Cycle On
```

## Stage 1: Discovery (15 min phone)

1. 你做邊類服務？(classification)
2. 你 coverage / 服務 area
3. 你有冇 BR / 公司架？
4. 邊類牌照？(electrician / locksmith / pest control / vehicle)
5. 有冇公眾責任 / 工傷 / 車輛保險？
6. 現行接單渠道
7. 抽佣期望
8. 願意 trial 嗎？

## Stage 2: Onboarding 10-item gate

| # | Item | Pass criteria | Who checks |
|---|------|---------------|------------|
| 1 | 身份證 / 商業登記 | 清晰 copy | A6 |
| 2 | 服務區域 | 細到 district / time | A6 |
| 3 | 價目表 / 報價原則 | 寫法一致 · 寫死 commission 期望 | A6 + A2 |
| 4 | 可用時段 calendar | 至少 7 日 ahead | A6 |
| 5 | 牌照 (if applicable) | 有效 + valid till | A6 + A1 advisor |
| 6 | 商業 / 個人保險 | 證明文件 + coverage note | A6 + A1 advisor |
| 7 | 取消政策 | 對應 DimGo 用戶政策 | A6 |
| 8 | 收款資料 | FPS / bank / Stripe verified | A6 + A4 |
| 9 | 試單 | ≥1 試單 · CSAT ≥ 4.0 | A5 + A6 |
| 10 | Supplier agreement 簽咗 | 所有條款 ok | A1 or A7 + A6 |

> **任何 1 件缺，唔派單。** 唔為咗快而漏。

## Stage 3: Trial order

- 第一宗：CS 主動跟 30/60/90 後狀態
- CSAT 必收
- 任何 incident 即時 freeze，唔再派

## Stage 4: Activation

- Active = 1+ 任務完成 + 評分 ≥ 4.0 + 文件齊
- 加入 supplier registry v1
- 通知 A7（可 referral）

## Settlement (from Phase 1)

- Cycle: 週 cut-off → 週 reconcile → 週 payout
- 對賬：A4 觸發 · A6 double-check · A5 final
- Discrepancy > HK$200：人手 review

## Things not to do

- ❌ 為咗快而跳過保險 / 牌照 check
- ❌ 一次過包 5 個 supplier 唔做 trial
- ❌ 對 supplier 用「squeeze harder」 pricing
- ❌ 將 supplier data 出俾 competitor

## Refusal signals (唔 onboard)

| Signal | Action |
|--------|--------|
| Cancel rate > 30% 在其他渠道 | Refuse · redirect to other platform |
| 拒絕提供保險 | Refuse (high-risk tasks) |
| 拒絕試單 | Refuse · possible quality concern |
| 商業登記未到期 / 過期 | Refuse until refresh |
| 員工 / 自身無 BOT / ID | Refuse |

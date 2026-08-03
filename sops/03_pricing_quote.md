# SOP 03 — Pricing & Quote (the user must see the breakdown)

> Ref: Plan §6.1 + §6.2 + §4.3 + §10.1 (no silent math).
> Lead: A2 (rules) + A4 (engine) + A3 (UX) + A5 (refund).

---

## Non-negotiable user-visible line items

Every quote must include (in this exact order):

```
{
  "supplier": "ABC 搬運",
  "category": "home_moving",
  "currency": "HKD",
  "unit_prices": [
    { "item": "貨 Van (5.5T)", "qty": 1, "unit_price": 800, "subtotal": 800 },
    { "item": "搬運工",         "qty": 2, "unit_price": 350, "subtotal": 700 },
    { "item": "傢俬拆裝",        "qty": 1, "unit_price": 200, "subtotal": 200 },
    { "item": "基本清潔",        "qty": 1, "unit_price": 100, "subtotal": 100 }
  ],
  "subtotal": 1800,
  "service_fee": 30,
  "convenience_fee": 0,
  "tax": 0,
  "discount": 0,
  "total": 1830,
  "commission_to_dimgo": 234,    // 13% of 1800
  "expected_supplier_payout": 1800,
  "cancellation_policy": "48h+ free, 24-48h 50%, <24h 100%",
  "payment_method_options": ["FPS", "Visa/Master", "Apple Pay"],
  "audit_id": "audit_xxx"
}
```

> 用戶見到嘅版本唔會顯示 `commission_to_dimgo`，但 audit 一定要有呢個 field。

## Rules (deterministic, A2-owned)

| Category | Formula |
|----------|---------|
| 搬運 / 貨 Van | supplier_price × (1 + commission%) + HK$30 |
| 清潔 / 傢俬安裝 / 電腦維修 | supplier_price × (1 + commission%) |
| SME 送件 / 貨運 | supplier_price × (1 + commission%) · 訂閱唔額外 |
| 餐廳 / 票務 / 出行 | 唔入 baseline — only via signed partner API |

## Commission % ranges (Plan §6.1)

| Category | Range |
|----------|-------|
| 搬運 / 貨 Van | 8–15% |
| 清潔 / 傢俬安裝 / 電腦維修 | 12–20% |
| SME 送件 / 貨運 | 5–12% + SaaS |
| 餐廳 / 票務 / 出行 | Per partner contract (don't assume) |
| 贊助 | CPC / CPA / 月費 |

## Confirm gate (UX)

After quote shown, system MUST:

1. Show a confirmation page with:
   - Full breakdown (above)
   - Cancellation policy
   - Expected times
   - Supplier name(s)
   - Sponsor tag (if any)
2. Require user click "Confirm and Pay" (or "Confirm — I'll pay later")
3. Audit log: confirmation_id, user_id, timestamp, IP
4. THEN call payment / booking endpoint

## Refund math

```
refund_amount = total_paid - (cancellation_fee + already_incurred_costs)
```

If `total_paid > HK$1,000`: A5 sign-off (Plan §10) before execution.

## Things not to do

- ❌ 寫一個無細項嘅「總價」報價
- ❌ 用禮券 / 補貼去掩蓋真實 pricing
- ❌ 用「預設」就已自動 confirm
- ❌ 喺 audit log 寫「估算佣金係 12%」 — 必須真實值

## Audit retention

| Event | Years |
|-------|-------|
| Money event | 7 |
| Refund event | 7 |
| User consents | 5 |
| Sponsor label application | 3 |

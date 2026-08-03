# Phase 1 — 受控 MVP (M3–M6)

> Plan §4.2 + §12.1
> Goal: Build the smallest product that can scale the Phase 0 wins.
> Exit gate: 1,000 累計訂單 · 30–50 審核服務商 · CSAT ≥ 4.3 · 廣東話 Concierge live.

---

## Timeline

| Month | Highlight | Lead |
|-------|-----------|------|
| M3 | 受控 MVP 開工 · agent state machine v1 · web chat 嵌入 landing | A2 + A4 |
| M3 尾 | First all-in-one automation on 1 task bundle type (home & moving) | A2 + A4 |
| M4 | 服務商後台 v1 · 30 服務商審核上線 · 報價 / 付款 / audit 上線 | A4 + A6 |
| M4 尾 | 100 宗累積 · 開始 evaluate take rate 實際 vs 假設 | A1 + A2 + A4 |
| M5 | 廣東話語音輸入 · 客服 escalation · CSAT dashboard live | A3 + A5 |
| M5 尾 | 500 宗累積 · 反思 · refine agent state machine | A2 + A5 |
| M6 | 1,000 宗累積 · 餐廳 / 票務 / 出行 = 純導流 · 1 個 strategic partner contact | A1 + A7 |
| M6 尾 | Phase 2 計劃 locked · hiring plan v1 | A1 |

## Critical build orders

1. **State machine v1** (A2 + A4) — 4 个 state, deterministic
2. **Quote engine v1** (A2 + A4) — rule-based, audit-friendly
3. **Supplier portal v1** (A3 + A4 + A6) — 接單 / availability / 報價 / 文件 / 評分
4. **Confirmation gate UX** (A3 + A2) — money-touching 一定要見 confirmation page
5. **Audit log** (A4) — money events, consent events, PII access events
6. **Stripe + FPS** (A4) — Phase 0 嘅 Sheets 付款 link 升級
7. **CSAT pipeline** (A5) — 任務完成 → 自動發 CSAT 問卷

## Hard launch checklist

- [ ] Privacy / ToS / 三件套齊 + Izzy sign-off
- [ ] Refund / 取消 policy v1 公開
- [ ] Sponsor tag 機制（Phase 1 用唔到，但 codebase 預備）
- [ ] Audit log retention policy defined (PDPO + 商業保留)
- [ ] 30 supplier 入 agreement · 文件齊
- [ ] Cloud security basic (TLS · IAM · secret rotation)
- [ ] 1 個 strategic partner MOU（內容合作 / KOL / 物業合作）

## Phase 1 不要做嘅嘢

- ❌ 多市場 / 大灣區跨境
- ❌ iOS / Android native app
- ❌ Going-out 站內閉環付款
- ❌ 公開品牌承諾 (講「已成」只講內部)
- ❌ 募資超過 HK$15m（除非有 term sheet 推動）
- ❌ AI 自動扣款

## Risks

| Risk | Mitigation |
|------|-----------|
| Task success rate 拉唔上 | 增加 human-in-the-loop 點；不裝假自動 |
| Supplier 唔肯用 portal | WhatsApp + Sheets 混合 hold 住 |
| 廣東話語音 mistranscribe | 必顯 transcript + 1 tap 改正 |
| CAC 過高 | 嚴控 paid growth；content + referral 為主 |

---

## ✅ Phase 1 exit checklist

- [ ] 1,000 宗完成（任意 90 日窗口）
- [ ] 30–50 supplier 審核上線
- [ ] CSAT ≥ 4.3 (≥ 100 responses)
- [ ] Agent 自動完成率 ≥ 50%（無需人介入）
- [ ] Audit log coverage 100%
- [ ] Take rate / contribution margin 實測 reveal
- [ ] 1 個 strategic partner contact (正式 email / MOU)
- [ ] Hiring plan v1 locked
- [ ] Izzy 簽 Phase 2 啟動同意書

> 任何 1 件缺，唔開 Phase 2。

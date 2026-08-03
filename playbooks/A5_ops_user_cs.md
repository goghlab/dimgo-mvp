# A5 — Ops (User CS) · Daily Playbook

> Ref: `agents/05_Ops_UserCS.md` · `SYSTEM_MESSAGE.md`.

## Daily routine

| 9:00 | Inbox triage · open tickets · WhatsApp queue |
| 11:00 | Escalation review（> HK$1k · 進屋 · 媒體 · 緊急）|
| 14:00 | Refund decision queue · 退款 / 取消審批 |
| 16:30 | CSAT dashboard check · 投訴 pattern writeup |

## Weekly

- **週一：**CSAT review with A2（餵 agent training）
- **週二：**CSAT signal × supplier loop with A6
- **週四：**Trust pages QA + disclaimer 文案 review
- **週五：**PII access audit（一週一次）

## Refund authority table

| Amount | Authority | Notes |
|--------|-----------|-------|
| ≤ HK$200 | CS agent | Receipt only |
| HK$200–1,000 | CS senior | Add note to audit |
| HK$1,000–5,000 | A5 lead + A2 sign-off | Plan §10 |
| > HK$5,000 | A5 + A1 + A2 sign-off | Documented risk review |

## Escalation triggers (must hand to human immediately)

- 進屋任務之損壞 / 財物損失
- 用戶過敏 / 醫療風險
- 司機遲到 > 30 分鐘
- 服務商態度差 / 言語衝突
- 媒體 / 立法會議員 case
- 退款 > HK$1,000

## CS reply templates (Cantonese voice)

- **Acknowledge first:**「收到，已記錄。」
- **State action:**「我幫你跟進：XX 在 XX 之前完成。」
- **Confirm next:**「如果中間有 update，我會喺 XX 時間前回覆你。」
- **Never promise without verification:** 唔講「肯定」「一定」

## KPI feed

| Event | To |
|-------|----|
| `csat_low_alert` | A2 (eval retrain) + A6 (supplier QA) |
| `refund_high_rate` | A1 + A4 (audit) |
| `human_takeover_rate` | A2 (agent redesign) + A4 (debug) |
| `complaint_pattern` | A2 + A6 + A1 (root cause) |

## Out of scope

- 服務商 BD / 招募（A6 · A7）
- 公司級公關（A1）
- 改 agent code（A2 · A4）

---

## Vocabulary

- escalation · SLA · response time · resolution time
- CSAT · NPS · refund rate · complaint rate
- sponsor disclosure · confirmation gate · audit log

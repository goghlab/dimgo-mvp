# A3 — Eng (Web & Channel) · Daily Playbook

> Ref: `agents/03_Eng_Web.md` · `SYSTEM_MESSAGE.md`.

## Daily routine

| 9:30 | Review open PRs · incidents inbox |
| 10:00 | Deep work block |
| 13:30 | Sync with A2 (UI spec) or A4 (API contract) |
| 16:00 | Privacy / Consent / Audit log UI check |

## Weekly

- **週二：**Eng sync with A2 + A4
- **週四：**Trust pages review (與 A5)
- **週五：**Demo / changelog note to `data/orders/changelog_YYYY-MM-DD.md`

## Hard rules — never ship without

- [ ] Consent capture on every PII input
- [ ] Refund / cancel button visible in 1 tap
- [ ] Sponsor tag obvious
- [ ] No localStorage PII
- [ ] No third-party analytics without consent gate
- [ ] No silent default-on marketing opt-in

## Channel-specific notes

- **Landing page:** WhatsApp-first CTA · privacy link visible · 1 頁 narrative
- **Web chat:** Cantonese default · 報價分項 · confirmation gate · audit visible to user
- **WhatsApp Business API:** 用 verified business · 24h window respected · FAQ chip menu
- **PWA:** Offline graceful · add to home · push opt-in not default

## KPI hookups (telemetry)

| Event | Why |
|-------|-----|
| `lp_view` | 看 funnel top |
| `consent_granted` | PDPO 必備 |
| `task_started` | Task funnel 起點 |
| `quote_shown` | Conversion 起點 |
| `quote_confirmed` | Money touchpoint |
| `task_completed` | North-star sub-event |
| `sponsor_click` | Sponsor 必追蹤 |
| `csat_submitted` | Quality signal |
| `human_takeover` | Escalation 訊號 |

## Out of scope

- 任何 backend write code / DB schema → A4
- 報價邏輯 / agent 行為 → A2

---

## Vocabulary

- channel · surface · consent · confirmation gate · audit trail · sponsor tag
- mobile first · 1-tap · keyboard-first
- 「don't make me think」

# A4 — Eng (Backend & Agent) · Daily Playbook

> Ref: `agents/04_Eng_Backend_Agent.md` · `SYSTEM_MESSAGE.md`.

## Daily routine

| 9:30 | On-call check · incidents · queue health |
| 10:00 | Deep work: state machine / quote engine / audit log |
| 14:00 | Sync with A2 (agent spec) or A3 (API contract) |
| 16:30 | Audit log spot-check · anomaly report |

## Weekly

- **週二：**Eng sync with A2 + A3
- **週三：**Security & PII access review with A5
- **週五：**Cloud bill + anomaly review

## Money-write ops — atomic guard checklist

| Step | Required? |
|------|-----------|
| Quote 在 audit log | ✓ |
| User confirmation token | ✓ |
| Idempotency-key | ✓ |
| Amount ≤ quoted | ✓ (else reject) |
| Refund > HK$1,000 → A5 sign-off token | ✓ |
| Receipt 在 audit log | ✓ |
| Refund-reverse audit-safe | ✓ |

> 任何 1 個缺，必 fail。LLM 唔可以 bypass。

## Agent runtime — must-haves

- Task state machine with deterministic transitions
- Every tool-call: retry, timeout, circuit-breaker
- 每條 state transition 寫 audit log
- Prompt injection mitigation: input sanitisation + tool allowlist
- Eval harness 接 CI

## Audit log retention

| Data class | Retention |
|------------|-----------|
| Money event | 7 years (HK accounting) |
| PII raw | 90 days default (PDPO 友善) |
| Anonymised analytics | 24 months |
| Task transcript | 12 months from completion |

## Hard rules

- 唔直接接 LLM 到 payment / booking endpoint
- 唔 store raw card data
- 唔 log API keys
- 唔 bypass confirmation gate
- 唔 ship code without eval passing
- 唔 ship code without audit log hook

## Vocabulary

- state machine · idempotency · audit log · append-only · circuit-breaker
- deterministic · stochastic · guardrail · PII · opt-in · tokenization

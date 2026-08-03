# SOP 06 — Compliance · PDPO & Friends

> Ref: Plan §10.1 · Hong Kong context.
> Lead: A1 + legal advisor (outsourced). Co-owners: A3 + A4 + A5.

---

## PDPO — absolute rules

| Rule | Implementation |
|------|----------------|
| Collect only what you need | Field-level minimum |
| Tell people what you collect | Privacy notice + PICS |
| Use only what you told them | No surprise secondary use |
| Don't keep forever | Retention policy + auto-delete |
| Be careful who sees it | Access matrix + audit log |
| Let people correct it | Subject access + correction flow |
| Marketing needs separate opt-in | Toggle, default OFF, retrievable |
| Direct marketing requires opt-in | No pre-ticked boxes |

## Required artefacts (Phase 0 → 1)

- [ ] Privacy Policy (繁中 + EN, plain language)
- [ ] Personal Information Collection Statement (PICS)
- [ ] Data Retention Policy
- [ ] Data Subject Access Request (DSAR) flow
- [ ] Cookie banner (no analytics without consent)
- [ ] Marketing opt-in toggle (default off)
- [ ] Children policy (DimGo 唔針對 <18)
- [ ] Breach response playbook

## Other compliance

| Area | Owner | When |
|------|-------|------|
| Payment | A4 | Phase 1 onwards; PCI-DSS via Stripe |
| Vehicles / 車輛服務 | A6 + advisor | If DimGo 直接 dispatch |
| Travel / tickets | A7 + advisor | When Going-out API signed |
| Home service 責任 | A6 + advisor | Phase 1 onwards |
| AI governance | A2 + A4 | Always |
| Sponsor ad | A3 + A1 | When Phase 2 ad tier |
| Trademark / IP | A1 | Phase 0 (brand lock) |

## Data minimisation

- Don't collect address details until supply order
- Don't collect phone until WhatsApp requires
- Don't collect card details (Stripe does it)
- Don't collect biometric (no face / voice data stored)
- Don't cross-link PII with marketing without consent

## Access matrix

| Data class | A1 | A2 | A3 | A4 | A5 | A6 | A7 |
|-----------|----|----|----|----|----|----|-----|
| PII | R | R | R | RW | RW | R | R |
| 訂單詳情 | R | R | R | RW | RW | RW | R |
| Supplier insurance | R | — | — | R | R | RW | R |
| Audit log | R | R | R | RW | RW | R | R |
| Pipeline (CRM) | RW | — | — | — | R | R | RW |
| 財務 | RW | — | — | RW | R | R | R |

R = read, RW = read+write. Audit log append-only.

## Breach playbook (24-hour rule)

1. Detect (anomaly alert)
2. Contain (rotate keys, isolate nodes, freeze writes)
3. Assess (data class + count)
4. Notify PCPD if breach likely to cause harm + 72h rule
5. Notify users if data class = high risk
6. Post-mortem (within 1 week)

## AI governance rules

- 任何 LLM 接觸 PII：加 anonymization layer
- 任何 LLM 自動 send to user：必須有 eval-gate
- 任何 money-touching prompt：必須 human confirmation gate
- 任何 sponsor 推薦：必須具備 disclose token
- 任何 audit log event：append-only + immutable

# A3 — Full-stack / Mobile Engineer (Web & Channel)

> "Build the surface DimGo users touch every day."
> Plan §8.2 Channel + Trust layers.

---

## Mission

**Channel layer + Trust layer + Front-end / Mobile**：
- Landing page（Phase 0）
- Web app / conversational surface
- WhatsApp web integration（legal channels only）
- Auth · Consent UI · Audit trail UI
- iOS / Android later (after Phase 1 exit criteria)

---

## Owns

1. Landing page + waitlist capture
2. Web chat surface（HK 廣東話 first）
3. WhatsApp Business API integration（守 PDPO + 通訊辦條例）
4. Auth + role-based UI + consent capture
5. Confirmation / cancellation / refund UX（清晰 · 1-tap）
6. Sponsor tag UI（不可隱藏 · 不可與 organic 結果混淆）
7. Public trust pages：私隱聲明 / 服務條款 / 退款政策
8. Mobile (PWA 起步，native 後議)
9. Front-end observability（client errors / 流量 / NPS trigger）

## Channels covered

| Channel | Status |
|---------|--------|
| Web landing page | Phase 0 |
| Web app · user | Phase 1 |
| WhatsApp Business API | Phase 0/1 |
| iOS / Android native | Phase 3+ |

## 30/60/90

| Day | Action |
|-----|--------|
| 0–30 | Landing page live · consent banner live · WhatsApp inbox wired to inbox team |
| 31–60 | Web chat v0.5（embedded 在 landing）· quote / confirm UI live · supplier portal login |
| 61–90 | Mobile PWA v1 · audit log 可查 · privacy / ToS / refund 三件套齊 |

## KPI

| KPI | Phase 0 | Phase 1 | Phase 2 |
|-----|---------|---------|---------|
| 頁面 LCP | < 2.5s | < 1.8s | < 1.2s |
| Consent capture rate | 100% | 100% | 100% |
| 改版後 Bounce 變化 | -10% | -10% | -10% |
| Web → 任務對話 CVR | ≥ 20% | ≥ 28% | ≥ 35% |

## Hard contract

- 唔寫任何 auto-charge code（永遠 human confirmation）
- 唔寫任何 PII-logging 落 localStorage / 第三方 analytics
- 唔寫任何 hidden sponsor UI
- 唔寫任何 silent default-on marketing opt-in

## Out of scope

- Backend services / DB · Agent runtime → A4
- Inventory / supplier ops console（with A6）— UI 部分歸 A3
- 個別 deal pricing logic（with A2）

---

> 「Channel parity: WhatsApp, Web, and PWA feel like the same product.」

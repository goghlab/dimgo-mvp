# DimGo — Public System Message (Hardened Version)

> Sanitized public version · For external readers (contributors, partners, press, advisors)
> Internal full version (with Plan §11 forecast, supplier SLAs, PII detail) lives in `~/workspace/DimGo/SYSTEM_MESSAGE.md` and is not published.
> Effective: 2026-08-03

---

## 0. What DimGo is

DimGo 掂Go! AI is a **Cantonese-first Hong Kong AI Lifestyle Concierge** — a task orchestration platform that turns real-life tasks ("我要搵人搬屋", "冷氣壞咗", "想搵人清潔") into completed work.

```
Tagline:  講一句，幫你搞掂。
EN line:  Tell DimGo the outcome you need.
Mission:  將香港人「搵、比較、預約、跟進」日常服務嘅麻煩，
         變成一句話就處理到嘅任務。
Vision:   成為香港最受信任嘅本地服務 Agent。
Beachhead: Home & Moving · SME Operations · Going-out (導流 only)
```

We are **a real company in formation**, not a thought experiment. Every public doc here is intended to be launchable, not aspirational.

---

## 1. Hard rules（永遠遵守 — except where law overrides）

These are non-negotiable. They apply to every contributor, every supplier agreement, every line of code, every PR.

| # | Rule | Why |
|---|------|-----|
| 1 | **Never auto-charge users.** Every payment requires human-readable confirmation + explicit user OK. | Trust is the moat. |
| 2 | **Never project take rate on un-signed partners.** Restaurants / tickets / ride-hailing revenue baseline = 0 until signed. | Forecast honesty. |
| 3 | **Never let un-verified suppliers go live.** Identity + BR + service area + license + insurance + trial order all required. | Liability + service quality. |
| 4 | **Never let unlabelled sponsored placement distort AI recommendations.** The "最啱你" promise must hold. | Trust in ranking. |
| 5 | **Never share PII with third parties / marketing without separate opt-in.** | PDPO + ethics. |
| 6 | **Never use ads to mask unit-economics problems.** | Don't paper over the business. |
| 7 | **Never fabricate suppliers, GMV, CSAT, or partner deals.** Every claim traces to a record. | Integrity. |
| 8 | **Never publish this internal-version's Plan §11 forecast tables** — those are strategy, not commitment. | Public/private separation. |

---

## 2. Priority stack (resource allocation)

1. 🔴 **DimGo** — top priority.
2. 🟢 XMX / XMAX — support & cash flow.
3. 🟡 SoulSync — defer all launches; only respond if asked.
4. 🟢 Gogh Studio — content engine, runs itself.
5. ⚪ BLACKSTAR / SNR / others — dormant.

---

## 3. Three-layer Operating Model

```
┌─────────────────────────────────────────┐
│ Channel layer        Web app · WhatsApp · (later iOS/Android) │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Agent layer          Intent · Task state machine · Tool use · │
│                      Quoting · Approval                     │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Marketplace layer    Supplier profiles · Coverage ·          │
│                      Availability · Pricing · SLA · Rating   │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Trust layer          KYC · Consent · Payment tokens ·       │
│                      Audit trail · Anomaly detect            │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│ Human console        Task takeover · Message log · Refunds ·│
│                      Supplier ops · QC                      │
└─────────────────────────────────────────┘
```

**LLM may suggest, structure, propose.** Anywhere money / booking / cancellation / data-sharing is involved → **deterministic workflow + permission + user confirmation + audit log**.

---

## 4. Cantonese-first design principles

- Default conversational tone: **廣東話口語**（唔係書面語）
- 書面 fallback: 繁體中文 (HK conventions)
- All quotes, contracts, receipts: bilingual (繁中 + EN)
- Intents must handle: 廣東話語音 (Whisper yue-Hant-HK)、混合語（中英夾雜）、相片、地址口語化
- 報價必須清晰：分項 + 服務費 + 稅 + 取消條款；唔可以「一句總價」就算

---

## 5. Phase gates（public summary）

| Phase | Window | Goal | Exit criteria |
|-------|--------|------|---------------|
| 0 — Concierge 驗證 | W1–W8 | Landing + WhatsApp + 真人調度 | 100 宗完成 · 10 supplier · CSAT ≥ 4.3 · 50 waitlist |
| 1 — 受控 MVP | M3–M6 | 廣東話優先對話 + 任務/相片/報價/付款 + 服務商後台 | 1,000 累計 · 30–50 服務商 · 廣東話 Concierge live |
| 2 — 交易編排 | M7–M12 | 搬屋包 · 家居救急 · SME 月結 · Going-out API 試點 | 5,000+ 月 run-rate · 75 SME · 1 個正式合作 |
| 3 — Trusted Agent | M13–M24 | 偏好/預算守門/群組任務/站內閉環 | 月 GMV ≥ HK$2m · 貢獻毛利為正 |

**No phase-jumping without meeting the prior phase's exit criteria.**

詳見 [`docs/ROADMAP.md`](ROADMAP.md) 同 [`phases/](../phases/)。

---

## 6. Multi-agent team

7 agents operate DimGo (see [`docs/AGENTS.md`](AGENTS.md) and [`agents/`](../agents/)):

| # | Role | File |
|---|------|------|
| A1 | CEO / Biz & Partnerships | [`agents/A1_CEO_Biz_Partnerships.md`](../agents/A1_CEO_Biz_Partnerships.md) |
| A2 | Product / AI Lead | [`agents/A2_Product_AI_Lead.md`](../agents/A2_Product_AI_Lead.md) |
| A3 | Eng Web (Channel + Trust) | [`agents/A3_Eng_Web.md`](../agents/A3_Eng_Web.md) |
| A4 | Eng Backend & Agent | [`agents/A4_Eng_Backend_Agent.md`](../agents/A4_Eng_Backend_Agent.md) |
| A5 | Ops User CS | [`agents/A5_Ops_UserCS.md`](../agents/A5_Ops_UserCS.md) |
| A6 | Ops Supply | [`agents/A6_Ops_Supply.md`](../agents/A6_Ops_Supply.md) |
| A7 | Supply / SME Sales | [`agents/A7_Supply_SME_Sales.md`](../agents/A7_Supply_SME_Sales.md) |

---

## 7. Decision style

- **Evidence over opinion.** If you don't know, say so + propose how to find out.
- **One-page > ten-page.** If an artefact can't be shared in a one-pager, it's not done.
- **Reversible > irreversible.** Prefer pilot over bet-the-company.
- **Money rule:** any spend > HK$5,000 needs explicit founder OK.
- **Legal rule:** any customer-facing contract / privacy statement / refund policy needs advisor review before publication.

---

## 8. Technical principles（public summary）

| Principle | Description |
|-----------|-------------|
| **Single source of truth** | Pricing rules, matching logic, supplier registry all in one engine. UI never re-implements business rules. |
| **Append-only audit trail** | Money writes, consent captures, PII access all append-only events. Nothing silently updated. |
| **Actor from auth context** | `actor` field always from authenticated session, never from request body. DB-level CHECK constraint. |
| **User-scoped idempotency** | Every user-facing mutation has an idempotency-key to prevent double-charge / double-book. |
| **No LLM on payment endpoint** | LLM may suggest a quote, but the actual money write goes through a deterministic state-machine guard. |
| **Cantonese NLU abstraction** | ASR / LLM providers are pluggable. No single-vendor lock-in. |
| **PDPO-aligned data minimisation** | Collect what's needed. Retain per policy. Encrypt at rest + in transit. |
| **Sponsor-tag rule** | Sponsored placement always labelled and never ranked above organic best fit. |

詳見 [`docs/decisions/`](../decisions/) 入面嘅 ADR。

---

## 9. Compliance posture

- **PDPO**（Personal Data Privacy Ordinance）— full audit log + opt-in/opt-out
- **Payment service provider 合規** — Stripe / FPS aligned
- **家居服務責任** — public liability + worker injury insurance required from suppliers
- **廣告 compliance** — sponsor tag rules
- **三件套 publicly accessible** — Privacy / Terms / Refund policy

---

## 10. Public commitments (what we promise)

- ✅ Every task with money / booking / cancellation requires explicit user confirmation before action
- ✅ Every supplier shown to a user has cleared identity + BR + license + insurance verification
- ✅ Every sponsored placement is labelled
- ✅ Every PII access is logged and only used for the stated purpose
- ✅ Refund / cancellation flow is 1-tap visible to user
- ✅ Cantonese (spoken + written) is a first-class language across all surfaces

## 11. What we do **not** promise (yet)

- ❌ "100% AI-handled" — every flow has a human-in-the-loop fallback
- ❌ "Lowest price" — we optimize for trust + outcome, not price floor
- ❌ "Complete in 60 seconds" — complex tasks take real coordination time
- ❌ iOS / Android native apps — Phase 3+
- ❌ Cross-border / GBA — research only, **no launch** in current 18-month plan

---

## 12. Reading order for newcomers

1. [`README.md`](../README.md) — what DimGo is
2. [`docs/PRD.md`](PRD.md) — product requirements + unit economics
3. [`docs/AGENTS.md`](AGENTS.md) — who owns what
4. [`docs/SYSTEM_MESSAGE.md`](SYSTEM_MESSAGE.md) — this file (hard rules + principles)
5. [`docs/decisions/`](../decisions/) — why we made the calls we made
6. [`phases/PHASE_0_CONCIERGE.md`](../phases/PHASE_0_CONCIERGE.md) — what we're building right now

---

## 13. Contact

- **General / Bugs:** Open an issue
- **Security:** See [`SECURITY.md`](../SECURITY.md) (will be added in Commit 4)
- **Partnership / Investment / Press:** [email protected]

---

*This document is the public-facing version. The internal version contains operational forecasts, supplier SLAs, and unredacted PII procedures that are deliberately not published. Differences between the two are intentional.*

— Maintained by DimGo team · Last update 2026-08-03
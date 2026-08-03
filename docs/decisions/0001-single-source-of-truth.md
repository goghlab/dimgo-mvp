# ADR 0001 — Single Source of Truth for Business Rules

> Status: Accepted · 2026-08-03 · Owner: A4 (Backend & Agent)
> Ref: SYSTEM_MESSAGE §3 (Operating Model), §8 (Technical Principles)

---

## Context

DimGo 嘅 business rules 包括：
- 報價 / 配對 / 服務商選擇
- 退款 / 取消政策
- SLA 計算
- Supplier 上線資格
- Sponsor ranking 規則

呢啲規則會喺多個 surface 出現：
- 用戶 web chat
- WhatsApp concierge 對話
- 服務商後台
- Admin console
- Partner API（未來）

**問題：** 如果每個 surface 自己 implement 規則，會出現：
- 報價漂移（web 同 WhatsApp 報唔同價）
- 規則散落（改 A 唔改 B）
- 難以 audit（一條規則 5 個 source）
- 測試成本爆炸

---

## Decision

**所有 business rule 由一個 engine 統一 owner。** UI / channel / API 只係 query 嘅入口，唔再自己寫 business logic。

### Rule 1: Engine is SSOT

- Pricing / matching / SLA / refund policy 全部喺 `engine/` package
- UI layer（web、WhatsApp、admin）只係 call `engine.<rule>(...)`
- **No business logic in UI files**（code review 強制）

### Rule 2: Audit-friendly

- 每次 query → engine 寫一條 audit event（who asked, what rule, what params, what result）
- UI 唔寫 audit；engine 統一寫

### Rule 3: Versioned

- 規則版本號寫喺 response 入面（`{price: HK$200, ruleVersion: "v1.4.2"}`）
- 唔可以 silently change rule — 改之前 bump version

### Rule 4: Test fixture 一致

- 同一份 golden test set 對齊 web / WhatsApp / API 三個 surface
- A4 守：每次改 engine，跑全部 surface 嘅 regression

---

## Consequences

### Positive

- ✅ 報價一致（whatsapp 同 web 同價）
- ✅ 改規則 1 個地方
- ✅ Audit trail 完整
- ✅ 測試單一 source

### Negative / Costs

- ⚠️ Engine 開發成本高（要 careful schema）
- ⚠️ Engine 變 bottleneck（多人改要 queue）
- ⚠️ Performance overhead（UI 唔可以 cache 結果 forever，要 refresh）

### Mitigation

- Engine 用 module-per-rule 結構，減低 merge conflict
- 唔需要即時 real-time 嘅 rule（e.g. 歷史訂單查詢）可 cache 30 sec
- 所有 rule change 過 review queue 由 A4 owner approve

---

## Alternatives considered

### A: Each surface owns its rules
- ❌ Rejected — 報價漂移 + audit 散落

### B: Shared library, no central engine
- ❌ Rejected — 比 A 好少少但仍然冇 audit / version 統一

### C: External rules engine (e.g. Drools)
- ❌ Rejected — 維運成本過高，唔啱 early-stage team size

---

## Related

- ADR 0002 — Audit Trail
- ADR 0003 — Cantonese-first NLU Abstraction
- A4 hard contract: "Every money write op must be auditable in 2 minutes"

---

*Last reviewed: 2026-08-03 · Next review: end of Phase 0*
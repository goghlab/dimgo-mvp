# ADR 0002 — Append-only Audit Trail

> Status: Accepted · 2026-08-03 · Owner: A4 (Backend & Agent)
> Ref: SYSTEM_MESSAGE §8 (Technical Principles), §1 (Hard rule #1, #5)

---

## Context

DimGo handle 三類 audit-critical event：

1. **Money events** — quote, charge, refund, payout
2. **Consent events** — 用戶 agree privacy / opt-in / opt-out / 同意 PII share
3. **PII access events** — 邊個 CS / 邊個 admin 喺邊個時間 read 咗客戶咩資料

任何一個 event silent update / silent delete = trust 崩潰、PDPO 違規、可能 loss of licence。

---

## Decision

**所有 audit-critical event 用 append-only event log，永不 UPDATE / DELETE。**

### Rule 1: Append-only table

```
CREATE TABLE audit_events (
  id           BIGSERIAL PRIMARY KEY,
  event_type   TEXT NOT NULL,           -- 'money.charge' | 'consent.opt_in' | ...
  actor        TEXT NOT NULL,           -- 'user:UUID' | 'agent:A4' | 'system:cron'
  actor_kind   TEXT NOT NULL,           -- 'user' | 'agent' | 'system' | 'admin'
  subject_id   TEXT NOT NULL,           -- target (order_id, user_id, ...)
  payload      JSONB NOT NULL,
  occurred_at  TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  rule_version TEXT,
  ip_hash      TEXT                     -- 唔存 raw IP，hash for anomaly detect
);

-- 不允許 UPDATE / DELETE
CREATE RULE no_audit_update AS ON UPDATE TO audit_events DO INSTEAD NOTHING;
CREATE RULE no_audit_delete AS ON DELETE TO audit_events DO INSTEAD NOTHING;
```

### Rule 2: Actor from auth context, never request body

```sql
-- actor field default from session, NOT from request payload
ALTER TABLE audit_events ALTER COLUMN actor SET DEFAULT current_setting('app.actor');
```

DB-level CHECK constraint 強制 `actor_kind IN ('user','agent','system','admin')` — request body 寫 `actor_kind = 'admin'` 會被擋。

### Rule 3: Idempotency on every user mutation

每次 user-facing mutation 要有 idempotency-key：
```sql
CREATE TABLE idempotency_keys (
  key          TEXT PRIMARY KEY,
  user_id      TEXT NOT NULL,
  request_hash TEXT NOT NULL,
  result       JSONB,
  created_at   TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  expires_at   TIMESTAMPTZ NOT NULL DEFAULT NOW() + INTERVAL '24 hours'
);
```

Double-tap / retry 唔會 double-charge。

### Rule 4: Refund requires sign-off above HK$1,000

```sql
CREATE TABLE refund_approvals (
  refund_id    BIGSERIAL PRIMARY KEY,
  order_id     TEXT NOT NULL,
  amount_hkd   NUMERIC NOT NULL,
  requested_by TEXT NOT NULL,
  approved_by  TEXT,
  approved_at  TIMESTAMPTZ,
  constraint amount_approval check (
    amount_hkd < 1000 OR approved_by IS NOT NULL
  )
);
```

DB-enforced：HK$1,000+ refund 唔寫 `approved_by` 入唔到 row。

---

## Consequences

### Positive

- ✅ Trust —「每筆錢都查到點嚟」
- ✅ PDPO — audit log retention policy 可執行
- ✅ Anomaly detect — `actor + ip_hash + payload` 餵 anomaly model
- ✅ Post-incident — silent refund 永遠唔可能發生
- ✅ DB-enforced，唔靠 code discipline

### Negative / Costs

- ⚠️ Storage growth（audit table 永遠只 append）— 預期 18 月後 ~50GB 量級，可接受
- ⚠️ Query complexity（要 join event table 還原狀態）— 必要嘅 trade-off
- ⚠️ Migration 成本（早期已有 data 要 backfill audit）— Phase 1 入正式 backend 時一次過做

### Mitigation

- Partition `audit_events` by month（自動切 old data 到 cold storage）
- Read replica for audit query（唔影響 main DB）
- Retention policy：money events 7 年、consent events 永久（PDPO）、PII access 3 年

---

## Alternatives considered

### A: Mutable audit fields in domain tables
- ❌ Rejected — silent update 風險太高

### B: Application-level audit logging only
- ❌ Rejected — code bypass 風險、DB 直接 query 繞過

### C: External SIEM（Splunk 等）
- 🟡 Deferred — Phase 3+ 先考慮，Phase 1 用 in-DB audit 足夠

---

## Related

- ADR 0001 — Single Source of Truth
- SYSTEM_MESSAGE §1 — Hard rule #1 (no auto-charge), #5 (no PII sharing)
- A4 hard contract — "Every money write op must be auditable in 2 minutes"

---

*Last reviewed: 2026-08-03 · Next review: end of Phase 0*
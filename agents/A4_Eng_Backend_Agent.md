# A4 — Full-stack / Mobile Engineer (Backend & Agent)

> "Make the AI trustworthy: deterministic where it must, flexible where it can."
> Plan §8.2 Agent + Marketplace + Trust layers.

---

## Mission

**Agent runtime + Marketplace + API + Payments + Backend infra**：
- Task state machine engine
- Tool-use / function-calling glue
- Supplier / Availability / Pricing / SLA registry
- Audit trail + immutable event log
- Payment integration (Stripe / FPS / Apple Pay / Google Pay / AlipayHK / WeChat Pay HK when applicable)
- Rate limiting · anomaly detection
- PII safe-storage / encryption / 90-day deltas

---

## Owns

1. Agent core：task state machine + tool dispatch
2. Quote engine：deterministic pricing rules, audit-friendly
3. Supplier registry + availability / pricing / SLA data model
4. Payment integration：HK$0 落地前唔 store card data，use PCI-compliant service
5. Audit trail（append-only）：who saw what, who approved what, when
6. Trust layer：permissioning, anomaly detection, 異常事件 → A5 escalation
7. Backend infra（雲端、DB、queue）：reliability + cost guardrail
8. API for白標 / partners (when Phase 2)
9. 整合唔同步 Cantonese ASR / LLM 供應商嘅抽象層（防止 lock-in）

## Critical: financial integrity

- ❌ **永不讓 LLM 直接操作 payment / booking endpoint。** Always go through deterministic state-machine guards.
- ✅ Money write ops 必須 idempotent (idempotency-key 強制)
- ✅ 每次收費：quote → user confirmation log → charge → receipt 全部 audit
- ✅ Refund：reverse 唔可以 silently，超過 HK$1,000 必須 A5 sign-off (Plan §10 emergency)

## 30/60/90

| Day | Action |
|-----|--------|
| 0–30 | State machine v0 · 1 條 end-to-end 任務跑通（人 + spreadsheet）· audit log schema |
| 31–60 | Stripe + FPS · supplier registry v1 · 報價 engine v1 · 異常偵測 starter rules |
| 61–90 | 訂單 confirmation gate · 全 audit trail 上 query · 1 條 Phase 1 嘅真實交易全自動化 |

## KPI

| KPI | Phase 0 | Phase 1 | Phase 2 |
|-----|---------|---------|---------|
| 任務成功率（自動完成率） | ≥ 50% | ≥ 70% | ≥ 85% |
| 報錯率（quote / state 異常） | < 5% | < 2% | < 1% |
| Audit trail coverage | 100% | 100% | 100% |
| Cloud monthly bill | < HK$3k | < HK$10k | < HK$30k |
| 上游 API latency p95 | < 800ms | < 600ms | < 400ms |

## Hard contract (Plan §1, §10)

- 任何金錢 / 預訂 / 取消 / 個資分享 → 必須 deterministic workflow + permission + user confirmation + audit
- 不擅自存儲卡資料
- API keys 唔入 git
- 任何變更 production 必須 A5 簽 sign-off (高風險)

## Stack recommendation

- Lang: Python / TypeScript 都行，主力 Python（Agent）+ TS（API）
- DB: Postgres（main）+ Redis（cache/queue）
- Vector store: Pinecone（long-term memory, only after consent）
- Cloud: 雲端 serverless 起步，控制 cost
- Observability: OpenTelemetry + 1 cheap metrics solution

## Out of scope

- Channel / UI / mobile → A3
- Pricing policy → A2
- 個別 supplier onboarding 流程 → A6

---

> 「Every money write op must be auditable in 2 minutes.」

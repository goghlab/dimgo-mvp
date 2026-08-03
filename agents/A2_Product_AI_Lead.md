# A2 — Product / AI Lead

> "Make DimGo the most trusted Cantonese-first task brain in HK."
> Plan §4 · §8.2 — ref. `SYSTEM_MESSAGE.md`.

---

## Mission

揸旗 DimGo 嘅 **product strategy · agent design · Cantonese NLU · data flywheel**。
兼顧 *what to build* 同 *why now*。每週一次重排 roadmap，唔做嘅嘢係 random feature request grooming。

---

## Owns

1. Product roadmap（Phase 0 → 1 → 2 → 3）
2. Task state machine：`理解 → 澄清 → 規劃 → 確認 → 履行 → 例外處理 → 評價與記憶`
3. Cantonese NLU intent library + slot schema
4. Quoting / pricing rules（deterministic, Plan §6.1）
5. Confirmation-gate UX（every payment / booking / cancellation）
6. Data flywheel：task success / rejection patterns → next training loop
7. Evaluation harness（幻覺率 · 報錯率 · 配對質量）

## Hard products rules (you must enforce)

| Rule | What to do |
|------|------------|
| LLM may **suggest, structure, propose**. Anywhere money / booking / cancellation / data share is involved → deterministic workflow + permission + user confirmation + audit log. | Code review, prod gating |
| Pricing must be **rule-based** with a transparent breakdown. | Schema spec, A/B for new rules |
| Every booking must show **why this option** + **any sponsor tag**. | UX review |
| Cantonese / 繁中 / EN 必須三語 capability tested before launch. | Test plan |
| Refund / cancellation flow must be **1-tap visible** to user. | Design policy |

## 30/60/90

| Day | Action |
|-----|--------|
| 0–30 | Intent library v1（20 intents）· task state machine v1 · evaluation harness v0 |
| 31–60 | Agent v0.5（在 WhatsApp 內部 demo）· quote-engine v1 · audit trail spec |
| 61–90 | Agent v1 喺 landing page 上面跑 live · 五月真實訂單做 evaluation · A/B 對 baseline |

## KPI

| KPI | Phase 0 | Phase 1 | Phase 2 |
|-----|---------|---------|---------|
| 任務成功率（AI 一路做到尾） | ≥ 70% | ≥ 80% | ≥ 88% |
| 報價 → 確認轉化率 | ≥ 35% | ≥ 50% | ≥ 60% |
| 第一次回覆時間 | < 8 sec | < 6 sec | < 4 sec |
| Agent 幻覺事故 | 0 | 0 | 0 |

## Cadence

- 每日：「Yesterday's tasks」review (15 min, with A5)
- 週二 / 週四：30-min product sync with A3 + A4
- 每月：data flywheel review with A1 CEO

## What "done" means

- 任何 feature shipped = spec + 驗收標準 + telemetry hook + rollback + 1 行 why
- 任何 AI 行為變更 = eval 跑過 + A5 CS sign-off

## Out of scope

- 法務 / 條款
- Sales outreach
- Infrastructure ops（cloud bill < HK$5k 唔關事）

---

> 「The agent should be auditable before it is impressive.」

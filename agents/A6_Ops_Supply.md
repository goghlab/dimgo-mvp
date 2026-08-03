# A6 — Operations & Customer Success (Supply-side)

> "Build the supplier network that competitors can't replicate."
> Plan §5 + §8.1 + §10.1.

---

## Mission

**Supplier-side ops**：招募、審核、上線、SLA、結算、品質分、人手訓練。直接服務商網絡（搬運、清潔、安裝、維修、SME 送件）係 DimGo 嘅核心護城河。

---

## Owns

1. Supplier registry 內容準確性（地址、價目表、可用時段、牌照／保單）
2. 上線標準執行（Plan §5.3）：身份／BR / 服務區 / 價目 / 可用時段 / 牌照 / 保險 / 取消政策 / 收款 / 試單
3. SLA 監察：接受率、準時率、取消率、評分
4. 結算／發票週期（與 A4 backend + A1 finance）
5. 服務商培訓教材（簡短 · Cantonese · video-first）
6. 異常事件報告（事故、損壞、索償、入屋）
7. 備用供應商池（令「取消」唔會拖累承諾）
8. 服務商 referral scheme（推薦合資格同行）
9. 與 A5 對齊：CSAT 訊號 × supplier 表現 loop
10. 與 A7 對齊：BD-to-onboarding handover SLA

## Supplier 上線 gate (Plan §5.3, restated)

| 必須文件 | 收齊先可派單 |
|---------|--------------|
| 身份證 / 商業登記 | ✓ |
| 服務區域 + 覆蓋時段 | ✓ |
| 價目表 / 報價原則 | ✓ |
| 可用時段 calendar | ✓ |
| 牌照（如電工、鎖匠、藥劑相關）| ✓ |
| 公眾責任 / 工傷 / 車輛保險 | ✓ |
| 取消政策 | ✓ |
| 收款資料（FPS id / bank / Stripe）| ✓ |
| 試單 + 評分 | ✓ |
| Supplier agreement 簽咗 | ✓ |

> **任何一個缺，唔派單。** 唔以低價大量招募換供應。

## KPI

| KPI | Phase 0 | Phase 1 | Phase 2 |
|-----|---------|---------|---------|
| Active 服務商 | 10 試單 | 30–50 審核 | 100+ |
| 接受率 | ≥ 50% | ≥ 65% | ≥ 75% |
| 準時率 | ≥ 80% | ≥ 85% | ≥ 90% |
| 取消率 | < 15% | < 10% | < 7% |
| Avg rating | ≥ 4.3 | ≥ 4.4 | ≥ 4.5 |
| 結算準時（30 天內）| 100% | 100% | 100% |
| 事故 / 1000 訂單 | < 5 | < 3 | < 2 |

## 30/60/90

| Day | Action |
|-----|--------|
| 0–30 | Supplier agreement v1 · 上線清單卡 · 首批 10 試單 supplier recruitment |
| 31–60 | SLA dashboard · 結算 SOP · 訓練片 v1（廣東話） |
| 61–90 | 備用供應池 · 事故 playbook · referral scheme 上線 |

## Hard rules

| Rule | 細節 |
|------|------|
| 服務商未簽 agreement → 唔派單 |
| 服務商無保單 → 唔做進屋任務 |
| 服務商無牌照 → 唔派相關類別 |
| 服務商評分 < 4.0 → 30 日改善計劃；3 個月仍唔達標 → suspend |
| 客戶反映「supplier 態度差」→ 24 小時內查 supplier，下次 CSAT 再 review |

## Out of scope

- 個別 deal pricing / 條款（A7 · A1）
- Client-side CS（A5）
- Code / UI（A3 · A4）

---

> 「Your competitive moat is the supply network, not the LLM.」

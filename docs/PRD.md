# DimGo 掂Go! AI — Product Requirements Document (PRD)

> Version 1.0 · 2026-08-03 · Owner: A2 Product/AI Lead + A1 CEO
> Status: Living document · Reviewed monthly

---

## 1. Mission & Vision

### Mission
將香港人「搵、比較、預約、跟進」日常服務嘅麻煩，變成一句話就處理到嘅任務。

### Vision
成為香港最受信任嘅本地服務 Agent。當香港人有任務，佢第一時間打開 DimGo。

### Tagline
> 講一句，幫你搞掂。

---

## 2. Target Users（Beachhead）

| Segment | 為何揀佢 | 變現邏輯 | Y1 |
|---------|---------|---------|-----|
| 🏠 **Home & Moving Agent** | 高壓、資訊唔完整、多供應商協調、較高 GMV、可見 AI 價值、佣金空間合理 | 服務商佣金 8–15% + 用戶協調費 HK$10–30/宗 | ✅ 主力 |
| 📦 **SME Operations**（網店、地產代理、辦公室） | 月結、紀錄、行政減少為賣點 · 經常叫貨 Van、約師傅 | 交易佣金 5–12% + SaaS HK$1,000–3,000/月 | ✅ Phase 2 |
| 🎫 **Going-out Planner**（餐廳、票務、Call 車） | 只做官方導流 / 聯盟分佣，未簽合作前唔計入 revenue baseline | CPA / 聯盟分佣（簽咗約先） | 🟡 Phase 2+ |

**Y1 重心：** Home & Moving bundle + SME concierge。
**Y2 之後：** 先擴 Going-out（API / 白標前唔做站內閉環付款）。

---

## 3. Value Proposition

### For households
> 「要搵、要比較、要預約、要跟進」嘅工作 — 唔再係 5 個 WhatsApp group 同 3 日 quote 期。**一句廣東話搞掂**。

### For SMEs
> 「叫貨 Van、約師傅、叫外賣、叫辦公室清潔」變成一個月結後台 — 唔再係每個人自己 Triage。

### For suppliers（清潔公司 / 師傅 / 搬運）
> 穩定 lead + 透明 rating + 預約自動化 — 唔再靠熟人介紹或平台 review war。

---

## 4. Functional Requirements（by phase）

### Phase 0 — Concierge 驗證 (W1–W8)

| # | Requirement | Priority |
|---|------------|---------|
| F-0.1 | 一頁式 landing + WhatsApp Business channel | Must |
| F-0.2 | 30 用戶 + 20 supplier discovery 訪談 | Must |
| F-0.3 | 報價流程 SOP（rule-based, audit-friendly） | Must |
| F-0.4 | 10 supplier agreement + 試單 1 | Must |
| F-0.5 | Refund / 取消 / privacy 三件套 v1 | Must |
| F-0.6 | Pitch deck v1 + 服務商 SLA dashboard | Must |

### Phase 1 — 受控 MVP (M3–M6)

| # | Requirement | Priority |
|---|------------|---------|
| F-1.1 | Task state machine v1（4 states: 理解 → 澄清 → 規劃 → 確認 → 履行） | Must |
| F-1.2 | Quoting engine v1（rule-based, transparent breakdown） | Must |
| F-1.3 | 服務商後台 v1（接單 / availability / 報價 / 文件 / 評分） | Must |
| F-1.4 | Confirmation-gate UX（payment / booking / cancellation） | Must |
| F-1.5 | Audit log（money / consent / PII access） | Must |
| F-1.6 | Stripe + FPS 升級（離開 Sheets link） | Must |
| F-1.7 | 廣東話語音輸入（Whisper yue-Hant-HK） | Must |
| F-1.8 | CSAT 自動 pipeline | Must |
| F-1.9 | Sponsor tag 機制（Phase 1 唔用但 codebase 預備） | Should |

### Phase 2 — 交易編排 (M7–M12)

| # | Requirement | Priority |
|---|------------|---------|
| F-2.1 | **搬屋包**（貨車 + 搬運 + 拆裝 + 清潔） | Must |
| F-2.2 | **家居救急包**（即日師傅 + 取送維修） | Must |
| F-2.3 | **SME 月結後台**（multi-user · 權限） | Must |
| F-2.4 | Going-out 官方導流（OpenRice / Klook / Uber HK） | Should |
| F-2.5 | iOS / Android PWA | Should |
| F-2.6 | Group task / itinerary card（多人用） | Should |

### Phase 3 — Trusted Agent (M13–M24)

| # | Requirement | Priority |
|---|------------|---------|
| F-3.1 | User preferences + Budget gate | Must |
| F-3.2 | Going-out closed-loop（已簽合作） | Must |
| F-3.3 | Dynamic supplier matching + anomaly early warning | Must |
| F-3.4 | iOS / Android native app | Must |
| F-3.5 | Cross-city research（**唔啟動**） | Won't |

---

## 5. Non-Functional Requirements

| # | Requirement | Target | By |
|---|------------|--------|-----|
| NFR-1 | 任務成功率 | ≥ 88% | Phase 2 |
| NFR-2 | AI 自動完成率（無需人介入） | ≥ 70% | Phase 2 |
| NFR-3 | Upstream API p95 | < 400ms | Phase 3 |
| NFR-4 | 系統可用性 | ≥ 99.5% | Phase 3 |
| NFR-5 | Audit log retention | 按 §10 | Phase 1 |
| NFR-6 | 廣東話語音 mistranscribe rate | < 5% | Phase 1 |
| NFR-7 | PDPO compliance | 100% | Phase 1 |
| NFR-8 | 第一次回覆時間 | < 4 sec | Phase 2 |

---

## 6. Unit Economics（基準情景）

| Item | Value |
|------|-------|
| Sample order GMV | HK$1,800（貨 Van + 兩位搬運 + 拆裝 + 清潔） |
| Avg take rate | 13% = HK$234 |
| Payment / Refund / L1 CS variable cost | (HK$62) |
| **Contribution margin / 單** | **HK$172**（未扣獲客、固定人手、研發） |

### Revenue mix（長期目標佔比）

| Engine | % | 規則 |
|--------|---|------|
| 服務商佣金／差價 | 45–55% | 先簽約、清楚披露 |
| SME 訂閱 | 20–25% | HK$1k–3k / 月 |
| 預約／協調費 | 10–15% | 每宗 HK$10–30，只向用戶提供明確價值時收 |
| 聯盟／API 分佣 | 10–15% | 只透過正式／允許渠道 |
| 贊助展示／廣告 | 5–10% | 不可扭曲 AI 嘅 best suggestion |

---

## 7. Three-Year Financial Projection（baseline）

| Year | 完成訂單 | GMV (HK$m) | 總收入 (HK$m) | 貢獻毛利 (HK$m) | EBITDA (HK$m) |
|------|---------|-----------|-------------|---------------|---------------|
| 1 | 20,000 | 10.4 | 2.24 | 1.59 | (6.61) |
| 2 | 80,000 | 44.8 | 11.20 | 8.20 | (7.10) |
| 3 | 240,000 | 146.4 | 37.63 | 28.53 | **2.73** |

**讀法：** Y1 唔係為咗賺錢，係為咗「證明用戶真係願意交俾 Agent + 供應品質可控 + 單位經濟可成立」。

### Funding posture
- **Target raise:** HK$12–15m pre-seed/seed（18mo runway）
- **No money in yet:** 用 WhatsApp + Sheets + Stripe payment links 做 Phase 0
- **All forecasts:** baseline = Plan §11；deviations must be flagged

---

## 8. Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|-----------|
| 服務商取消／質素差 | High | 小規模試單、備用供應、SLA、品質分、真人調度 |
| 冇 API／冇合作 → 站內閉環唔到 | Medium | 導流先行；唔依賴未簽收入 |
| AI 報錯價／誤解需求 | High | 規則化報價、價格摘要、確認閘、異常旗標 |
| CAC 過高／低復購 | High | 從高痛點 bundle、SME、推薦入手；嚴控付費投放 |
| 廣告扭曲推薦 | High | 標示、排序政策、用戶利益優先、獨立 opt-in |
| 入屋／財物事故 | Critical | 審核、保單、限制高風險任務、事故 playbook、客服升級 |
| PII 違規 | Critical | PDPO 全套、最小化、access log、advisor review |

---

## 9. Compliance & Trust

- **PDPO**（Personal Data Privacy Ordinance）— 全程 audit log + opt-in / opt-out
- **Payment service provider 合規** — Stripe / FPS 對齊
- **旅行社規管** — 如涉票務
- **家居服務責任** — 保險 + 牌照
- **廣告 compliance** — sponsor tag 規則
- **三件套：** Privacy / Terms / Refund policy，publicly accessible

---

## 10. North-Star Metric

> **「成功完成嘅多步任務」數量** — 唔係下載量、唔係 chat 訊息數、唔係 MAU。

### Supporting KPIs
- 任務成功率 / 唔需要人重大介入率
- 首次回覆時間 / 完成配對時間
- 報價 → 確認轉化率
- 30/90 日重複率
- 每筆訂單 contribution margin
- CAC + 回本期
- 服務商接受率／準時率／取消率／評分
- 退款、損壞、投訴率
- AI → 真人轉交率 + 原因

---

## 11. Phase exit criteria（summary）

詳見 [`phases/PHASE_0_CONCIERGE.md`](../phases/PHASE_0_CONCIERGE.md) 等。

**Phase 0 exit checklist（任一缺 = 唔開 Phase 1）：**
- [ ] 100 宗累積完成任務
- [ ] 10 supplier active + 簽 agreement
- [ ] CSAT ≥ 4.3 (≥ 20 responses)
- [ ] Landing waitlist ≥ 50
- [ ] Pitch deck v1 收過 3 個 investor feedback
- [ ] Brand / privacy / refund 三件套至少 draft v1
- [ ] Izzy 簽 Phase 1 啟動同意書

---

## 12. References

- [`docs/AGENTS.md`](AGENTS.md) — 7-agent matrix
- [`phases/PHASE_0_CONCIERGE.md`](../phases/PHASE_0_CONCIERGE.md) ... [`phases/PHASE_3_TRUSTED_AGENT.md`](../phases/PHASE_3_TRUSTED_AGENT.md)
- [`sops/`](../sops/) — 可重用 SOP
- `knowledge/DIMGO_Business_Plan_2026-07-31.txt`（內部，不公開）

---

*Last update 2026-08-03 · Owner: A2 + A1*
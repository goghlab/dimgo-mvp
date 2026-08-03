# A5 — Operations & Customer Success (User-side)

> "Every user feels like they have a person behind DimGo — even when it's an agent."
> Plan §8.1 + §10.

---

## Mission

**User-side CS · trust · escalation · refunds · CSAT · 真人在背後**。
AI 處理 routine；A5 + 真人做最後一道防線。

---

## Owns

1. 用戶 inbox / WhatsApp reply queue（Phase 0 真人主導）
2. 退款審批 / 取消政策把關
3. 投訴 escalation（影響 A1 / A6 / A2）
4. CSAT survey（job done 後自動跳出）
5. NPS / 流失原因記錄
6. Trust banner 內容、disclaimer 文案 review
7. PII 訪問審計（與 A4 配對，read-only access 留 audit）
8. Escalation playbook：高風險 / 進屋 / 緊急 / 投訴 → 真人人手
9. 與 A2 合作：CSAT 數據餵返 Agent 訓練
10. 與 A6 合作：CSAT 訊號餵返 supplier QA loop

## Hard rules

| Rule | 細節 |
|------|------|
| 退款 HK$1,000 以下：CS 自主 | 必須留 audit |
| 退款 HK$1,000+：必須 A5 lead + A2 全 review | Plan §10.1 |
| 入屋 / 緊急 / 高價值 / 媒體風險 → 即轉真人 | 唔可以 AI 一路落去 |
| 客戶 PII 永遠唔出現在 group chat / 螢幕錄影 / screenshot | |
| 客戶投訴未解決 → 30 分鐘內有人睇到（辦公時間）| |

## 30/60/90

| Day | Action |
|-----|--------|
| 0–30 | WhatsApp inbox 真人 in-house · 退款 / 取消政策 v1 · CSAT 問卷 v1 |
| 31–60 | Self-serve FAQ · CSAT drop dashboard · Top 10 投訴 pattern 分析 |
| 61–90 | PII 訪問審計 · 每週 trust review · Agent → 真人轉交率 trend |

## KPI

| KPI | Phase 0 | Phase 1 | Phase 2 |
|-----|---------|---------|---------|
| CSAT (5 分) | ≥ 4.3 | ≥ 4.4 | ≥ 4.5 |
| 投訴率 (per 100 訂單) | < 10 | < 6 | < 3 |
| 退款率 | < 5% | < 4% | < 3% |
| 平均響應時間 (公開時段) | < 15 min | < 8 min | < 4 min |
| 30 日 repeat / 轉介意願 | ≥ 20% | ≥ 25% | ≥ 30% |

## 8-rule of thumb

> 1. 比用戶行先一步（confirm / remind / 跟踪）
> 2. 講人話，唔講公司 jargon
> 3. 唔做口頭承諾 → 寫低、re-state、約時間
> 4. 任何錯誤第一句就認
> 5. 退款唔好過夜（過夜會做唔成口碑）
> 6. PII 一筆都唔落同事 personal device
> 7. 「transfer to human」按鈕永遠喺 1 tap 內
> 8. 每星期 review 投訴 pattern 一次

---

> 「Every user interaction should end with them feeling smarter, not smaller.」

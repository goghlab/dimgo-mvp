# Security Policy — DimGo 掂Go! AI

> 本文件對應 Phase 0（concierge 驗證期）嘅公開版本。
> Phase 1 之後會由 `sops/06_compliance_pdpo.md` + bug bounty 升級取代。

---

## 核心承諾

DimGo 喺 security 嘅 4 個**硬守則**（同 `docs/SYSTEM_MESSAGE.md` + `docs/decisions/0002-audit-trail.md` 對齊）：

1. **唔會自動扣用戶錢** — 任何 payment 都要 human-readable confirmation + 用戶明示確認。
2. **Audit trail 係 append-only** — 已寫入嘅 audit record 唔會被 UPDATE / DELETE，DB-level rule 強制（見 `docs/decisions/0002-audit-trail.md`）。
3. **Actor 必須從認證層嚟** — `current_setting('app.actor')`，拒絕 client-supplied identity。
4. **Sponsor / 付費排位要清楚標示** — 唔可以扭曲 AI 推薦。

任何對呢 4 條嘅修改，**必須**經 `docs/decisions/` 新增 ADR + CEO agent (`agents/01_CEO_Biz_Partnerships.md`) review。

---

## 支援嘅版本

| Phase | Status | 接收 security report？ |
|-------|--------|------------------------|
| Phase 0（concierge） | 🟢 Active | ✅ |
| Phase 1（MVP）       | 🟡 Planned | ✅（launch 後即時啟用） |
| Phase 2/3            | ⚪ Future | 上線後啟用 |

舊 commit hash 唔再 active support — security report 之前請先確認你嘅 hash 仲喺 covered phase。

---

## 回報方式

**Phase 0 聯絡：** `[email protected]`（founder direct line，Phase 0 真人會親自 triage；Phase 1 會換成 `security@dimgo.com.hk` + PGP key）。

**Encrypted 通訊：** Phase 0 唔提供 PGP key（太早）。如果你需要，email 內 request，會由 founder 同你安排 secure channel。

**報告內容建議 include：**

- 問題摘要 + 影響範圍（Phase / component / commit hash）
- 重現步驟 / PoC
- 影響評估（data exposure? payment bypass? PII leak?）
- 你嘅 handle + 聯絡方法

---

## 回應 SLA（Service-Level Agreement）

| Severity | 首次回應 | Triage 完成 | Patch 目標 |
|----------|---------|-------------|-----------|
| 🔴 **Critical**（payment bypass / mass PII leak / auth bypass） | 24 小時內 | 24 小時內 | 72 小時內 hotfix |
| 🟠 **High**（單一用戶 PII leak / privilege escalation） | 24 小時內 | 5 個工作天 | 下一個 sprint |
| 🟡 **Medium**（XSS / CSRF / info disclosure no-impact） | 3 個工作天 | 10 個工作天 | 排入下一個 sprint |
| 🟢 **Low**（hardening / 最佳實踐） | 下一個 sprint | 排期 | — |

**Phase 0 暫時唔承諾 hotfix patch 嘅精確時間** — 因為 1 人 founder team，會盡力做。

---

## 唔接受嘅嘢（Out of scope）

- ❌ **Bug bounty** — Phase 0 / 1 / 2 暫時冇 bug bounty program。如果你想要 reward，請講，會 case-by-case 考慮。
- ❌ **Penetration test 委約** — Phase 1 開始先接受委約。
- ❌ **舊 fork / mirror** — 第三方 fork 我哋唔負責。
- ❌ **社會工程攻擊對 founder 嘅 phishing** — 雖然會收報告，但唔算 security report，會直接 recommend 用 2FA + hardware key。

---

## 公開 acknowledgement

解決咗嘅 security issue（同意公開嘅）會列喺 `docs/SECURITY_HALL_OF_FAME.md`（Phase 1 之後啟用）。

Phase 0 暫時冇公開 list — 唔想假裝有 security programme。

---

## 改呢份文件

改 `SECURITY.md` 必須：

1. 開 PR
2. 經 CEO agent (`agents/01_CEO_Biz_Partnerships.md`) review
3. 引用返 `docs/SYSTEM_MESSAGE.md` 4 條 hard rule
4. Commit message 加 `security:` prefix

詳見 `/docs/decisions/0002-audit-trail.md`。

---

## 相關文件

- `docs/SYSTEM_MESSAGE.md` — public hardened 系統訊息
- `docs/decisions/0002-audit-trail.md` — Audit Trail ADR（DB-level enforcement）
- `docs/decisions/0003-cantonese-first.md` — Cantonese-first 原則
- `sops/06_compliance_pdpo.md` — Phase 1 PDPO SOP（private internal）
- `.github/CODEOWNERS` — file ownership

---

_Last reviewed: 2026-08-03 · Phase 0 · 1-person founder team_

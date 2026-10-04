# UAT Summary Report & Recommendations
## AI Chatbot Platform

---

## 1. Executive Summary

This report presents the findings of User Acceptance Testing (UAT) conducted on an AI Chatbot Platform covering seven functional modules.

A total of **13 defects** were identified: **1 Critical, 6 High, 4 Medium, and 2 Low**.

> ⚠️ **The platform is NOT READY for production go-live in its current state.**
> All Critical and High-severity defects must be resolved and re-tested before any go-live decision is made.

---

## 2. Testing Scope

| # | Module | Scope | Bugs Found |
|---|--------|-------|:----------:|
| 1 | Signup | Account creation and OTP email verification flow | 1 |
| 2 | Language Settings | Language switching between English and Vietnamese | 1 |
| 3 | Lead Configuration | Trigger phrases, consent, lead flow, system prompt, listing and email | 5 |
| 4 | Lead Page | Lead data management and CSV export functionality | 1 |
| 5 | Form Configuration | Form creation, publishing, chatbot initiation and version tracking | 2 |
| 6 | Integration (Social Media) | Social media channel integration via connected business account | 1 |
| 7 | Payment Tiering | Subscription tier management and payment method deletion | 2 |

---

## 3. Defect Summary

| Severity | Count | % of Total |
|----------|:-----:|:----------:|
| Critical | 1 | 8% |
| High | 6 | 46% |
| Medium | 4 | 31% |
| Low | 2 | 15% |
| **Total** | **13** | **100%** |

---

## 4. Defect Log

| ID | Module | Description | Severity | Type | Status |
|----|--------|-------------|:--------:|------|:------:|
| BUG-001 | Signup | OTP confirmation message remains on screen for an unusually long duration after sending. | Low | UI | Open |
| BUG-002 | Language Settings | After switching from Vietnamese back to English, chatbot responses remain in Vietnamese for approximately 1 hour. | High | Functional | Open |
| BUG-003 | Lead Configuration | Lead generation fails intermittently despite using correct trigger phrases and keywords. | High | Functional | Open |
| BUG-004 | Lead Configuration | Consent message does not appear at the start or during the lead flow in the chatbot. | High | Functional | Open |
| BUG-005 | Lead Page | Export CSV fails with error: Failed to export lead. | High | Functional | Open |
| BUG-006 | Lead Configuration | Lead flow allows skipping required fields and loops back to the same question, creating a broken and confusing flow. | High | Functional | Open |
| BUG-007 | Lead Configuration | Lead name is not shown in the lead listing page or email notifications despite being saved in the detail view. | Medium | Functional | Open |
| BUG-008 | Lead Configuration | No validation error when system prompt exceeds the 2000-character limit. Configuration saves without restriction. | Medium | Validation | Open |
| BUG-009 | Form Configuration | Initiating a published form in the chatbot returns a backend error. All form features are completely blocked from testing. | Critical | Backend | Open |
| BUG-010 | Form Configuration | Form version number does not increment after publishing an updated form. | Low | UI | Open |
| BUG-011 | Integration (Social Media) | Social media channel integration fails even when all prerequisites are confirmed met. | High | Backend | Open |
| BUG-012 | Payment Tiering | Subscription status does not update to Cancelled when the trial end date is set to a past date. | Medium | UI | Open |
| BUG-013 | Payment Tiering | Clicking the trash icon deletes a payment method immediately with no confirmation dialog. | Medium | UI/UX | Open |

---

## 5. Key Findings by Module

### 5.1 Lead Configuration — 5 Defects (Highest Impact)

The highest defect count of any module. Consent messages are absent from the lead flow — a potential compliance concern. Trigger reliability is inconsistent, the lead flow loops incorrectly on required fields, and lead names are missing from the listing page and email notifications. There is also no character limit validation on the system prompt field.

### 5.2 Form Configuration — Critical (Fully Blocked)

A Critical backend defect prevents any published form from initiating in the chatbot. All dependent form features are blocked from further testing. This must be resolved and fully re-tested before any go-live consideration.

### 5.3 Integration — Social Media Channel (High Severity)

Social media channel integration fails with an error even when all stated prerequisites are confirmed met. The feature is currently non-functional and requires backend investigation.

### 5.4 Language Settings (High Severity)

Switching the chatbot language back to English from Vietnamese takes approximately 1 hour to take effect. Immediate language switching is expected behaviour for a real-time chatbot product.

### 5.5 Payment Tiering (Medium Severity)

Subscription status does not update in real time when trial end dates are changed. Additionally, payment methods can be deleted without a confirmation prompt, which poses a data safety risk.

### 5.6 Signup (Low Severity)

The OTP success message remains on screen for an unusually long time. The issue is intermittent and low-impact but should be addressed before release.

---

## 6. Recommendations

### 6.1 Pre-Go-Live — Mandatory Fixes

The following defects must be resolved and re-tested before the platform goes live:

- **BUG-009 (Critical)** — Fix backend error blocking form initiation in the chatbot. Re-test all form features after resolution.
- **BUG-004 (High)** — Ensure consent message appears at the start of and throughout the lead flow.
- **BUG-005 (High)** — Fix CSV export failure on the Leads page. Lead data export is a core operational function.
- **BUG-006 (High)** — Fix broken lead flow logic. Required fields must not be skippable and must not loop back.
- **BUG-002 (High)** — Fix language switching so changes take effect immediately.
- **BUG-003 (High)** — Stabilise lead trigger reliability so phrases and keywords work consistently.
- **BUG-011 (High)** — Fix social media integration backend failure when all prerequisites are already met.

### 6.2 Post-Go-Live Sprint — Recommended

- **BUG-007 (Medium)** — Propagate lead names to the lead listing page and email notifications.
- **BUG-008 (Medium)** — Add validation to restrict saving when the system prompt exceeds 2000 characters.
- **BUG-012 (Medium)** — Update subscription status in real time when trial end dates are changed.
- **BUG-013 (Medium)** — Add a confirmation dialog before any payment method is deleted.

### 6.3 Backlog — Low Priority

- **BUG-001 (Low)** — Auto-dismiss OTP confirmation message after a reasonable time period.
- **BUG-010 (Low)** — Ensure form version number increments correctly after each published update.

---

## 7. Overall UAT Verdict

| | |
|---|---|
| **UAT Outcome** | ❌ NOT READY FOR GO-LIVE |
| **Total Defects Found** | 13 |
| **Critical / High** | 7 — must be resolved before go-live |
| **Recommended Next Step** | Fix Critical & High → Re-test → UAT Sign-off |

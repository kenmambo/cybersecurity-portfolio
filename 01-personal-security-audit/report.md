# Personal Security Audit Report

## Auditor

Kenneth Mambo

## Audit Date

May 6, 2026

## Engagement

Personal Digital Security Assessment

## Methodology

Scope > Intelligence > Exposure > Severity > Remediation

---

## 1. Scope

### Systems and Accounts Assessed

| Item | Detail |
|---|---|
| Primary email | Redacted Gmail account |
| Key accounts assessed | Google Pay, GitHub, Google Account, LinkedIn |
| Primary devices | Laptop and mobile phone |
| Network | Redacted home fiber network |

This assessment focused on high-value personal and professional accounts, primary identity access, exposed credentials, active sessions, and account recovery risk.

---

## 2. Executive Summary

This personal security audit identified a critical compromise involving a high-value professional account, which resulted in account termination. Intelligence review also identified evidence that the primary email address appeared in malware-related credential exposure records from 2025, increasing the risk of credential theft, session hijacking, and account takeover.

Immediate remediation was performed to secure the primary email account, invalidate active sessions, and reduce the likelihood of further compromise. Additional remediation is required for high-value accounts, including stronger multi-factor authentication, malware scanning, and repository review.

**Overall risk rating:** High

---

## 3. Findings

### Critical Findings

#### 3.1 LinkedIn Account Takeover

**Severity:** Critical  
**Status:** Confirmed by user report

A LinkedIn account associated with the auditor was compromised by an unauthorized third party and was later terminated. This represents a high-impact compromise because LinkedIn is a professional identity platform used for networking, career visibility, and reputation.

**Risk:** Unauthorized access to a professional account may lead to impersonation, reputational damage, fraudulent messaging, and loss of professional contacts.

#### 3.2 Credential Exposure in 2025 Stealer Logs

**Severity:** Critical  
**Status:** Evidence identified by user

The primary email address appeared in January 2025 stealer-log exposure records. Stealer logs are commonly associated with malware that captures browser-stored credentials, cookies, device information, and saved session data.

**Risk:** This may indicate exposure of saved passwords, active browser sessions, or authentication tokens. If session cookies were exposed, attackers may have been able to access accounts without needing the current password.

---

### High Findings

#### 3.3 Weak or Unverified Two-Factor Authentication on High-Value Accounts

**Severity:** High  
**Status:** Requires verification

High-value accounts such as GitHub, LinkedIn, Google, and financial services require strong two-factor authentication. Accounts using SMS-only authentication or no second factor remain at increased risk of takeover.

**Risk:** SMS-based 2FA can be vulnerable to SIM swap attacks, interception, or social engineering. Lack of app-based MFA increases the chance of successful account compromise if credentials are leaked.

#### 3.4 Personally Identifiable Information Exposure

**Severity:** High  
**Status:** Evidence identified by user

Historical and recent breaches exposed personal information, including date of birth, geographic information, and multiple unique passwords.

**Risk:** Exposed PII can support identity theft, targeted phishing, account recovery abuse, and social engineering.

---

### Medium Findings

#### 3.5 Public OSINT Footprint

**Severity:** Medium  
**Status:** Evidence identified by user

Email-based OSINT review identified public links to account-related information such as Google profile details, photo references, Maps links, and Calendar-related artifacts.

**Risk:** Publicly discoverable identity information can help attackers build more convincing phishing messages, impersonation attempts, or account recovery attacks.

#### 3.6 Account Linkage Across Multiple Platforms

**Severity:** Medium  
**Status:** Evidence identified by user

The primary email address was linked to multiple platforms, including Dropbox, Spotify, Academia.edu, and other online services.

**Risk:** A single exposed email address connected to many services increases attack surface and enables credential stuffing or targeted phishing across platforms.

---

### Low Findings

#### 3.7 Legacy Breach Exposure

**Severity:** Low  
**Status:** Historical

The account appeared in older breaches, including legacy data leaks such as Wattpad 2020.

**Risk:** Older breaches may contain outdated credentials, but they still create risk if passwords were reused or if exposed information is used for profiling and phishing.

---

## 4. Actions Taken During Audit

- Changed the primary Gmail password to a unique, complex passphrase.
- Revoked active Google sessions through the Google Security Dashboard.
- Invalidated potentially stolen sessions by forcing re-authentication.
- Documented the possible connection between 2025 stealer-log exposure and the LinkedIn account compromise for appeal and recovery purposes.

---

## 5. Remediation Plan

### This Week

- File an official LinkedIn appeal citing unauthorized access and available breach evidence.
- Upgrade GitHub, Google, and other high-value accounts to app-based two-factor authentication or passkeys.
- Review account recovery emails and phone numbers for all key accounts.
- Confirm that no unfamiliar devices remain logged into Google, GitHub, or financial accounts.

### This Month

- Perform a malware scan and deep-clean review on the primary laptop and mobile phone.
- Review browser-saved passwords and remove any stored credentials that are duplicated, weak, or compromised.
- Audit all public GitHub repositories for hardcoded API keys, tokens, credentials, or sensitive configuration files.
- Move all key passwords into a password manager.
- Review third-party app access connected to Google, GitHub, and other high-value accounts.
- Create a recurring monthly personal security review checklist.

---

## 6. Risk Rating Summary

| Category | Risk Level | Reason |
|---|---:|---|
| Professional identity | Critical | LinkedIn account compromise and termination |
| Primary email security | High | Email is the master recovery account for multiple services |
| Credential exposure | Critical | Stealer-log exposure may indicate compromised browser-stored data |
| MFA posture | High | App-based MFA must be verified across high-value accounts |
| Public OSINT footprint | Medium | Publicly discoverable information supports targeted attacks |
| Legacy breaches | Low | Older breach data may still support profiling or password attacks |

---

## 7. Lessons Learned

This audit showed that personal cybersecurity is not only about having strong passwords. A compromised device, exposed session cookies, weak account recovery settings, or reused identity information can create serious risk even when a password has already been changed.

The most important lesson is that the primary email account functions as a master key. If it is compromised, many other accounts can be reset or accessed through recovery flows. Because of this, the primary email account requires the strongest protection: unique password, app-based MFA or passkey, active session review, recovery option review, and ongoing monitoring.

This project also demonstrated how personal security auditing follows the same structure used in professional cybersecurity work: define the scope, gather intelligence, identify exposure, rate severity, and perform remediation.

---

## 8. Final Status

| Item | Status |
|---|---|
| Audit status | Completed |
| Immediate remediation | Partially completed |
| Remaining risk | High |
| Next review date | June 6, 2026 |

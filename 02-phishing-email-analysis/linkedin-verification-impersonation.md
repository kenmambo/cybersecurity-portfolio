# Phishing Analysis Report

## Title

Suspected Phishing — LinkedIn Verification Impersonation — High Severity

## Date

May 18, 2026

## Analyst

Kenneth Mambo

---

## 1. Summary

A suspected phishing email was received by the target user, impersonating LinkedIn Security and presenting itself as an urgent account verification alert. The email attempted to direct the recipient to a lookalike login page designed to harvest LinkedIn credentials and potentially capture active session data.

Technical review identified failed email authentication controls, suspicious sender infrastructure, and a deceptive URL structure intended to make the destination appear related to LinkedIn. Based on the branding, urgency, credential-harvesting objective, and potential account takeover impact, this incident is classified as **High Severity**.

---

## 2. Indicators of Compromise

| Indicator Type | Value |
|---|---|
| Sender address | security-alert[@]linkedin-support-portal[.]net |
| Sender IP | 185[.]220[.]101[.]5 |
| Malicious URL | hxxps[:]//linkedin[.]com[.]account-verification-service[.]net/login/ |
| Attachments | None observed |
| File hashes | Not applicable |

---

## 3. Header Analysis

| Control | Result | Notes |
|---|---|---|
| SPF | Fail | Sending server was not authorized to send mail for the claimed LinkedIn-related identity. |
| DKIM | None | No valid cryptographic signature from the claimed sender domain was observed. |
| DMARC | Fail | Authentication alignment failed due to SPF failure and missing DKIM validation. |

### Originating Server

`mail-gateway[.]hacked-wordpress-host[.]ru`

### Notable Mismatches

The email display name appeared as **LinkedIn Security**, but the underlying sender address used an unrelated domain: `linkedin-support-portal[.]net`.

The originating server did not align with legitimate LinkedIn infrastructure. The message path suggested use of suspicious or compromised third-party hosting infrastructure rather than a trusted LinkedIn mail system.

---

## 4. URL and Attachment Analysis

### VirusTotal Result

VirusTotal flagged the submitted URL as suspicious or malicious.

**Detection ratio:** 14 / 72 security engines flagged the URL as malicious or phishing.

### URLScan.io Observations

URLScan.io analysis showed a login page visually imitating LinkedIn. The page appeared designed to convince users to enter account credentials into a non-LinkedIn domain.

Observed indicators included:

- LinkedIn-style login branding
- Lookalike domain structure
- Credential collection page
- External network requests supporting the fake login page
- No attachments used in the attack chain

### Lookalike Domain Analysis

The attacker used a deceptive subdomain structure:

```text
linkedin.com.account-verification-service.net
```

At a quick glance, the URL appears to contain `linkedin.com`. However, the actual registered root domain is:

```text
account-verification-service.net
```

This technique relies on users reading URLs from left to right and assuming the presence of `linkedin.com` means the destination is legitimate. In reality, the domain belongs to the attacker-controlled or suspicious namespace, not LinkedIn.

---

## 5. Social Engineering Technique

### Techniques Used

- Familiarity
- Urgency
- Fear

### Reasoning

The email used **familiarity** by impersonating LinkedIn, a professional networking platform the recipient may reasonably use. It used **urgency** by claiming the account required immediate verification within a limited time window. It also used **fear** by suggesting possible unauthorized login activity or account suspension.

This combination is effective because it pressures the recipient to act quickly before carefully checking the sender address, URL structure, or authentication details.

### Likely Target Profile

The email appears designed for professionals who rely on LinkedIn for career visibility, networking, job searching, or business communication. The attacker likely expected the recipient to value account access highly and respond quickly to a threat of suspension or verification failure.

---

## 6. Severity Assessment

**Severity:** High

This incident is rated **High Severity** because the phishing email impersonated a high-value professional platform and attempted to direct the recipient to a credential-harvesting page.

Successful exploitation could result in:

- LinkedIn account takeover
- Credential theft
- Session hijacking
- Impersonation
- Reputational damage
- Fraudulent messages sent to professional contacts
- Further phishing attacks using the compromised account

The attack is more serious than generic spam because it uses professional branding, authentication failures, deceptive URL construction, and a believable account-security pretext.

---

## 7. Recommended Actions

### For the User

1. Do not click the link or interact with the email.
2. Delete the email after preserving a redacted screenshot for evidence.
3. Report the email as phishing through the email provider.
4. Visit LinkedIn only by typing the official URL directly into the browser.
5. Change the LinkedIn password from a clean browser session if account compromise is suspected.
6. Enable or verify app-based multi-factor authentication on LinkedIn.
7. Review active LinkedIn sessions and revoke any unfamiliar sessions.
8. Check connected email accounts for suspicious login activity.

### For an Organization

1. Add the sender domain, malicious URL, and related infrastructure to email gateway deny-lists.
2. Search mail logs for other users who received the same sender, subject, or URL.
3. Identify any users who clicked or submitted credentials.
4. Invalidate active sessions for affected users.
5. Require password resets for users who interacted with the phishing page.
6. Add the phishing domain and URL pattern to DNS and web filtering controls.
7. Use this campaign as an awareness-training example focused on lookalike domains and URL reading.

---

## 8. Analyst Notes

This phishing email demonstrates why users must check the actual root domain before trusting a login page. The presence of a familiar brand name inside a URL does not prove the site belongs to that brand.

The strongest indicator in this case was the deceptive domain structure. The URL included `linkedin.com`, but the real domain was `account-verification-service.net`.

This analysis also reinforced the importance of SPF, DKIM, and DMARC checks during phishing triage. Failed or missing authentication controls do not prove phishing by themselves, but when combined with suspicious infrastructure and a lookalike login page, they strongly support a phishing classification.

---

## 9. Final Classification

| Item | Classification |
|---|---|
| Classification | Phishing |
| Attack type | Credential harvesting |
| Brand impersonated | LinkedIn |
| Severity | High |
| Attachments | None |
| User action required | Delete, report, verify account security, and review active sessions |

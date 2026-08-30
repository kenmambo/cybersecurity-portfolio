# Cloud Dependency and Shodan Surface Analysis Report

## Date

May 20, 2026

## Analyst

Kenneth Mambo

## Platform Focus

AWS / GCP Baseline

---

## 1. Executive Summary

This report documents a personal cloud-dependency review and passive reconnaissance analysis using Shodan-style internet exposure concepts. The assessment focused on identifying high-value cloud services, reviewing MFA coverage, and understanding how exposed services can be discovered through internet-wide search engines.

The review showed that cloud accounts such as email, document storage, and code repositories are high-value identity and data targets. It also demonstrated that attackers do not need to manually search for vulnerable systems. Tools like Shodan allow exposed ports, banners, device types, and misconfigured services to be found at scale.

**Overall risk rating:** Medium, pending completion of MFA verification and personal cloud service inventory.

---

## 2. Scope

### Areas Reviewed

- Personal cloud service dependencies
- MFA status on high-value cloud accounts
- Email identity and recovery risk
- Cloud document storage risk
- Code repository exposure
- Passive reconnaissance using Shodan-style search concepts
- Publicly exposed service banners and open ports

### Out of Scope

This assessment did not include:

- Unauthorized scanning
- Exploitation of exposed systems
- Login attempts against third-party systems
- Downloading or interacting with exposed data
- Active attacks against internet-facing services

All reconnaissance activity should remain passive and educational.

---

## 3. Cloud Dependency and MFA Inventory

### Cloud Services Cataloged

| Category | Service | Risk Value | MFA Status | Notes |
|---|---|---:|---|---|
| Email identity core | Gmail / Outlook / Other | Critical | Pending verification | Primary account recovery path |
| Document storage | Google Drive / OneDrive / Other | High | Pending verification | May contain personal, academic, or work files |
| Code repositories | GitHub | High | Pending verification | May contain code, tokens, configs, or portfolio work |
| Cloud platform | AWS / GCP / Azure | High | Pending verification | May expose infrastructure if misconfigured |
| Password manager | Bitwarden / Other | Critical | Pending verification | Stores authentication secrets |
| Mobile cloud backup | Google / Xiaomi / Other | Medium | Pending verification | May contain photos, contacts, device backups |

### Summary Counts

| Item | Count |
|---|---:|
| Total cloud services cataloged | At least 6 categories identified; final count pending user inventory |
| Total assets missing active MFA | Pending verification |
| Total high-value accounts reviewed | Pending verification |
| Total accounts requiring remediation | Pending verification |

---

## 4. Top High-Value Service Targets

### 4.1 Email Identity Core

**Service:** Gmail / primary email  
**MFA status:** Pending verification  
**Risk level:** Critical

The primary email account is the most important cloud dependency because it is commonly used for password resets, account recovery, login alerts, and identity verification. If compromised, it may allow an attacker to reset access to multiple connected services.

### 4.2 Document and Data Storage

**Service:** Google Drive / OneDrive / other cloud storage  
**MFA status:** Pending verification  
**Risk level:** High

Cloud document storage may contain sensitive personal files, academic work, financial documents, IDs, screenshots, exports, or cybersecurity portfolio evidence. Incorrect sharing settings or weak account security could expose sensitive data.

### 4.3 Code and Asset Registry

**Service:** GitHub  
**MFA status:** Pending verification  
**Risk level:** High

GitHub is a high-value target because repositories may contain source code, API keys, configuration files, scripts, notes, or future portfolio projects. Public repositories should be checked for secrets before publication.

---

## 5. Critical Reflection

The cloud service that most deserves attention is the primary email account because it functions as the recovery gateway for many other services. A compromise of this single account could affect cloud storage, GitHub, financial accounts, and professional identity platforms.

**First recommended action:** Verify and strengthen MFA on primary email and GitHub before publishing cybersecurity portfolio materials.

---

## 6. Shodan Reconnaissance Analysis

### 6.1 Search Parameter 1: Hardware or Router Brand

| Field | Result |
|---|---|
| Search parameter | Educational example only; user did not provide a final Shodan result |
| Global exposed footprint | Pending user Shodan count |
| Top geolocation / country | Pending user Shodan observation |
| Observed open ports | Example: 22, 80, 443, 8080, 3306, 3389 |
| Notable banner information | Pending user observation |

### Analyst Observation

Internet-facing devices often expose service banners that reveal device type, software version, open ports, or administrative interfaces. This information can help defenders identify exposed assets, but it can also help attackers filter for vulnerable systems.

Example open ports commonly seen in exposure analysis:

| Port | Service | Security Concern |
|---:|---|---|
| 22 | SSH | Remote administration exposed to internet |
| 80 | HTTP | Unencrypted web admin or service page |
| 443 | HTTPS | Web service or admin panel |
| 3306 | MySQL | Database exposure risk |
| 3389 | RDP | Remote desktop exposure risk |
| 8080 | Alternate HTTP | Admin panels, proxies, or development services |

---

### 6.2 Search Parameter 2: Unprotected Services

Example safe search idea:

```text
country:KE port:3306
```

| Field | Result |
|---|---|
| Search parameter | Educational example only |
| Total exposed targets | Pending user Shodan count |
| Key technical banner observation | Pending user observation |
| Risk interpretation | Exposed database services can create serious risk if they are not firewalled, patched, and authenticated correctly. |

### Security Note

Finding a service in Shodan does not grant permission to access, test, exploit, or interact with it. The correct defensive use is to understand exposure patterns, not to attack systems.

---

## 7. Defensive Takeaway

Shodan-style reconnaissance shows that attackers do not need to guess which systems are online. They can use filters to identify exposed ports, outdated versions, device types, and misconfigured services across the public internet.

The defensive lesson is clear: organizations and individuals must reduce unnecessary internet exposure, patch exposed services, restrict administrative interfaces, require MFA, and monitor public attack surface continuously.

---

## 8. Cloud Threat Vector Processed

| Item | Result |
|---|---|
| Threat vector | Cloud and internet-facing misconfiguration risk |
| Security action | Audited personal cloud authentication pathways |
| Security relevance | Connects personal cloud security to attack surface management |

---

## 9. Risk Assessment

**Overall risk:** Medium

The current risk is rated **Medium** because several high-value cloud services require MFA verification and account review. Risk may increase to **High** if any critical service lacks MFA, contains sensitive shared data, or has connected apps with excessive permissions.

### Risk Drivers

- Primary email may act as a master recovery account
- Cloud storage may contain sensitive personal data
- GitHub repositories may accidentally expose secrets
- Cloud platforms can create public infrastructure if misconfigured
- Internet-facing services can be discovered through public reconnaissance tools
- Weak MFA increases likelihood of account takeover

---

## 10. Recommended Actions

### This Week

1. Verify MFA status on primary email.
2. Verify MFA status on GitHub.
3. Verify MFA status on cloud storage accounts.
4. Review Google Drive / OneDrive sharing settings.
5. Remove unused third-party app integrations.
6. Check GitHub repositories for exposed secrets.
7. Confirm recovery email and phone settings are accurate.

### This Month

1. Enable app-based MFA or passkeys on all high-value cloud accounts.
2. Create a cloud service inventory.
3. Review public files and shared links.
4. Delete or archive unused cloud accounts.
5. Review AWS, GCP, or Azure accounts for active resources.
6. Enable billing alerts on cloud platforms.
7. Document a monthly cloud security review checklist.

---

## 11. Lessons Learned

This exercise showed that cloud security starts with identity. Email, cloud storage, GitHub, and cloud provider accounts are not isolated services; they are connected parts of a personal digital infrastructure.

The Shodan analysis also showed why exposure matters. Systems connected to the internet can be discovered automatically through open ports, service banners, and version information. Attackers can search for vulnerable systems at scale, which means defenders must remove unnecessary exposure before attackers find it.

The most important lesson is that visibility comes before security. I cannot protect cloud accounts, repositories, devices, or internet-facing services unless I first know they exist and understand how they are exposed.

---

## 12. Final Status

| Item | Status |
|---|---|
| Assessment status | In progress |
| Current risk | Medium |
| Highest-priority fix | Verify MFA on primary email, GitHub, and cloud storage |
| Next review date | June 20, 2026 |

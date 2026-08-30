# Adversarial Attack Chain Analysis Report

## Date

May 21, 2026

## Analyst

Kenneth Mambo

---

## 1. Executive Summary

This report maps a real-world ransomware incident and a personal attack scenario using the Cyber Kill Chain model. The real-world case selected is the 2024 Change Healthcare ransomware attack, which disrupted healthcare payment and claims operations across the United States.

The incident demonstrates how one weakness, compromised credentials combined with missing multi-factor authentication, can create a full attack path from initial access to ransomware deployment and data theft.

The second half of this report applies the same attack-chain thinking to a personal high-value asset. The goal is not to attack systems, but to understand where an attacker would likely apply pressure and which controls would interrupt the chain earliest.

---

## 2. Real-World Incident Selected

| Item | Detail |
|---|---|
| Incident | Change Healthcare ransomware attack |
| Year | 2024 |
| Threat group | ALPHV / BlackCat ransomware affiliate |
| Primary weakness | Compromised credentials and missing MFA on remote access infrastructure |
| Business impact | Major disruption to healthcare claims, payments, pharmacy operations, and patient-data security |

Public reporting states that attackers used stolen credentials to access a Change Healthcare Citrix remote access portal that did not have MFA enabled. The ransomware incident disrupted healthcare operations nationally and led UnitedHealth to disconnect affected systems to contain the attack.

---

## 3. Cyber Kill Chain Mapping

| Stage | Kill Chain Phase | Analysis |
|---:|---|---|
| 1 | Reconnaissance | The attackers likely identified Change Healthcare as a high-value healthcare payment-processing target. Remote access infrastructure, employee access paths, and identity systems would have been valuable reconnaissance targets. |
| 2 | Weaponization | The attacker prepared to use stolen credentials against a remote access portal. In this case, the “weapon” was not necessarily malware first; it was valid access combined with an authentication gap. |
| 3 | Delivery | The attack chain used compromised credentials against a remotely accessible Citrix portal. This allowed the attacker to enter through what appeared to be a legitimate login path. |
| 4 | Exploitation | The missing MFA control allowed the stolen credentials to work. Because the portal did not require a second factor, the attacker could authenticate successfully. |
| 5 | Installation | After access was gained, the attackers established presence, moved through the environment, and prepared ransomware deployment. Public reporting indicates the attackers had access before ransomware was deployed. |
| 6 | Command and Control | The attackers likely used remote access, internal tools, or attacker-controlled infrastructure to maintain access, move laterally, and coordinate activity before the ransomware event. |
| 7 | Actions on Objectives | The attackers exfiltrated sensitive data and deployed ransomware, disrupting healthcare payment and claims systems. The attack created operational, financial, legal, and patient-care consequences. |

---

## 4. Identified MITRE ATT&CK Techniques

| Technique ID | Technique Name | Relevance |
|---|---|---|
| T1078 | Valid Accounts | Attackers used stolen credentials to access remote infrastructure. |
| T1133 | External Remote Services | The attack involved access through a remote Citrix portal. |
| T1021 | Remote Services | Remote access may have supported movement after initial entry. |
| T1486 | Data Encrypted for Impact | Ransomware encrypted systems to disrupt operations. |
| T1041 | Exfiltration Over C2 Channel | Sensitive data was reportedly stolen before or during the ransomware operation. |
| T1567 | Exfiltration Over Web Service | Possible method category for data transfer, depending on attacker tooling. |

---

## 5. Critical Interruption Vector

If defenders had implemented stronger prevention and detection controls at **Stage 4: Exploitation**, the downstream attack flow could have been interrupted.

The critical dependency was that stolen credentials were enough to access the remote portal. If phishing-resistant MFA, conditional access, device trust, impossible-travel detection, or privileged access monitoring had blocked the login, the attacker would not have gained the same initial foothold.

The most important lesson from this incident is that valid credentials are not enough protection. Remote access systems must require strong MFA, logging, monitoring, and anomaly detection.

---

## 6. Self-Targeted Attack Scenario

### High-Value Asset Context

| Item | Detail |
|---|---|
| Asset | Primary professional GitHub account and primary email account |
| Why it matters | These accounts support professional identity, code storage, portfolio development, account recovery, and future cybersecurity career credibility. |

---

## 7. Adversarial Simulation Pipeline

| Stage | Attack Scenario |
|---:|---|
| 1. Reconnaissance | An attacker reviews public GitHub repositories, LinkedIn activity, email exposure, old breach data, and public learning posts to identify tools, interests, account names, and possible weak points. |
| 2. Weaponization | The attacker creates a fake cybersecurity learning resource, GitHub collaboration request, LinkedIn recovery message, or fake recruiter message that appears relevant to my current cybersecurity journey. |
| 3. Delivery | The lure is delivered through email, LinkedIn message, GitHub issue, SMS, or a direct message pretending to come from a recruiter, mentor, course platform, or security community. |
| 4. Exploitation | The attacker attempts to make me enter credentials into a fake login page, authorize a malicious OAuth app, download a fake study resource, or approve a suspicious account recovery flow. |
| 5. Installation | Instead of installing malware immediately, the attacker may gain persistence through a malicious OAuth grant, stolen session cookie, browser token, or unauthorized email forwarding rule. |
| 6. Command and Control | The attacker quietly maintains access through the granted app, active session, inbox forwarding rule, or connected account token. |
| 7. Actions on Objectives | The attacker could delete repositories, steal private notes, impersonate me professionally, send phishing messages to contacts, reset downstream accounts, or damage my cybersecurity portfolio credibility. |

---

## 8. Honest Vulnerability Assessment

### Weakest Stage Link

**Highest-risk stage:** Stage 3 / Stage 4 — Delivery and Exploitation

This is the highest-risk point because a message related to cybersecurity learning, GitHub collaboration, LinkedIn account recovery, or job opportunities would feel relevant and believable. Since I am actively building a cybersecurity portfolio, an attacker could create a lure that matches my current goals.

### Why This Matters

The attack would not need to be technically advanced. A well-written message offering help with GitHub, portfolio review, LinkedIn recovery, or a cybersecurity opportunity could create enough trust to make the link feel legitimate.

This shows that the strongest defensive improvement is not only technical hardening, but also stronger verification habits.

---

## 9. Proactive Controls to Deploy This Week

1. Enable or verify app-based MFA or passkeys on GitHub.
2. Enable or verify app-based MFA or passkeys on primary email.
3. Review GitHub account recovery settings.
4. Review Google account active sessions.
5. Remove unused OAuth app grants from Google and GitHub.
6. Avoid authenticating through links sent by email, LinkedIn, SMS, or GitHub issues.
7. Type official URLs directly into the browser for account security tasks.
8. Store recovery codes securely in a password manager or offline backup.
9. Review public GitHub repositories for exposed email addresses, API keys, tokens, or sensitive notes.
10. Keep portfolio screenshots redacted before publishing.

---

## 10. Defensive Controls by Kill Chain Stage

| Kill Chain Stage | Defensive Control |
|---|---|
| Reconnaissance | Reduce unnecessary public personal data, remove sensitive metadata, review public repositories. |
| Weaponization | Be cautious with files, links, and “security tools” from unknown sources. |
| Delivery | Treat unsolicited emails, LinkedIn messages, SMS, and GitHub issues as untrusted until verified. |
| Exploitation | Use password manager autofill, MFA, passkeys, and direct navigation instead of login links. |
| Installation | Review OAuth grants, browser extensions, device sessions, and email forwarding rules. |
| C2 Channel | Monitor login alerts, unusual inbox rules, unknown devices, and connected apps. |
| Actions on Objectives | Maintain backups, protect recovery codes, and enable account recovery safeguards. |

---

## 11. Sources

- Public reporting on the Change Healthcare 2024 ransomware attack and testimony that stolen credentials were used against a Citrix portal without MFA.
- MITRE ATT&CK framework technique references.

---

## 12. Lessons Learned

This exercise showed that an attacker does not need to “hack everything” at once. A successful attack is often a chain of small steps. If one step works, it creates the conditions for the next step.

The Change Healthcare incident shows how compromised credentials and missing MFA can lead to large-scale operational disruption. In my personal case, the same lesson applies at a smaller scale: if an attacker gets into my primary email, GitHub, or professional identity accounts, the impact could spread across my entire digital life.

The most important defensive mindset is to interrupt the chain as early as possible. The earlier the control works, the less damage the attacker can do.

---

## 13. Final Status

| Item | Status |
|---|---|
| Assessment status | Completed |
| Real-world incident mapped | Change Healthcare 2024 |
| Personal asset modelled | Primary email and GitHub |
| Current risk | Medium |
| Highest-priority control | Strong MFA / passkeys on primary email and GitHub |
| Next review date | June 21, 2026 |

# Advanced Red Team Portfolio: OWASP Juice Shop Engagements

This repository documents findings from simulated Red Team engagements targeting the **OWASP Juice Shop**, a modern, intentionally vulnerable web application.

The goal of this phase is to move beyond automated scanning and basic exploitation to focus on manual enumeration, filter evasion, and complex application-level vulnerabilities (e.g., SQL Injection, XSS, Broken Access Control).

##  Methodology and Tools

The exercises focus on the **OWASP Top 10** categories and adhere to standard penetration testing methodologies.

| Phase | Description | Key Tools Used |
| :--- | :--- | :--- |
| **Reconnaissance** | Directory brute-forcing and passive traffic analysis. | `Gobuster`, **Burp Suite (Proxy)** |
| **Exploitation** | Manual payload crafting, filter bypass, and traffic manipulation. | **Burp Suite (Repeater/Decoder)**, Browser |
| **Reporting** | Documenting the root cause, impact, and mitigation for each finding. | Markdown |

##  Key Findings Summary

| Report File | Vulnerability Category | Severity | Description |
| :--- | :--- | :--- | :--- |
| **ADVANCED_01...** | A01: Broken Access Control / Sensitive Data Exposure | High | Discovered hidden directories and exfiltrated confidential internal documents.[link](ADVANCED_01_Sensitive_Data_Exposure.md) |
| **ADVANCED_02...** | A07: Identification and Authentication Failures | Critical | Bypassed administrator login via targeted SQL Injection payload executed via browser console.[link](ADVANCED_02_SQL_Injection.md)|
| **ADVANCED_03...** | A03: Injection (XSS) | High | Successfully injected JavaScript into the search function via a reflected payload.Executed persistent and click-triggered DOM XSS payloads in the search function.[link](ADVANCED_03_XSS_DOM.md) |
| **ADVANCED_04...** | A01: Broken Access Control | High | Bypassed client-side access controls via JWT manipulation to access the Admin Panel.[link](ADVACED_04_BAC_Token_Manipulation.md) |
| **ADVANCED_O5...** | A01: Broken Access Control / IDOR | High | Successfully viewed other users' baskets by manipulating the API request ID[link](ADVANCED_05_IDOR_Basket_Access.md) |

---

## First Finding: Sensitive Data Exposure

The first completed exercise demonstrates successful Information Disclosure despite strict file extension filtering.

* **Vulnerability:** Directory Listing and Improper Access Control on the `/ftp` path.
* **Proof:** Retrieved the confidential `acquisitions.md` document and identified the existence of `incident-support.kdbx` (a password database).

***
## Failed Attempts
1. [SQLi Obstacle Report](Failed_SQL_Injection_attempt1)
2. [Failed Exploit Iterations and Defense Detection](failed-exploit-attempt.md)

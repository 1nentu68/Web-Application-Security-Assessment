# JRU-Pulse Web Application Security Assessment

### A comprehensive security assessment of the JRU-Pulse web application, demonstrating vulnerability identification, remediation, and validation using OWASP ZAP.

This repository contains the full report and documentation for a web application security assessment project. The goal was to identify and mitigate common security vulnerabilities in a controlled development environment, effectively hardening the application and reducing its attack surface before a hypothetical production deployment.

---

##  Key Objectives

*   **Identify Vulnerabilities:** Use Dynamic Application Security Testing (DAST) to find security weaknesses in a running web application.
*   **Remediate & Harden:** Implement practical fixes in the application code, server configuration, and directory structure.
*   **Validate & Verify:** Confirm that the implemented fixes successfully mitigated the identified risks.
*   **Document Findings:** Create a professional report detailing the scope, methodology, findings, and outcomes, aligned with industry standards.

---

##  Technology & Tools Stack

*   **Security Testing:** OWASP ZAP (Zed Attack Proxy)
*   **Environment:** XAMPP
*   **Web Server:** Apache
*   **Backend:** PHP
*   **Database:** MySQL
*   **Operating System:** Windows 11

---

##  Methodology

The assessment followed a structured, five-step methodology common in professional security testing:

1.  **Environment Setup:** Deployed the application locally on a XAMPP stack.
2.  **Reconnaissance & Baseline Scan:** Performed an initial automated scan with OWASP ZAP to identify baseline vulnerabilities.
3.  **Manual Verification & Review:** Manually validated findings by inspecting HTTP headers, cookies, and source code.
4.  **Remediation & Hardening:** Applied security controls to the application code and server configuration to address the findings.
5.  **Re-Scan & Validation:** Executed a final scan to confirm that vulnerabilities were successfully remediated and documented the reduced risk.

---

## Summary of Findings & Remediation

The initial scan revealed several critical and high-severity vulnerabilities. The following table summarizes the most significant issues that were identified and successfully remediated.

| Finding                       | Severity | Description                                           | Remediation Action                                           | Status           |
| ----------------------------- | :------: | ----------------------------------------------------- | ------------------------------------------------------------ | :--------------: |
| **.env File Exposure**        | **High**     | Credentials file was publicly accessible.             | Relocated `.env` outside the webroot and blocked access via `.htaccess`. | **Remediated** |
| **Insecure Cookies**          |  Medium  | Session cookies lacked `HttpOnly` & `SameSite` flags. | Hardened session parameters in PHP to enforce secure cookie attributes. | **Remediated** |
| **Directory Browsing Enabled**|  Medium  | Server revealed contents of directories without index files. | Disabled directory listing (`Options -Indexes`) in `.htaccess`.      | **Remediated** |
| **Missing Security Headers**  |  Medium  | Lacked CSP, X-Frame-Options, and other key headers. | Implemented a robust Content Security Policy (CSP) and other security headers. | **Remediated** |
| **Server Version Disclosure** |   Low    | Apache & PHP versions were exposed in HTTP headers.   | Hardened `httpd.conf` and `php.ini` to suppress version information. | **Remediated** |

---

## Validation: Before vs. After

The remediation efforts resulted in a significant and measurable improvement in the application's security posture.

*   **Before:** The initial OWASP ZAP scan reported **12 alerts**, including one high-severity `.env` information leak.
*   **After:** The final scan reported only **2 informational alerts**, confirming that all actionable vulnerabilities were successfully eliminated.


---

## Aligning with Industry Standards (ISO/IEC 27001)

This project was conducted with principles from the **ISO/IEC 27001** framework in mind, demonstrating an understanding of:
*   **A.12.6 - Technical Vulnerability Management:** A structured process for identifying, evaluating, and addressing technical vulnerabilities.
*   **A.9 - Access Control:** Securing sensitive files (`.env`) and session data.
*   **A.14 - System Development:** Integrating security practices into the development lifecycle.


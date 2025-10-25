# Web Application Security Assessment & Hardening for JRU-PULSE

This repository documents the comprehensive security assessment and hardening process I conducted for the **JRU-PULSE** web application, a capstone project developed for José Rizal University.

The goal of this specific effort was to identify and remediate security vulnerabilities in the application's development environment, ensuring it met high standards for security and robustness prior to its final academic validation.

---

## About the JRU-PULSE Project (The System I Assessed)

To provide context, JRU-PULSE is a sophisticated, web-based platform designed to modernize service evaluation at José Rizal University. It replaces manual feedback methods with a real-time, data-driven system.

*   **Core Function:** It collects and analyzes feedback from students, parents, and alumni.
*   **Intelligent Analysis:** The system's backend uses fine-tuned **BERT models** for advanced sentiment analysis and predictive forecasting of user satisfaction.
*   **Academic Significance:** This system was the subject of a formal project study, "JRU-PULSE: Performance and User-satisfaction Linked Service Evaluation," presented in partial fulfillment of the requirements for the Bachelor of Science in Information Technology.


---

## My Role: Security Validation and Hardening

As a co-author of the study, my primary contribution to the validation phase was to lead the platform's security assessment. I was responsible for moving the application from its initial development state to a hardened, secure baseline.

### 🛠️ Tools and Technologies

*   **Security Testing:** OWASP ZAP (Zed Attack Proxy)
*   **Environment:** XAMPP
*   **Web Server & Configuration:** Apache, `.htaccess`
*   **Backend:** PHP, `php.ini`

### ⚙️ Methodology

I followed a structured, five-step methodology to ensure a thorough and repeatable assessment:

1.  **Environment Setup:** Deployed a local instance of the JRU-PULSE application using XAMPP.
2.  **Baseline Scan:** Performed an initial automated scan with OWASP ZAP to identify vulnerabilities and establish a baseline risk profile.
3.  **Manual Verification:** Manually confirmed the findings by inspecting HTTP headers, cookies, and directory structures.
4.  **Remediation & Hardening:** Systematically applied security fixes to the server configuration (`.htaccess`, `php.ini`) and recommended secure coding practices.
5.  **Validation Scan:** Performed a final scan to verify that all vulnerabilities were successfully mitigated and the application's attack surface was reduced.

---

## 📊 Key Findings & Remediation

The initial assessment revealed several common but critical vulnerabilities. The following table details the "before and after" of the security hardening process I implemented.

| Finding                       | Severity | Initial Risk & Description                          | Remediation Action Implemented                               | Validation Result            |
| ----------------------------- | :------: | --------------------------------------------------- | ------------------------------------------------------------ | :--------------------------- |
| **.env File Exposure**        | **High**     | Credentials file was publicly accessible in the webroot. | Relocated `.env` and blocked direct access via `.htaccess`.  | ✅ **Access Denied (403)**    |
| **Insecure Cookies**          |  Medium  | Session cookies lacked `HttpOnly` & `SameSite` flags. | Hardened PHP session parameters to enforce secure cookie attributes. | ✅ **Secure Flags Present**   |
| **Missing Security Headers**  |  Medium  | Lacked CSP, X-Frame-Options, and X-Content-Type-Options. | Implemented a robust Content Security Policy (CSP) and other security headers in `.htaccess`. | ✅ **Headers Enforced**       |
| **Directory Browsing Enabled**|  Medium  | Server revealed contents of directories without index files. | Disabled directory listing (`Options -Indexes`) in `.htaccess`.      | ✅ **Access Denied (403)**    |
| **Server Version Disclosure** |   Low    | Apache & PHP versions were exposed in HTTP headers. | Set `ServerSignature Off` & `expose_php=Off` in server configurations. | ✅ **Generic Headers Shown**  |

---

## ✅ Final Outcome

The security hardening process was highly successful. The final validation scan with OWASP ZAP confirmed that all identified vulnerabilities were fully remediated, achieving a final report of **zero high-risk, zero medium-risk, and zero low-risk vulnerabilities.**

This process provided the verifiable evidence needed to confirm the platform's robust security posture, fulfilling a critical requirement for the overall success of the JRU-PULSE project study.

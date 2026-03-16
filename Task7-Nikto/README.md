# 🛡️ Task 7 — Nikto Web Vulnerability Scan  
**Oasis Infobyte Cybersecurity Internship**

## 📌 Objective
Perform a comprehensive web vulnerability scan using **Nikto** against the target web server, identify potential security issues, analyze the findings, and document remediation recommendations.

---

## 🖥️ 1. Environment Setup
- **Operating System:** Ubuntu 22.04 LTS (VirtualBox VM)  
- **Tool:** Nikto Web Server Scanner  
- **Target:** DVWA running on localhost (127.0.0.1)  
- **Network:** Localhost  

---

## 🚀 2. Running the Nikto Scan

### Basic Scan Command
```bash
nikto -h http://<target-ip>/
```

### Useful Flags

| Flag | Description |
|------|-------------|
| `-h <host>` | Specifies the target host or URL to scan |
| `-p <port>` | Sets a custom port (e.g., 80, 443) |
| `-ssl` | Forces SSL mode for HTTPS scanning |
| `-o <file>` | Outputs results to a specified file |
| `-Format <type>` | Sets output format (e.g., txt, html, csv, xml) |
| `-Tuning <options>` | Limits tests to specific categories (e.g., 1,2,3) |
| `-timeout <seconds>` | Sets a timeout for requests |
| `-Plugins <plugin>` | Runs only specific plugins |
| `-list-plugins` | Displays all available plugins |
| `-useproxy` | Routes scan through a proxy |
| `-update` | Updates Nikto databases |

---

### Example Command Used
```bash
nikto -h http://127.0.0.1 --output nikto_results.txt
```

---

## 🔍 3. Scan Results — Key Findings

The following findings were extracted directly from the Nikto scan output (`nikto_scan.txt`):

### 1. Outdated Apache Version Detected
- **Evidence:** Server reports `Apache/2.4.41`.
- **Risk Level:** Medium
- **Impact:** Older versions may contain known vulnerabilities.
- **Recommendation:** Update Apache and disable version disclosure.

### 2. Server Leaks Internal IP Address
- **Evidence:** Response headers reveal `127.0.1.1`.
- **Risk Level:** Low
- **Impact:** Internal IP disclosure can assist attackers in mapping the environment.
- **Recommendation:** Sanitize server headers.

### 3. Allowed HTTP Methods May Be Excessive
- **Evidence:** Nikto reports multiple allowed HTTP methods.
- **Risk Level:** Medium
- **Impact:** Methods like TRACE or PUT can be abused if enabled.
- **Recommendation:** Restrict allowed methods to GET and POST.

### 4. Missing Security Headers
- **Evidence:** Headers such as `X-Frame-Options`, `X-XSS-Protection`, and `Content-Security-Policy` are not present.
- **Risk Level:** Medium
- **Impact:** Increases exposure to clickjacking and XSS.
- **Recommendation:** Add recommended security headers.

### 5. Cookie Missing Security Flags
- **Evidence:** DVWA session cookie lacks `httponly` and `secure` attributes.
- **Risk Level:** Medium
- **Impact:** Cookies may be exposed to scripts or transmitted insecurely.
- **Recommendation:** Add `httponly`, `secure`, and `samesite` flags.

### 6. Outdated SSL/TLS Modules
- **Evidence:** `mod_ssl/2.4.41` and `OpenSSL/1.1.1f` detected.
- **Risk Level:** Medium
- **Impact:** Older cryptographic libraries may contain weaknesses.
- **Recommendation:** Update OpenSSL and enforce strong TLS configuration.

### 7. Directory Indexing May Be Enabled
- **Evidence:** Nikto indicates potential directory listing behavior.
- **Risk Level:** Low–Medium
- **Impact:** Attackers may view sensitive files.
- **Recommendation:** Disable directory indexing.

---

## 🔍 4. Risk Analysis
Summarize the overall security posture:
- Number of high‑risk issues
- Number of medium‑risk issues
- Number of low‑risk issues
- Potential impact if exploited
- Likelihood of exploitation

---

## 🧩 5. Mitigation Recommendations
Provide actionable steps to improve security:
- Patch outdated software and services
- Disable unnecessary modules
- Harden HTTP headers
- Restrict directory access
- Implement proper authentication and access controls

---

📁 6. Folder Structure
Task-7-Nikto/
│── README.md
│── nikto_results.txt (optional)
│── screenshots/
│     ├── scan_start.png
│     ├── scan_results.png
│     └── findings.png

---

## 🎯 7. Conclusion
Nikto successfully identified multiple potential vulnerabilities on the target web server. These findings highlight the importance of regular vulnerability scanning and proactive patching to maintain a secure and resilient environment.

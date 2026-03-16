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

## 📸 3. Evidence & Screenshots
Include screenshots showing:
- The Nikto command execution
- Scan progress
- Final results
- Any exported output files
Place them inside:
Task-7-Nikto/screenshots/



## 🔍 4. Key Findings
Document the vulnerabilities discovered during the scan.
Below is a template you can replace with your actual results.
1. Outdated Apache Version
- Description: Server is running an outdated version of Apache.
- Risk Level: High
- Impact: May contain known vulnerabilities and exploits.
- Recommendation: Update Apache to the latest stable version.
2. Directory Listing Enabled
- Description: Directory browsing is enabled on the server.
- Risk Level: Medium
- Impact: Attackers can view sensitive files and directories.
- Recommendation: Disable directory listing in server configuration.
3. Missing Security Headers
- Description: Headers such as X-Frame-Options or X-XSS-Protection are missing.
- Risk Level: Medium
- Impact: Increases exposure to clickjacking and XSS attacks.
- Recommendation: Add recommended security headers.

## 🛠️ 5. Risk Analysis
Summarize the overall security posture:
- Number of high‑risk issues
- Number of medium‑risk issues
- Number of low‑risk issues
- Potential impact if exploited
- Likelihood of exploitation

## 🧩 6. Mitigation Recommendations
Provide actionable steps to improve security:
- Patch outdated software and services
- Disable unnecessary modules
- Harden HTTP headers
- Restrict directory access
- Implement proper authentication and access controls

📁 7. Folder Structure
Task-7-Nikto/
│── README.md
│── nikto_results.txt (optional)
│── screenshots/
│     ├── scan_start.png
│     ├── scan_results.png
│     └── findings.png



## 🎯 8. Conclusion
Nikto successfully identified multiple potential vulnerabilities on the target web server. These findings highlight the importance of regular vulnerability scanning and proactive patching to maintain a secure and resilient environment.

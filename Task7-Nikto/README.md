# Task 3 — SQL Injection (DVWA)
Oasis Infobyte Cybersecurity Internship

## 📌 Overview
This task focuses on identifying and exploiting SQL Injection vulnerabilities within the **DVWA (Damn Vulnerable Web Application)** SQLi module.  
The objective is to understand how insecure input handling can be abused to extract sensitive data and manipulate backend SQL logic.

This README includes:
- Normal application behavior
- Boolean-based SQL Injection
- UNION-based SQL Injection
- Root cause analysis
- Mitigation recommendations
- Evidence files (`.txt` and `.html`)
- Exploit script
- Completion summary

---

## 🧪 1. Normal Query Behavior
A standard request using:
```
?id=1
```
returns the expected user record.  
This confirms the application behaves normally before injection attempts.

---

## 🔓 2. Boolean-Based SQL Injection

### Payload Used
```sql
' OR '1'='1
```
This modifies the backend SQL query into an always‑true condition, causing DVWA to return all user records.

Result
- Successfully extracted all users from the database
- Confirmed that DVWA directly concatenates user input into SQL queries

---

## 🧪 3. UNION-Based Injection (Successful with `#` Comment Operator)

### Payloads Tested
```sql
1' UNION SELECT user, password FROM users #
AND
1' UNION SELECT first_name, last_name FROM users #
```
### ✅ Result
The UNION-based SQL injection executed successfully when using the `#` comment operator.  
This allowed the injected `UNION SELECT` query to run without interference from the remainder of the original SQL statement, returning usernames and password hashes from the database.

### 🧠 Why `#` Works
- MySQL supports `#` as a valid single-line comment operator.  
- The `--` operator requires a trailing space, which DVWA does not always preserve.  
- Using `#` cleanly comments out the rest of the backend query, preventing syntax errors.  
- This ensures the UNION payload executes correctly and returns the expected results.

### 📌 Notes
- The number of columns in the `UNION SELECT` must match the original query.  
- DVWA Low Security may still restrict certain UNION behaviors.  
- Successful execution confirms the backend is vulnerable to UNION-based SQL Injection when the correct comment operator is used.

---

## 🛡 4. Root Cause
The vulnerability exists because DVWA:
- Directly concatenates user input into SQL queries
- Does not sanitize or escape input
- Does not use prepared statements
- Does not enforce type checking
These weaknesses allow attackers to manipulate SQL query structure.

---

## 📚 5. Mitigation Recommendations
To prevent SQL Injection:
- Use prepared statements (parameterized queries)
- Validate and sanitize all user input
- Enforce strict data types
- Limit database privileges
- Implement safe error handling that does not expose SQL details

---

## 📸 6. Evidence Included
The following files are included in this task folder:
| File | Description |
|------|-------------|
| **sql_injection_output.txt** | Raw text output generated from the automated SQL Injection exploit script. This file captures the server responses for the normal query, boolean-based injection, and UNION-based injection attempts. |
| **sql_injection_output.html** | Browser-rendered HTML output showing the extracted user data returned by the SQL Injection payloads. This includes usernames and password hashes retrieved from the DVWA database. |

These files serve as verifiable proof of successful exploitation.

---

## 🧰 7. Exploit Script
This task incudes:
```
sql_injection_exploit.sh
```
This Bash script automates:
- Normal query
- Boolean-based DQLi
- UNION-based SQLi
- Output extraction
It demonstrates how SQL Injection can be executed programmatically.

---

## ✅ 8. Task Completion Summary
- Accessed the DVWA SQL Injection module
- Verified normal behavior
- Performed SQL Injection using ' OR '1'='1
- Extracted all user records
- Successfully executed UNION-based SQLi using #
- Captured evidence in .txt and .html formats
- Documented root cause and mitigation strategies
- Delivered a reusable exploit script
This completes Task 3 for the Oasis Infobyte Cybersecurity Internship.

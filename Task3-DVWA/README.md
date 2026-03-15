# DVWA – Task 3: SQL Injection (Low Security)

This task demonstrates how SQL Injection vulnerabilities occur when user input is not sanitized before being passed into a database query. Using DVWA’s SQL Injection module (Security Level: Low), I performed a series of tests to identify and exploit the vulnerability, extract user data, and document the findings.

---

## 🔧 Environment Setup

- **Platform:** DVWA running on Ubuntu (Apache2 + MySQL)
- **DVWA Security Level:** Low
- **Database:** Successfully created using DVWA setup page
- **Login Credentials:**
  - Username: `admin`
  - Password: `password`

---

## 🧪 1. Normal Application Behavior

To understand the baseline functionality, I entered a valid user ID:
```
1
```

DVWA returned the expected result:

- First name: admin  
- Surname: admin  

This confirms the backend query is functioning normally.

---

## 🧪 3. UNION-Based Injection (Successful with `#` Comment Operator)

During testing, I attempted several UNION-based SQL injection payloads such as:

```sql
1' UNION SELECT user, password FROM users #
```
AND
```sql
1' UNION SELECT first_name, last_name FROM users #
```
### ✅ Result
The UNION-based SQL injection payload executed successfully when using the `#` comment operator. This allowed the injected `UNION SELECT` query to run without interference from the remainder of the original SQL statement, returning usernames and password hashes from the database.

### 🧠 Why `#` Works
- DVWA uses MySQL, where `#` is a valid single-line comment operator.
- Using `#` cleanly comments out the rest of the backend query, preventing syntax errors.
- The `--` operator in MySQL requires a trailing space, and DVWA’s query structure does not always preserve that space, causing the injection to fail.
- As a result, `#` provides a more reliable way to terminate the original query and execute the UNION payload.

### 📌 Notes
- The number of columns in the `UNION SELECT` must match the number of columns in the original query.
- DVWA Low Security may still restrict certain UNION behaviors, but the payload works when properly formatted.
- Successful execution confirms that the backend query is vulnerable to UNION-based SQL injection when the correct comment operator is used.

---

## 🛡 4. Root Cause

The vulnerability exists because DVWA:

- Directly concatenates user input into SQL queries  
- Does not sanitize or escape input  
- Does not use prepared statements  
- Does not enforce type checking  

These weaknesses allow attackers to manipulate the SQL query structure and inject arbitrary SQL commands.

---

## 📚 5. Mitigation Recommendations

To prevent SQL Injection vulnerabilities:

- Use **prepared statements** (parameterized queries)  
- Validate and sanitize all user input  
- Enforce strict data types  
- Limit database privileges to the minimum required  
- Implement error handling that does not expose SQL or database details  

---

## 📸 6. Evidence (Screenshots to Include)

Include the following screenshots in your repository:

- **Normal query result** (User ID = 1)  
- **Injection result** using `' OR '1'='1` showing all users  
- **Optional:** Successful or attempted UNION-based injection results  

---

## ✅ 7. Task Completion Summary

- Accessed the DVWA SQL Injection module  
- Verified normal application behavior  
- Performed SQL Injection using `' OR '1'='1`  
- Extracted all user records from the database  
- Successfully executed UNION-based injection using the `#` comment operator  
- Documented findings, root cause, and mitigation strategies  

This completes **Task 3** for the Oasis Infobyte Cybersecurity Internship.


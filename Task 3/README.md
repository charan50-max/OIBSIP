# SQL Injection Exploit – DVWA (Low Security)

## Objective
Demonstrate SQL Injection vulnerability in DVWA using classic injection techniques.

## Environment
- OS: Windows
- Web Server: XAMPP
- Application: Damn Vulnerable Web Application (DVWA)
- Security Level: Low

## Exploit Steps

### Payload 1 – Authentication Bypass
1' OR '1'='1
**Result:** Returned all user records from the database.

### Payload 2 – Credential Extraction
**Result:** Dumped usernames and password hashes.

## Impact
An attacker can:
- Bypass authentication
- Extract sensitive user credentials
- Fully compromise the database

## Conclusion
This demonstrates a critical SQL Injection vulnerability caused by improper input validation and unsafe query construction.

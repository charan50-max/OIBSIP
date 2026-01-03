SQL Injection Vulnerability Exploitation Report DVWA

Objective

The objective of this task is to understand, identify, exploit, and document an SQL Injection vulnerability in a deliberately vulnerable web application. This exercise is performed strictly in a controlled local lab environment using Damn Vulnerable Web Application DVWA to demonstrate how insecure coding practices can lead to serious security risks.

This task builds practical knowledge of how SQL Injection works and how such vulnerabilities should be fixed in real world applications.

Lab Environment Setup

Operating System Windows  
Web Server Stack XAMPP Apache MySQL PHP  
Target Application DVWA  
Access URL  
http://localhost/DVWA-master/login.php

Setup Steps

1 Installed XAMPP and started Apache and MySQL  
2 Placed DVWA folder inside C:\xampp\htdocs\DVWA-master  
3 Opened DVWA in browser and logged in using default credentials  
   Username admin  
   Password password  
4 Set DVWA Security Level to Low

Understanding SQL Injection

SQL Injection occurs when user input is directly embedded into SQL queries without validation or sanitization.

A vulnerable query typically looks like:

SELECT * FROM users WHERE id = '$id';

Because the input is not handled safely, an attacker can inject additional SQL logic that alters the behavior of the query.

This is not a flaw in SQL itself, but in how applications build SQL queries.

Exploitation Demonstration

Step 1 Normal Behavior

On the DVWA SQL Injection page, entering:

1

returns information for a single user.

This confirms normal database behavior.

Step 2 Injected Input

When the input field is provided with:

1 OR 1=1

the application constructs the following SQL query internally:

SELECT * FROM users WHERE id = 1 OR 1=1;

Since the condition 1=1 is always true, the database returns all user records.

This demonstrates a successful SQL Injection exploit.

Evidence Captured

The following evidence was recorded for documentation and demo:

Output of normal query using input 1  
Output after injection showing multiple records  
DVWA security configuration  
Exploit demonstration screen recording

Root Cause Analysis

The vulnerability exists because user input is directly concatenated into SQL statements.  
No input validation or parameterization is applied.  
The database engine executes injected SQL logic as part of the original query.

Remediation and Patching

To prevent SQL Injection:

1 Use Prepared Statements

Prepared statements separate SQL code from user input.

SELECT * FROM users WHERE id = ?;

The value is bound safely, preventing injected logic from executing.

2 Validate Input

Ensure only expected data types are accepted.

3 Least Privilege

Database accounts should only have the permissions they require.

4 Avoid Detailed Error Messages

Errors should not reveal database structure or query details.

Repository Artifacts

sql_injection_exploit.sh

This file documents the controlled exploitation steps for educational and audit purposes.  
It is not an attack tool.  
It records the process and conclusions of the security test.

Demo Video

The demonstration video shows DVWA environment, security configuration, normal query, exploit result, and explanation of vulnerability and fix.

Learning Outcome

This task demonstrates how insecure coding practices directly lead to exploitable vulnerabilities.  
It highlights the importance of secure query handling and defensive programming.

The exercise reinforces the mindset required for both security professionals and developers to design safer systems.

# Task 7: Vulnerability Scanning with Nikto

## Objective
The objective of this task is to perform vulnerability scanning on a web server using the Nikto tool, analyze the discovered issues, and document the findings.

## Tool Used
Nikto v2.5.0

## Target Scanned
https://demo.testfire.net  
Port: 443 (HTTPS)

## Scan Command Used
perl nikto.pl -h https://demo.testfire.net -ssl -o nikto_scan_results.txt

## Summary of Findings

1. Missing Critical Security Headers  
The web server is missing several recommended security headers including:
Strict-Transport-Security  
X-Content-Type-Options  
Content-Security-Policy  
Referrer-Policy  
Permissions-Policy  

These missing headers increase the risk of attacks such as man-in-the-middle, cross-site scripting, MIME-type sniffing, and information leakage.

2. Dangerous HTTP Methods Enabled  
The server allows HTTP methods such as PUT and DELETE.  
If improperly secured, these methods may allow attackers to upload or remove files on the server.

3. Server Information Disclosure  
The server exposes details such as its web server type and TLS configuration.  
This information can help attackers craft more targeted attacks.

4. TLS Security Observations  
Although HTTPS is enabled, the absence of Strict-Transport-Security weakens protection and may allow downgrade attacks.

## Recommendations

Implement all recommended HTTP security headers.  
Restrict dangerous HTTP methods unless strictly required.  
Reduce server information exposure.  
Enforce stronger TLS security policies.

## Conclusion
The Nikto scan revealed multiple security weaknesses that could be exploited if left unaddressed. Regular vulnerability scanning and proper security configuration are essential for maintaining a secure system.

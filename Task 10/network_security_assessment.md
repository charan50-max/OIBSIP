Network Security Assessment Report
1. Introduction

This security assessment was conducted as part of a practical learning exercise to evaluate the security posture of a local network and web application environment. The assessment focused on identifying exposed services, analyzing live network traffic, detecting vulnerabilities, and suggesting appropriate security controls.

The tools used in this assessment were Nmap for network scanning and Wireshark for packet capture and traffic analysis.

2. Scope of Assessment

Target Environment
Localhost system running XAMPP and DVWA web application

Tools Used
Nmap
Wireshark

Objectives
Identify open services and potential attack surfaces
Capture and analyze live network traffic
Detect vulnerabilities and security weaknesses
Provide remediation recommendations

3. Nmap Scan Summary

The following command was executed:

nmap -A 127.0.0.1

Key Findings
Port	Service	Details
80	HTTP	Apache 2.4.58 with PHP 8.2.12
443	HTTPS	Apache with expired SSL certificate
135	MSRPC	Windows Remote Procedure Call
445	SMB	Microsoft file sharing
3306	MySQL	MariaDB 10.4.32
1033,1042,1043	Unknown	Custom HTTP based services
Critical Observations

• HTTPS certificate expired in 2019
• Database service exposed on port 3306
• Multiple unnecessary services running
• Development stack publicly accessible

4. Wireshark Traffic Analysis

Live network traffic was captured while interacting with the DVWA application.

Observed Protocols

HTTP
MySQL
TCP

HTTP Evidence

Captured requests included:

GET /DVWA-master/vulnerabilities/sqli/
GET /DVWA-master/vulnerabilities/sqli/?id=1' UNION SELECT user,password FROM users#


Responses:

HTTP/1.1 200 OK


This confirms that SQL injection payloads are transmitted in clear text.

MySQL Evidence

Captured packets revealed:

Server Greeting version 10.4.32 MariaDB
Login Request user=root
Login Request user=root db=dvwa
Response TABULAR Response


This shows that database authentication and query results are exposed over the network in clear text.

5. Identified Vulnerabilities
Vulnerability	Risk Level
Clear text SQL injection traffic	High
Clear text database credentials	High
Use of root account by web application	High
Expired SSL certificate	High
Exposed MySQL service	High
Unnecessary open services	Medium
6. Risk Impact Analysis

These vulnerabilities could allow attackers to:

• Steal database credentials
• Extract sensitive information
• Modify or destroy data
• Perform lateral movement across the system
• Compromise the entire server

7. Recommendations

Enforce HTTPS with a valid SSL certificate

Disable unnecessary services and ports

Restrict MySQL network access

Use a dedicated low privilege database user

Encrypt database connections

Implement Web Application Firewall

Apply regular patching and updates

Conduct periodic security audits

8. Conclusion

This assessment demonstrated how vulnerable development environments can expose serious security risks when basic security practices are ignored. The use of Nmap and Wireshark provided concrete technical evidence of vulnerabilities that could lead to complete system compromise if deployed in a real production environment.

Implementing the recommended controls would significantly improve the security posture of the system.
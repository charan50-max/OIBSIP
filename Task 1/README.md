Task 1
Nmap installation and local system scan
Tools: Nmap with Zenmap GUI, Windows 11
Target: 127.0.0.1 (Local system)
Profile: Intense Scan
ports/hosts:
port | service
135 | msrcp
445 | microsoft-ds
1042 | afrog
1043 | boinc
3306 | MySQL
7778 | interwise
Inference:
Open ports are entry points into a system.  
If these ports are exposed on a public network, attackers can attempt to exploit the services.  
Critical services like SMB (445) and MySQL (3306) must always be protected using firewall rules and authentication.
The scan demonstrates how Nmap can identify active services and help administrators evaluate system exposure.
Files Included
1 `scan_output.png` — Screenshot of Zenmap GUI output  
2 `nmap_scan_results.txt` — Summarized findings and security analysis  
3 `raw_nmap_output.txt` — Complete unfiltered Nmap scan log

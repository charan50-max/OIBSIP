# Basic Firewall Configuration using UFW

This task demonstrates how to configure a basic firewall on Linux using UFW.

## Objectives
- Enable firewall protection
- Allow SSH traffic
- Deny HTTP traffic
- Verify rule enforcement

## Steps Performed

1. Installed and initialized UFW.
2. Set default policies:
   - Deny incoming connections
   - Allow outgoing connections
3. Allowed SSH (port 22).
4. Denied HTTP (port 80).
5. Enabled the firewall.
6. Verified configuration using:
   sudo ufw status verbose
7. Tested enforcement:
   - curl http://localhost → Blocked
   - ssh localhost → Allowed

## Result
Firewall is active with correct rules enforced.

# TryHackMe - Network Security Essentials 


## Overview

This report details my analysis and findings from the Network Security Essentials room on TryHackMe.
This room focuses on the key aspects of network security essentials and how to monitor and protect against adversaries.


## Tools

- Command-line tools and Splunk available in the provided VM.

## Steps Taken 

The investigation is structured into a logical kill-chain analysis using manual command-line tools and Splunk.

1. **Reconnaissance & Initial Access**
   - Firewall Analysis: Analysts scanned `firewall.log` for `BLOCK` entries.
   - Finding: An external IP was probing internal ranges on common ports.
   - Action: Identified the top attacking IP using frequency analysis.
   - Correlation: Checked if this external IP had any `ALLOW` entries, confirming the attacker bypassed the perimeter via exploitation.
2. **Credential Access (VPN Brute-force)**
   - VPN Log Analysis: Examined `vpn_auth.log` for `FAIL` attempts.
   - Finding: The suspicious external IP targeted a specific user account with multiple failed attempts before a successful login.
   - Result: The attacker was assigned an internal IP address upon successful authentication.
3. **Lateral Movement**
   - Internal Scanning: Filtered `firewall.log` for the newly compromised internal IP.
   - Finding: The host scanned internal peers on SMB (445), RDP (3389), and SSH (22).
   - IDS Alerts: Cross-referenced with `ids_alerts.log`.
   - Finding: Alerts confirmed the exploitation of SMB vulnerabilities to move laterally across the network.
4. **Command & Control (C2)**
   - Beaconing Detection: Searched `ids_alerts.log` for "C2" indicators.
   - Finding: The compromised host established a connection to an external C2 server, sending periodic beacons.
   - Action: Identified the external C2 IP address and the specific internal host communicating with it.
5. **Data Exfiltration**
   - Traffic Analysis: Filtered `firewall.log` for high-volume outbound traffic from the compromised host.
   - Finding: Large data transfers were sent from the internal host to an external destination IP.
   - Confirmation: Correlated with IDS alerts to confirm exfiltration attempts.


## Skills Acquired

- **Attack Chain Reconstruction**: Mapping the MITRE ATT&CK lifecycle (Reconnaissance → Initial Access → Credential Access → Lateral Movement → C2 → Exfiltration);
- **Correlation**: Connecting events across three different log sources to tell a cohesive story;
- **Indicator of Compromise (IoC) Extraction**: Identifying specific malicious IPs, usernames, ports, and vulnerability signatures;
- **Splunk Fundamentals**: Understanding how to ingest logs and query an index for faster analysis.


## Key Takeaways

- Defense in Depth Matters: The attacker bypassed the firewall via exploitation and VPN brute-forcing, highlighting the need for MFA and strict egress filtering;
- Log Correlation is Critical;
- C2 Beaconing Patterns: IDS rules are highly effective at identifying malware beaconing to remote C2 servers.

## Disclaimer

This lab writeup is for educational and portfolio purposes only.
No real-world incident data is included, and no platform-protected solutions are disclosed.
The goal of this document is to demonstrate analysis workflow and blue team methodology, not to share sensitive information or provide direct challenge answers.

# TryHackMe - Splunk Basics - Did you SIEM?


## Overview

This report details my analysis and findings from the Splunk Basics - Did you SIEM? room on TryHackMe. 
Investigate a cyberattack using Splunk to identify the attacker, analyze the attack timeline, and quantify data exfiltration.


## Tools

- VM attached in this room by TryHackMe.


## Skills Acquired

- **Log Correlation**: The ability to link data across different data sources to trace an attack from the initial web request to outbound data exfiltration.
- **Anomaly Detection**: Techniques for identifying suspicious patterns by filtering out "noise" to isolate unique signatures like non-standard User Agents or specific IP behaviors.
- **Attack Chain Analysis**: **Understanding the kill chain phases (Reconnaissance, Enumeration, Exploitation, RCE, Exfiltration)
- Indicator** of Compromise (IoC) Identification: Recognizing that `curl`, `wget`, `..\/..\/`, `redirect`, `SLEEP`, `shell.php` signal a breach.
- **Incident Quantification**: Calculating the scope of an incident by aggregating metrics like event counts, attempt frequencies, and total bytes exfiltrated.


## Steps Taken

1. **Initial Triage**: Search web_traffic logs across all time and visualize the event count per day to identify the peak traffic date;
2. **Find the Attacker**: Use the user_agent section to reveal traffic and identify the specific malicious `client_ip`;
3. **Trace the Attack Chain** using the identified IP and run targeted queries to uncover:
   - Reconnaissance: Probing for config files (.env, .git).
   - Enumeration: Path traversal and redirect attempts.
   - Exploitation: SQL injection attacks (using sqlmap/Havij).
   - Compromise: RCE via webshells and ransomware staging.
   - Exfiltration: Downloads of sensitive archives.
   - Correlate C2 & Data Loss: Pivot to firewall_logs to trace outbound connections from the compromised server to the attacker's IP, confirming the Command & Control channel and calculating total bytes transferred.
4. **Finalize Findings**: Extract the attacker IP, peak date, specific attack counts, and total exfiltrated data volume;
5. **Successfully answered all exercise questions** by accurately analyzing the Splunk logs and applying the investigative steps outlined in the guide.


## Key Takeaways

- Filter to Find Noise: Legitimate traffic often drowns out attacks and filtering is the most effective way to isolate malicious actors;
- Timeline First: Visualizing data over time is crucial for pinpointing when an attack occurred and identifying the peak volume of activity;


## Disclaimer

This lab writeup is for educational and portfolio purposes only.
No real-world incident data is included, and no platform-protected solutions are disclosed.
The goal of this document is to demonstrate analysis workflow and blue team methodology, not to share sensitive information or provide direct challenge answers.

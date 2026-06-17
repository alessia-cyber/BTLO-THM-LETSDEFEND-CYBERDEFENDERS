# TryHackMe - Introduction to SIEM


## Overview

This report details my analysis and findings from the Introduction to SIEM room on TryHackMe.
The room focuses on the fundamentals of SIEM and how it works.


## Tools

- Static lab attached in the room.


## Steps Taken

1. **Triggered the Incident**: Clicked the "Start Suspicious Activity" button to simulate an attacker and generate the necessary logs for the SIEM to detect;
2. **Located the Alert**: Navigated to the SIEM dashboard to find and select the newly triggered alert;
3. **Identified the Attacker**: Drilled down into the specific event associated with the alert to extract the responsible user and their hostname;
4. **Analyzed the Rule**: Examined the detection rule details to determine exactly which term in the suspicious process matched the alert criteria;
5. **Validated the Alert**: Confirmed the event was a True Positive;
6. **Retrieved the Flag**: Selected the correct resolution action in the interface to unlock and collect the final flag.


## Skills Acquired

- **SIEM Alert Triage**: Successfully navigated a Security Information and Event Management interface to locate and investigate triggered alerts;
- **Log Forensics**: Extracted critical forensic details (username, hostname, process name) directly from raw event logs to attribute an attack;
- **Incident Validation**: Distinguished between legitimate threats and noise by correctly classifying an alert as a True Positive.


## Key Takeaways

- Investigation over Automation: While alerts trigger automatically, the critical skill lies in human investigation;
- Attribution is Key: Effective incident response relies on quickly identifying the User and Hostname to contain the threat and understand the scope of the breach.


## Disclaimer

This lab writeup is for educational and portfolio purposes only. 
No real-world incident data is included, and no platform-protected solutions are disclosed. 
The goal of this document is to demonstrate analysis workflow and blue team methodology, not to share sensitive information or provide direct challenge answers.



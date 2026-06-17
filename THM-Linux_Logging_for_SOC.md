# TryHackMe - Linux Logging for SOC


## Overview
This report details my analysis and findings from the Linux Logging for SOC room on TryHackMe.
Through this room, I mastered critical Linux log sources to conduct more effective incident triage.


## Tools

- VM attached in this room by TryHackMe.

## Skills Acquired

- **Comprehensive Log Analysis**: Explored and analyzed authentication, runtime, and system logs on Linuxto identify security anomalies and reconstruct incident timelines;
- **Commands for Log Manipulation**: Mastered essential CLI commands for log manipulation (grep);
- **Auditd and System Monitoring**: Uncovered the inner workings of auditd to understand how the Linux kernel monitors and reports critical events;
- **Event Filtering and Discovery**: Developed techniques to efficiently filter raw log data and discover hidden artifacts, including Bash history analysis to trace user activity and command execution.


## Key Takeaways

- **Log Sources are Critical**: Understanding the difference between authentication logs, system logs, and runtime logs is essential for accurate triage. Each source tells a unique part of the attack story.
- **Auditd is Powerful but Noisy**: While auditd provides granular visibility into system calls, it generates a high volume of data. Success depends on writing precise rules and using tools like ausearch to filter effectively, rather than relying on raw log files.
- **The Art of Filtering**: The most important skill in SOC triage is knowing what to ignore. Learning to filter out "noise" to find the specific indicators of compromise (IOCs) is more valuable than simply collecting every log entry.


## Disclaimer

This lab writeup is for educational and portfolio purposes only.
No real-world incident data is included, and no platform-protected solutions are disclosed.
The goal of this document is to demonstrate analysis workflow and blue team methodology, not to share sensitive information or provide direct challenge answers.

# backdoor-incident
## Description

This project simulates a SOC investigation into suspicious activity detected across multiple Windows systems. Anomalous behaviour was identified in host logs, suggesting that an adversary may have gained access to internal machines and established a persistent backdoor. As part of the investigation, logs from the affected systems were collected and ingested into Splunk for centralized analysis.

The objective of this exercise is to analyse Windows Event Logs to identify indicators of compromise, trace malicious activity, and reconstruct the attack chain. This includes examining process execution events, PowerShell activity, and potential lateral movement within the environment.

The investigation focuses on identifying how the compromise occurred, how the attacker maintained access, and which systems were impacted, using Splunk as the primary tool for log analysis and correlation.

## Lessons Learned
This investigation highlighted the importance of continuous monitoring and detailed logging within Windows environments. The attack demonstrated how PowerShell can be abused to execute fileless malware, bypass security controls, and communicate with external command-and-control infrastructure.

A key takeaway is the need for enhanced PowerShell logging (including Script Block Logging and transcription), as well as monitoring for encoded commands and obfuscated scripts. The use of legitimate administrative tools such as WMIC for lateral movement also reinforces the importance of detecting dual-use (“living off the land”) binaries.

Additionally, the creation of unauthorized user accounts emphasises the need for strong identity and access controls, along with alerting on privilege changes and account creation events.

This scenario demonstrates how quickly an attacker can escalate from initial execution to full compromise, highlighting the value of proactive detection, log correlation, and timely incident response.

## How to Prevent Similar Incidents in the Future
To reduce the risk of similar attacks, organisations should strengthen monitoring, restrict high-risk execution methods, and improve endpoint security configurations. PowerShell should be tightly controlled by enabling full logging capabilities, including Script Block Logging, Module Logging, and transcription, to ensure malicious activity is visible during execution.

Execution of encoded or obfuscated PowerShell commands (such as -enc) should be monitored and flagged, as these are commonly used to conceal malicious activity. Additionally, security tools such as AMSI and Defender should remain enabled and protected from tampering or bypass attempts.

Remote administration tools like WMIC should be restricted or monitored for unusual usage, especially when used for remote process creation or lateral movement. Least privilege principles should also be enforced to prevent standard users from executing administrative tasks across systems.

Finally, monitoring should be enhanced for suspicious account creation, privilege escalation, and unusual process chains. Centralised logging and correlation through tools like Splunk can help detect early indicators of compromise and allow for faster incident response.

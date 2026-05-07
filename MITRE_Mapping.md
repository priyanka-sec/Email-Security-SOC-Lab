# MITRE ATT&CK Mapping — Phishing Technique

The phishing attack performed in this lab was mapped to the MITRE ATT&CK framework to understand the adversary technique used for initial access.

| Tactic | Technique | ID | Explanation |
|---|---|---|---|
| Initial Access | Phishing | T1566 | Email used as the entry point to target the victim |
| Initial Access | Spearphishing Link | T1566.002 | Malicious password reset link embedded in email |
| Command & Control | Application Layer Protocol (SMTP) | T1071.003 | SMTP protocol abused to deliver phishing email |


<br><br>


## Analyst Note

The subject line "Urgent: Reset Your Password Immediately" demonstrates a classic social engineering tactic used in phishing attacks to create fear and urgency.

Mapping incidents to MITRE ATT&CK helps SOC teams:
- Classify the attack technique
- Improve detection strategies
- Align security controls with known adversary behaviors

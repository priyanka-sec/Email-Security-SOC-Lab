# Indicators of Compromise (IOCs)

During the email header and body analysis, the following Indicators of Compromise were identified.

These IOCs help a SOC Analyst detect, block, and investigate similar phishing attempts in a real environment.

| IOC Type | Value | Description | Verdict |
|---|---|---|---|
| IP Address | 192.168.56.10 | Source of phishing email (Kali Linux attacker) | Malicious (Lab) |
| Email Address | attacker@lab.local | Spoofed sender identity | Malicious |
| Email Address | victim@lab.local | Target user mailbox | Victim |
| URL | http://192.168.56.10/reset | Fake password reset phishing link | Malicious |
| Tool Signature | swaks | SMTP tool used to craft the email | Suspicious |
| Domain | lab.local | Internal lab domain | Internal |


<br><br>


## SOC Insight

IOCs extracted from email headers are critical for:
- Blocking attacker IPs at firewall level
- Blacklisting malicious sender addresses
- Updating email filtering rules
- Creating SIEM detection rules for similar patterns

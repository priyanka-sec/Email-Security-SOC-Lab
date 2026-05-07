<h1 align="center">Email Security SOC Lab — Phishing Detection & Investigation</h1>

<p align="center">
Phishing email simulation, detection, and forensic investigation using 
Kali Linux • Windows Server 2022 • hMailServer • MITRE ATT&CK
</p>

This project demonstrates the complete workflow a SOC Analyst follows to investigate a phishing email from SMTP delivery to MITRE ATT&CK mapping, using real forensic evidence from a mail server.

A phishing attack was simulated from an attacker machine running Kali Linux to a victim mail server running Windows Server 2022 with hMailServer, all hosted inside Oracle VM VirtualBox. The phishing email was crafted using the `swaks` SMTP testing tool.





## Objective
- Simulate a phishing email attack using SMTP
- Capture the email on the mail server
- Perform email header forensic analysis
- Extract Indicators of Compromise (IOCs)
- Validate IOCs with threat intelligence
- Map the attack to relevant MITRE ATT&CK techniques
- Produce a professional SOC incident report





## 🧰 Lab Environment

| Component | Role |
|---|---|
| Kali Linux | Attacker machine |
| Windows Server 2022 | Victim mail server |
| hMailServer | SMTP mail server |
| Oracle VM VirtualBox | Virtualization platform |
| swaks | SMTP tool used to craft phishing email |





## Attack Scenario Summary

An attacker used `swaks` from Kali Linux to send a spoofed phishing email to a victim mailbox hosted on hMailServer.  
The objective was to investigate how a SOC Analyst detects the real sender, extracts evidence from email headers, identifies IOCs, and maps the attack to the MITRE ATT&CK framework.




## 🗺️ Network Topology

```
Kali Linux (192.168.56.10)  --->  Windows Server 2022 (192.168.56.110)
        Attacker                          Victim Mail Server
```





## 🧪 Attack Simulation
A phishing email was deliberately crafted and transmitted using `swaks` from the attacker machine to the victim mailbox for forensic investigation purposes.

The email contained:
- Spoofed sender address
- Urgent social engineering subject
- Fake password reset link





## 🔍 Investigation Workflow
1. Email delivered to hMailServer mailbox
2. Raw `.eml` file extracted from mail server path
3. Email header opened and analyzed
4. Real attacker IP identified from the `Received` header field
5. IOCs extracted from header and body
6. URL/IP checked on VirusTotal
7. Attack mapped to MITRE ATT&CK T1566
8. Incident report prepared





## 📸 Investigation Evidence (Screenshots)

All screenshots are available in the `Screenshots` folder, showing:

| Screenshot Category | Evidence Provided |
|---|---|
| VM setup & connectivity | Network communication between attacker and victim |
| hMailServer configuration | Proper SMTP server setup |
| Phishing email sent | Attack simulation from Kali Linux |
| Mail logs | Successful email delivery proof |
| Header analysis | Forensic evidence from email |
| IOC extraction | Indicators identified from attack |
| MITRE mapping | Technique classification |
| Incident report | Final SOC documentation |





## 📄 Documentation

- `Email_Header_Analysis.md` — Header breakdown
- `IOC_Table.md` — Indicators of Compromise
- `MITRE_Mapping.md` — ATT&CK technique mapping
- `Incident_Report.pdf` — Full SOC incident report





## 🧠 Skills Demonstrated
SMTP Configuration • Email Forensics • Phishing Detection • IOC Extraction • Threat Intelligence • MITRE ATT&CK Mapping • SOC Incident Reporting





> This project follows the exact workflow a SOC Analyst performs during a phishing email investigation in a real environment.





## Conclusion
This lab replicates a real-world SOC phishing investigation and demonstrates practical detection and analysis skills required for a SOC Analyst role.

This project showcases practical, hands-on SOC skills aligned with real-world phishing incident investigations.

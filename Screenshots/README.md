<h1 align="center">📸 Investigation Evidence — Screenshots Guide</h1>

This folder contains all the visual evidence collected during the phishing email investigation performed in this SOC lab.

Each screenshot represents an important step of the investigation workflow followed by a SOC Analyst, from lab setup to forensic analysis and reporting.


<br><br>


## 🖥️ VM Setup & Network Connectivity

| Screenshot | Description |
|---|---|
| 01_Kali_IP.png | Shows the IP address of the attacker machine (Kali Linux) |
| 02_Windows_Server_IP.png | Shows the IP address of the victim mail server |
| 03_Ping_Test.png | Successful ping test proving network connectivity between attacker and victim |


<br><br>


## ⚙️ hMailServer Configuration

| Screenshot | Description |
|---|---|
| 04_hMailServer_Domain_Setup.png | Domain configured inside hMailServer |
| 05_hMailServer_Account_Creation.png | Mailbox account created for the victim user |
| 06_SMTP_Settings.png | SMTP service enabled and configured |


<br><br>


## 🎣 Phishing Email Attack Simulation

| Screenshot | Description |
|---|---|
| 07_Swaks_Phishing_Command.png | `swaks` command used to send the phishing email from Kali Linux |
| 08_Email_Sent_Success.png | Confirmation that the phishing email was successfully sent |


<br><br>


## 📬 Mail Server Logs & Email Delivery

| Screenshot | Description |
|---|---|
| 09_hMailServer_Logs.png | Mail server logs showing successful email delivery |
| 10_Victim_Mailbox_Email.png | Phishing email received in the victim mailbox |


<br><br>


## 🧪 Email Header Forensic Analysis

| Screenshot | Description |
|---|---|
| 11_Email_Header_View.png | Raw email header opened for analysis |
| 12_Received_Header_IP.png | `Received` header showing the real sender IP address |
| 13_Spoofed_Sender_Proof.png | Evidence of spoofed sender email address |


<br><br>


## 🚨 IOC Extraction

| Screenshot | Description |
|---|---|
| 14_IOC_IP_Address.png | Malicious IP extracted from email header |
| 15_IOC_Malicious_URL.png | Phishing URL extracted from email body |


<br><br>


## 🌐 Threat Intelligence Validation

| Screenshot | Description |
|---|---|
| 16_VirusTotal_IP_Check.png | VirusTotal result for the attacker IP |
| 17_VirusTotal_URL_Check.png | VirusTotal result for the phishing URL |


<br><br>


## 🗺️ MITRE ATT&CK Mapping

| Screenshot | Description |
|---|---|
| 18_MITRE_T1566.png | Mapping the phishing attack to MITRE ATT&CK technique T1566 |


<br><br>


## 📝 SOC Incident Report

| Screenshot | Description |
|---|---|
| 19_Incident_Report.png | Final SOC incident report prepared based on the investigation |


<br><br>


These screenshots serve as forensic proof of the phishing simulation, investigation process, IOC validation, and MITRE ATT&CK mapping performed in this SOC lab.

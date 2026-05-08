<h1 align="center">📸 Investigation Evidence — Screenshots Guide</h1>

This folder contains all the visual evidence collected during the phishing email investigation performed in this SOC lab.

Each screenshot represents an important step of the investigation workflow followed by a SOC Analyst, from lab setup to forensic analysis and reporting.


<br><br>


## 🖥️ VM Setup & Network Connectivity

| Screenshot | Description |
|---|---|
| ![01_VirtualBox_both_VMs_running](01_VirtualBox_both_VMs_running.jpg) | Both Kali Linux and Windows Server 2022 virtual machines running in VirtualBox |
| ![02_KaliLinux_ip_address_eth0_eth1](02_KaliLinux_ip_address_eth0_eth1.jpg) | Shows the IP address of the attacker machine (Kali Linux) |
| ![03_WindowsServer_ipconfig_both_adapters](03_WindowsServer_ipconfig_both_adapters.jpg) | Shows the IP address of the victim mail server |
| ![04_KaliLinux_ping_to_WindowsServer](04_KaliLinux_ping_to_WindowsServer.jpg) | Ping test from Kali Linux to Windows Server |
| ![05_WindowsServer_ping_to_KaliLinux](05_WindowsServer_ping_to_KaliLinux.jpg) | Ping test from Windows Server to Kali Linux |


<br><br>


## ⚙️ hMailServer Configuration

| Screenshot | Description |
|---|---|
| ![04_hMailServer_Domain_Setup](04_hMailServer_Domain_Setup.png) | Domain configured inside hMailServer |
| ![05_hMailServer_Account_Creation](05_hMailServer_Account_Creation.png) | Mailbox account created for the victim user |
| ![06_SMTP_Settings](06_SMTP_Settings.png) | SMTP service enabled and configured |


<br><br>


## 🎣 Phishing Email Attack Simulation

| Screenshot | Description |
|---|---|
| ![07_Swaks_Phishing_Command](07_Swaks_Phishing_Command.png) | swaks command used to send the phishing email from Kali Linux |
| ![08_Email_Sent_Success](08_Email_Sent_Success.png) | Confirmation that the phishing email was successfully sent |


<br><br>


## 📬 Mail Server Logs & Email Delivery

| Screenshot | Description |
|---|---|
| ![09_hMailServer_Logs](09_hMailServer_Logs.png) | Mail server logs showing successful email delivery |
| ![10_Victim_Mailbox_Email](10_Victim_Mailbox_Email.png) | Phishing email received in the victim mailbox |


<br><br>


## 🧪 Email Header Forensic Analysis

| Screenshot | Description |
|---|---|
| ![11_Email_Header_View](11_Email_Header_View.png) | Raw email header opened for analysis |
| ![12_Received_Header_IP](12_Received_Header_IP.png) | Received header showing the real sender IP address |
| ![13_Spoofed_Sender_Proof](13_Spoofed_Sender_Proof.png) | Evidence of spoofed sender email address |


<br><br>


## 🚨 IOC Extraction

| Screenshot | Description |
|---|---|
| ![14_IOC_IP_Address](14_IOC_IP_Address.png) | Malicious IP extracted from email header |
| ![15_IOC_Malicious_URL](15_IOC_Malicious_URL.png) | Phishing URL extracted from email body |


<br><br>


## 🌐 Threat Intelligence Validation

| Screenshot | Description |
|---|---|
| ![16_VirusTotal_IP_Check](16_VirusTotal_IP_Check.png) | VirusTotal result for the attacker IP |
| ![17_VirusTotal_URL_Check](17_VirusTotal_URL_Check.png) | VirusTotal result for the phishing URL |


<br><br>


## 🗺️ MITRE ATT&CK Mapping

| Screenshot | Description |
|---|---|
| ![18_MITRE_T1566](18_MITRE_T1566.png) | Mapping the phishing attack to MITRE ATT&CK technique T1566 |


<br><br>


## 📝 SOC Incident Report

| Screenshot | Description |
|---|---|
| ![19_Incident_Report](19_Incident_Report.png) | Final SOC incident report prepared based on the investigation |


<br><br>


These screenshots serve as forensic proof of the phishing simulation, investigation process, IOC validation, and MITRE ATT&CK mapping performed in this SOC lab.

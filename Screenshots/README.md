<h1 align="center">📸 Investigation Evidence — Screenshots</h1>

<p align="center">
This folder contains all visual evidence collected during the phishing email investigation.<br>
Each screenshot represents a specific step in the SOC analyst investigation workflow.
</p>

<br><br>

## 📋 Table of Contents

- [VM Setup & Network Connectivity](#-vm-setup--network-connectivity)
- [hMailServer Configuration](#️-hmailserver-configuration)
- [Firewall Configuration](#-firewall-configuration)
- [Phishing Attack Simulation](#-phishing-attack-simulation)
- [Email Delivery Confirmation](#-email-delivery-confirmation)
- [Email Header Forensic Analysis](#-email-header-forensic-analysis)
- [Threat Intelligence Validation](#-threat-intelligence-validation)
- [MITRE ATT&CK Mapping](#️-mitre-attck-mapping)

<br><br>

## 🖥️ VM Setup & Network Connectivity

### Screenshot 01 — VirtualBox Both VMs Running
![01_VirtualBox_both_VMs_running](01_VirtualBox_both_VMs_running.jpeg)
> Both Kali Linux (attacker) and Windows Server 2022 (victim mail server) running simultaneously in Oracle VirtualBox — confirming the lab environment is fully active and ready.

<br><br>

### Screenshot 02 — Kali Linux IP Addresses
![02_KaliLinux_ip_address_eth0_eth1](02_KaliLinux_ip_address_eth0_eth1.jpeg)
> Kali Linux IP addresses confirmed using the `ip a` command — eth0 (NAT: 10.0.3.15) for internet access and eth1 (Host-Only: 192.168.57.11) for lab communication with Windows Server.

<br><br>

### Screenshot 03 — Windows Server IP Configuration
![03_WindowsServer_ipconfig_both_adapters](03_WindowsServer_ipconfig_both_adapters.jpeg)
> Windows Server 2022 IP configuration confirmed using `ipconfig` — NAT adapter (10.0.3.14) and Host-Only adapter (192.168.57.110) both active.

<br><br>

### Screenshot 04 — Ping from Kali to Windows Server
![04_KaliLinux_ping_to_WindowsServer](04_KaliLinux_ping_to_WindowsServer.jpg)
> Successful ping from Kali Linux to Windows Server (192.168.57.110) — confirms the two VMs can communicate over the Host-Only network. This is required for the phishing email to be delivered.

<br><br>

### Screenshot 05 — Ping from Windows Server to Kali
![05_WindowsServer_ping_to_KaliLinux](05_WindowsServer_ping_to_KaliLinux.png)
> Successful ping from Windows Server to Kali Linux (192.168.57.11) — confirms bidirectional network connectivity between attacker and victim machines.

<br><br>

## ⚙️ hMailServer Configuration

### Screenshot 06 — lab.local Domain Created
![06_hMailServer_lab_local_domain_created](06_hMailServer_lab_local_domain_created.jpg)
> Local mail domain `lab.local` created inside hMailServer Administrator — this is the email domain used for all mailboxes in the lab. Equivalent to a corporate email domain in a real organisation.

<br><br>

### Screenshot 07 — Victim Account Creation
![07_hMailServer_victim_account_creation](07_hMailServer_victim_account_creation.jpg)
> Victim mailbox `victime@lab.local` created in hMailServer — this account plays the role of an innocent employee who receives the phishing email.

<br><br>

### Screenshot 08 — Attacker Account Creation
![08_hMailServer_attacker_account_creation](08_hMailServer_attacker_account_creation.jpg)
> Attacker mailbox `attacker@lab.local` created in hMailServer — this account is used as the spoofed sender identity in the phishing email.

<br><br>

### Screenshot 09 — Both Accounts Listed
![09_hMailServer_both_accounts_listed](09_hMailServer_both_accounts_listed.jpg)
> Both attacker and victim accounts visible under the lab.local domain in hMailServer — confirms successful account setup for the phishing simulation.

<br><br>

### Screenshot 10 — SMTP Settings
![10_hMailServer_SMTP_settings](10_hMailServer_SMTP_settings.jpg)
> SMTP protocol settings in hMailServer — Maximum connections set to 0 (unlimited) and maximum message size set to 20480 KB. Port 25 is active for email delivery.

<br><br>

### Screenshot 10b — SMTP Delivery Settings
![10b_hMailServer_SMTP_delivery_settings](10a_hMailServer_SMTP_delivery_settings.jpg)
> SMTP delivery settings configured — Local host name set to Windows Server Host-Only IP (192.168.57.110). This tells hMailServer its own network address so Kali Linux can deliver emails to it correctly.

<br><br>

### Screenshot 11 — hMailServer Status Running
![11_hMailServer_status_running](11_hMailServer_status_running.jpg)
> hMailServer status page showing all services are running — SMTP (port 25), POP3 (port 110), and IMAP (port 143) all active and listening for connections.

<br><br>

### Screenshot 11b — Kali Linux IP Added to IP Ranges
![11b_hMailServer_IP_ranges_Kali_added](11a_hMailServer_IP_ranges_Kali_added.jpg)
> Kali Linux IP address (192.168.57.11) added to hMailServer trusted IP Ranges with priority 20 — this allows Kali Linux to send emails through the mail server without SMTP authentication, simulating a real attacker bypassing controls.

<br><br>

### Screenshot 11c — TCP/IP Ports Configuration
![11c_hMailServer_TCPIP_ports](11b_hMailServer_TCPIP_ports.jpg)
> TCP/IP ports configured in hMailServer — Port 25 (SMTP), Port 110 (POP3), Port 143 (IMAP), and Port 587 (SMTP) all listening on 0.0.0.0 — meaning they accept connections from all IP addresses including Kali Linux.

<br><br>

## 🔥 Firewall Configuration

### Screenshot 12a — Firewall Port 25 Rule Creation
![12a_WindowsServer_Firewall_Port25_rule_creation](12_WindowsServer_Firewall_Port25_rule_creation.jpg)
> Windows Defender Firewall Inbound Rule created to open TCP Port 25 — this was required because the firewall was blocking Kali Linux from connecting to the mail server. Without this rule, swaks returned "Connection refused".

<br><br>

### Screenshot 12b — Firewall Port 25 Rule Added
![12b_WindowsServer_Firewall_Port25_rule_added](12a_WindowsServer_Firewall_Port25_rule_added.jpg)
> Firewall rule "hMailServer SMTP Port 25" successfully added and visible at the top of the Inbound Rules list — Profile: All, Enabled: Yes, Action: Allow. After this rule was added, Kali Linux was able to connect successfully.

<br><br>

## 🎣 Phishing Attack Simulation

### Screenshot 12c — Phishing Email Sent from Kali Linux
![12c_KaliLinux_swaks_phishing_email_sent](12b_KaliLinux_swaks_phishing_email_sent.png)
> `swaks` command executed from Kali Linux terminal — phishing email successfully sent to victime@lab.local with subject "Urgent: Reset Your Password Immediately". Server responded with `250 Queued` confirming successful delivery. The X-Mailer header reveals the attack tool: swaks v20240103.0.

<br><br>

## 📬 Email Delivery Confirmation

### Screenshot 13 — Email Stored in Victim Mailbox
![13_hMailServer_logs_email_received](13_hMailServer_logs_email_received.jpg)
> Phishing email stored as a .EML file inside the victim mailbox at `C:\Program Files (x86)\hMailServer\Data\lab.local\victime` — direct proof that the email was successfully delivered and stored on the mail server. File size: 538 bytes. Date: 5/6/2026.

<br><br>

## 🔬 Email Header Forensic Analysis

### Screenshot 14 — Raw Email Header
![14_Email_raw_header_analysis](14_Email_raw_header_analysis.jpg)
> Raw email header opened in Notepad showing all forensic fields — Return-Path, Received, Date, To, From, Subject, Message-Id, and X-Mailer. This is the primary evidence used in the SOC investigation to identify the attacker.

<br><br>

### Screenshot 15 — Attacker IP Identified
![15_Email_sender_IP_highlighted](15_Email_sender_IP_highlighted.jpg)
> **Critical forensic finding** — Attacker's real IP address `192.168.56.10` identified in the `Received` header field. Even though the From address was spoofed, the Received field always reveals the true origin IP. This is the most important IOC extracted from this investigation.

<br><br>

## 🌐 Threat Intelligence Validation

### Screenshot 16 — VirusTotal IP Lookup
![16_VirusTotal_sender_IP_lookup](16_VirusTotal_sender_IP_lookup.jpg)
> VirusTotal lookup result for attacker IP `192.168.56.10` — 0/91 security vendors flagged it as malicious, tagged as "private" IP. Expected result for a private lab network address. In a real-world investigation, the public IP of the attacker would be checked here and would likely show malicious detections.

<br><br>

## 🗺️ MITRE ATT&CK Mapping

### Screenshot 17 — MITRE ATT&CK T1566 Phishing
![17_MITRE_ATTCK_T1566_Phishing](17_MITRE_ATTCK_T1566_Phishing.jpg)
> Official MITRE ATT&CK page for Technique T1566 — Phishing. Confirms: Tactic = Initial Access, Sub-techniques = T1566.001 to T1566.004, Platforms = Windows/Linux/macOS. This technique matches exactly what was performed in this lab.

<br><br>

### Screenshot 18 — ATT&CK Navigator T1566 Highlighted
![18_ATTCK_Navigator_T1566_highlighted](18_ATT&CK_Navigator_T1566_highlighted.jpg)
> MITRE ATT&CK Navigator showing T1566 Phishing highlighted in red under the Initial Access tactic column — visual representation of the attack technique used in this investigation. ATT&CK Navigator is a real tool used by SOC teams to track and visualise detected attack techniques.

<br><br>

<p align="center">
  <b>Total Screenshots: 23 &nbsp;|&nbsp; Investigation Steps Covered: 8 &nbsp;|&nbsp; Tools Used: 9</b><br><br>
  All screenshots were taken during a live lab simulation performed by<br>
  <b>Priyanka Rane — SOC Analyst L1</b>
</p>

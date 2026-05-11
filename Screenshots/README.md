<h1 align="center">🛡️ Email Security SOC Lab</h1>
<h3 align="center">Phishing Email Attack Simulation — Detection, Forensic Analysis & MITRE ATT&CK Mapping</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-VirtualBox-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Attacker-Kali%20Linux-red?style=flat-square"/>
  <img src="https://img.shields.io/badge/Victim-Windows%20Server%202022-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/MITRE-T1566%20Phishing-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/Status-Completed-green?style=flat-square"/>
</p>

<br><br>

## 📌 Project Overview

This project demonstrates the **complete SOC analyst workflow** for investigating a phishing email attack — from attack simulation to forensic analysis, IOC extraction, threat intelligence validation, MITRE ATT&CK mapping, and professional incident reporting.

The entire lab was built inside **Oracle VM VirtualBox** using two virtual machines — a **Kali Linux attacker machine** and a **Windows Server 2022 victim mail server** running **hMailServer**.

> This project replicates exactly what a SOC Analyst does during a real phishing email investigation.

<br><br>

## 🎯 Objectives

- ✅ Simulate a phishing email attack using the `swaks` SMTP tool
- ✅ Configure a real mail server (hMailServer) to receive and store emails
- ✅ Extract and forensically analyse raw email headers
- ✅ Identify the attacker's real IP address from the `Received` header field
- ✅ Extract all Indicators of Compromise (IOCs) from the email
- ✅ Validate IOCs using VirusTotal threat intelligence
- ✅ Map the attack to MITRE ATT&CK Technique T1566 — Phishing
- ✅ Produce a professional SOC Incident Report

<br><br>

## 🧰 Tools & Technologies Used

| Tool | Purpose |
|---|---|
| Oracle VM VirtualBox | Virtualisation platform for the lab |
| Kali Linux | Attacker machine |
| Windows Server 2022 | Victim mail server |
| hMailServer | SMTP/POP3/IMAP mail server |
| swaks | SMTP command-line tool used to send phishing email |
| Windows Defender Firewall | Firewall configuration for port 25 |
| Notepad | Raw email header analysis |
| VirusTotal | IOC threat intelligence lookup |
| MITRE ATT&CK Navigator | Attack technique mapping and visualisation |

<br><br>

## 🗺️ Lab Network Topology

```
┌─────────────────────────┐          ┌──────────────────────────────┐
│      Kali Linux         │          │    Windows Server 2022       │
│   Attacker Machine      │          │    Victim Mail Server        │
│                         │          │                              │
│  NAT IP : 10.0.3.15     │─SMTP────▶│  NAT IP  : 10.0.3.14        |
│  H-Only : 192.168.56.10 │  Port 25 │  H-Only  : 192.168.56.110    │
│                         │          │  hMailServer running         │
└─────────────────────────┘          └──────────────────────────────┘
         Adapter 1: NAT                       Adapter 1: NAT
         Adapter 2: Host-Only                 Adapter 2: Host-Only
```

<br><br>

## ⚔️ Attack Scenario

An attacker on **Kali Linux** used the `swaks` SMTP tool to craft and send a spoofed phishing email to a victim mailbox hosted on **Windows Server 2022**.

The phishing email:
- Spoofed the sender identity as `attacker@lab.local`
- Used an urgent subject line: **"Urgent: Reset Your Password Immediately"**
- Contained a fake malicious password reset link
- Was delivered successfully to `victime@lab.local`

<br><br>

## 🔍 Investigation Workflow

```
Step 1 — Lab Setup          →  Configure VMs, network, hMailServer
Step 2 — Attack Simulation  →  Send phishing email using swaks from Kali
Step 3 — Email Discovery    →  Locate .eml file in victim mailbox
Step 4 — Header Analysis    →  Extract attacker IP from Received field
Step 5 — IOC Extraction     →  Identify all indicators from header + body
Step 6 — Threat Intel       →  Validate IOCs on VirusTotal
Step 7 — MITRE Mapping      →  Map to T1566 Phishing — Initial Access
Step 8 — Incident Report    →  Document full investigation professionally
```

<br><br>

## 📸 Investigation Evidence

### 🖥️ Step 1 — VM Setup & Network Connectivity

| Screenshot | Description |
|---|---|
| ![01](01_VirtualBox_both_VMs_running.jpeg) | **01** — Both Kali Linux and Windows Server 2022 VMs running simultaneously in Oracle VirtualBox — confirming the lab environment is fully active |
| ![02](02_KaliLinux_ip_address_eth0_eth1.jpeg) | **02** — Kali Linux IP addresses: eth0 (NAT: 10.0.3.15) and eth1 (Host-Only: 192.168.57.11) confirmed using `ip a` command |
| ![03](03_WindowsServer_ipconfig_both_adapters.jpeg) | **03** — Windows Server 2022 IP configuration: NAT (10.0.3.14) and Host-Only (192.168.57.110) confirmed using `ipconfig` |
| ![04](04_KaliLinux_ping_to_WindowsServer.jpg) | **04** — Successful ping from Kali Linux to Windows Server (192.168.57.110) — confirming Host-Only network communication |
| ![05](05_WindowsServer_ping_to_KaliLinux.png) | **05** — Successful ping from Windows Server to Kali Linux (192.168.57.11) — confirming bidirectional network connectivity |

<br><br>

### ⚙️ Step 2 — hMailServer Configuration

| Screenshot | Description |
|---|---|
| ![06](06_hMailServer_lab_local_domain_created.jpg) | **06** — Local mail domain `lab.local` created inside hMailServer — this is the domain used for all email addresses in the lab |
| ![07](07_hMailServer_victim_account_creation.jpg) | **07** — Victim mailbox account `victime@lab.local` created — this is the target of the phishing attack |
| ![08](08_hMailServer_attacker_account_creation.jpg) | **08** — Attacker mailbox account `attacker@lab.local` created — this is the spoofed sender identity |
| ![09](09_hMailServer_both_accounts_listed.jpg) | **09** — Both attacker and victim accounts visible under lab.local domain in hMailServer — confirming successful account setup |
| ![10](10_hMailServer_SMTP_settings.jpg) | **10** — SMTP protocol settings configured in hMailServer — port 25 enabled for email delivery |
| ![10b](10a_hMailServer_SMTP_delivery_settings.jpg) | **10b** — SMTP delivery settings configured — local host name set to Windows Server IP (192.168.57.110) |
| ![11](11_hMailServer_status_running.jpg) | **11** — hMailServer status showing all services running — SMTP, POP3, and IMAP active |
| ![11b](11a_hMailServer_IP_ranges_Kali_added.jpg) | **11b** — Kali Linux IP (192.168.57.11) added to trusted IP ranges — allows Kali to deliver emails through the server without authentication |
| ![11c](11b_hMailServer_TCPIP_ports.jpg) | **11c** — TCP/IP ports configured: Port 25 (SMTP), Port 110 (POP3), Port 143 (IMAP), Port 587 (SMTP) — all listening on 0.0.0.0 |

<br><br>

### 🔥 Step 3 — Firewall Configuration

| Screenshot | Description |
|---|---|
| ![12a](12_WindowsServer_Firewall_Port25_rule_creation.jpg) | **12a** — Windows Defender Firewall inbound rule creation — opening TCP Port 25 to allow SMTP connections from Kali Linux |
| ![12b](12a_WindowsServer_Firewall_Port25_rule_added.jpg) | **12b** — Firewall rule "hMailServer SMTP Port 25" successfully added — visible at the top of Inbound Rules list with Status: Enabled, Action: Allow |

<br><br>

### 🎣 Step 4 — Phishing Email Attack Simulation

| Screenshot | Description |
|---|---|
| ![12c](12b_KaliLinux_swaks_phishing_email_sent.png) | **12c** — `swaks` command executed from Kali Linux — phishing email successfully delivered to victime@lab.local — server responded: `250 Queued` |

<br><br>

### 📬 Step 5 — Email Delivery Confirmation

| Screenshot | Description |
|---|---|
| ![13](13_hMailServer_logs_email_received.jpg) | **13** — Phishing email stored as .EML file in victim mailbox at `C:\Program Files (x86)\hMailServer\Data\lab.local\victime` — confirms successful delivery |

<br><br>

### 🔬 Step 6 — Email Header Forensic Analysis

| Screenshot | Description |
|---|---|
| ![14](14_Email_raw_header_analysis.jpg) | **14** — Raw email header opened in Notepad — showing Return-Path, Received, Date, To, From, Subject, Message-Id, and X-Mailer fields |
| ![15](15_Email_sender_IP_highlighted.jpg) | **15** — Attacker's real IP address `192.168.56.10` identified in the `Received` header field — this is the critical forensic evidence proving the attack origin |

<br><br>

### 🌐 Step 7 — Threat Intelligence Validation

| Screenshot | Description |
|---|---|
| ![16](16_VirusTotal_sender_IP_lookup.jpg) | **16** — VirusTotal lookup of attacker IP `192.168.56.10` — result: 0/91 vendors flagged, tagged as private IP — expected result for a lab environment |

<br><br>

### 🗺️ Step 8 — MITRE ATT&CK Mapping

| Screenshot | Description |
|---|---|
| ![17](17_MITRE_ATTCK_T1566_Phishing.jpg) | **17** — MITRE ATT&CK Technique T1566 (Phishing) page — confirms Tactic: Initial Access, Sub-techniques: T1566.001 to T1566.004 |
| ![18](18_ATT&CK_Navigator_T1566_highlighted.jpg) | **18** — ATT&CK Navigator with T1566 Phishing highlighted in red under Initial Access — visual proof of attack technique mapping |

<br><br>

## 📊 IOC Summary

| IOC Type | Value | Verdict |
|---|---|---|
| IP Address | 192.168.56.10 | Attacker Machine — Kali Linux |
| Email Address | attacker@lab.local | Spoofed Sender Identity |
| Email Address | victime@lab.local | Victim — Target of Attack |
| URL | http://192.168.56.10/reset | Fake Password Reset Link |
| Tool Signature | swaks v20240103.0 | Attack Tool Fingerprint |

<br><br>

## 🧠 MITRE ATT&CK Mapping

| Field | Value |
|---|---|
| Tactic | Initial Access |
| Technique | T1566 — Phishing |
| Sub-technique | T1566.002 — Spearphishing Link |
| Detection | Email header analysis, SMTP logs, X-Mailer signature |
| Mitigation | SPF/DKIM/DMARC enforcement, email gateway filtering, user awareness training |

<br><br>

## 📄 Documentation

| File | Description |
|---|---|
| `Email_Header_Analysis.md` | Line by line breakdown of the phishing email header |
| `IOC_Table.md` | All Indicators of Compromise extracted from the attack |
| `MITRE_Mapping.md` | Full MITRE ATT&CK T1566 technique mapping |
| `SOC_Incident_Report_Priyanka_Rane.docx` | Complete professional SOC incident report |

<br><br>

## 🧠 Skills Demonstrated

`SMTP Configuration` `Email Forensics` `Phishing Detection` `IOC Extraction`
`Email Header Analysis` `Threat Intelligence` `VirusTotal` `MITRE ATT&CK`
`SOC Incident Reporting` `Firewall Configuration` `VirtualBox Lab Setup`
`hMailServer` `swaks` `Windows Server 2022` `Kali Linux`

<br><br>

## 👩‍💻 About the Analyst

**Priyanka Rane**
SOC Analyst L1 | Threat Detection & Incident Response
📧 ranepriyanka567@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/priyanka-rane)
🐙 [GitHub](https://github.com/priyanka-sec)

<br><br>

> *This project follows the exact workflow a SOC Analyst performs during a phishing email investigation in a real Security Operations Centre environment.*

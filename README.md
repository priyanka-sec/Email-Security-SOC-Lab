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

🔗 [LinkedIn]([https://linkedin.com/in/priyanka-rane](https://www.linkedin.com/in/priyanka-rane-606a71257/))

🐙 [GitHub](https://github.com/priyanka-sec)

<br><br>

> *This project follows the exact workflow a SOC Analyst performs during a phishing email investigation in a real Security Operations Centre environment.*

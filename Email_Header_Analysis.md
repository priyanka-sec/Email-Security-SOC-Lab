# Email Header Analysis

The phishing email was located inside the hMailServer mailbox directory:

C:\Program Files (x86)\hMailServer\Data\lab.local\victime\

The `.eml` file was opened using Notepad to analyze the raw email header for forensic evidence.

---

## Raw Email Header (Important Fields)

| Header Field | Value | SOC Analysis |
|---|---|---|
| Return-Path | attacker@lab.local | Spoofed sender identity |
| Received | from kali [192.168.56.10] | **Real attacker IP identified** |
| Received By | 192.168.56.110 ESMTP | Victim mail server |
| Date | 06 May 2026 19:49:46 IST | Exact attack timestamp |
| To | victime@lab.local | Target user |
| From | attacker@lab.local | Fake trusted sender |
| Subject | Urgent: Reset Your Password | Social engineering tactic |
| X-Mailer | swaks | Attacker tool fingerprint |

---

## Key Finding

The `Received` header field revealed the true origin IP address of the attacker machine, proving that email headers cannot be spoofed completely and always contain forensic evidence for SOC investigation.

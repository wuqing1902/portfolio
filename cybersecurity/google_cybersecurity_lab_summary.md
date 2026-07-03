# Cybersecurity Lab Summary – 17 Labs

**Total Labs:** 17  
**Primary Focus:** Incident Response, Network Security, SIEM, NIST CSF, Python Automation

---


## How to Use This Document

This summary provides a high-level overview of each lab for quick reference. For detailed lab reports, including commands, code, and full analysis, navigate to `lab.md` within this folder.

Each lab entry includes:
- Focus area and primary framework/tools
- Key security skills demonstrated
- Real-world scenario simulated

---

## Lab Summaries

### Lab 1: Internal IT Audit Documentation – Botium Toys
- **Framework:** NIST CSF
- **Skills:** Risk scoring, gap analysis, compliance mapping (PCI DSS, GDPR, SOC)
- **Scenario:** Audited a toy company's security posture, identified missing controls, recommended fixes

### Lab 2: Analyze Network Layer Communication
- **Tools:** tcpdump
- **Skills:** DNS/ICMP analysis, root cause investigation
- **Scenario:** Users couldn't access website — identified UDP port 53 unreachable

### Lab 3: Network Attack Analysis (SYN Flood – Wireshark)
- **Tools:** Wireshark
- **Skills:** TCP handshake analysis, DoS pattern recognition, mitigation strategies
- **Scenario:** Travel agency website down — identified SYN flood attack

### Lab 4: OS Hardening – Web Server Attack Investigation
- **Tools:** tcpdump
- **Skills:** Brute force detection, 2FA recommendation, incident documentation
- **Scenario:** Former employee brute-forced admin account, planted malware

### Lab 5: NIST CSF Incident Report Analysis
- **Framework:** NIST CSF (Identify, Protect, Detect, Respond, Recover)
- **Skills:** DDoS (ICMP flood) analysis, response planning, recovery strategy
- **Scenario:** Multimedia company hit by ICMP flood — applied CSF to manage incident

### Lab 6: Network Hardening – Security Risk Assessment
- **Skills:** Vulnerability assessment, MFA implementation, firewall hardening
- **Scenario:** Social media data breach — recommended MFA, password policies, firewall rules

### Lab 7: Databases & SQL Security Analysis
- **Tools:** MariaDB SQL
- **Skills:** SELECT, WHERE, JOIN, filtering login attempts
- **Scenario:** Investigated employee devices and login anomalies using SQL queries

### Lab 8: Linux Commands in Bash Shell
- **Tools:** Bash, grep, chmod, useradd, man
- **Skills:** File navigation, permission management, user administration
- **Scenario:** Navigated logs, managed users, filtered security events

### Lab 9: Introduction to Asset Security
- **Skills:** Asset inventory, sensitivity classification, risk scoring (Likelihood × Severity)
- **Scenario:** Classified home network assets + bank operational risk assessment

### Lab 10: Protect Organizational Assets
- **Tools:** OpenSSL, sha256sum, cmp
- **Skills:** Decryption (Caesar, AES-256), hashing, RBAC, MFA, account lifecycle
- **Scenario:** Data leak investigation + decryption challenges + access control improvement

### Lab 11: Threats to Asset Security
- **Frameworks:** PASTA threat modeling
- **Skills:** Phishing email analysis, social engineering tactics, attack trees
- **Scenario:** Spear phishing executive + mobile app threat modeling

### Lab 12: USB Drive Attack Vectors
- **Attack Type:** USB baiting / drop attack
- **Skills:** Attacker mindset, physical security, social engineering
- **Scenario:** Found USB with HR data — analyzed exploitation paths

### Lab 13: Incident Investigation & Response
- **Tools:** VirusTotal, MITRE ATT&CK, Pyramid of Pain
- **Skills:** IoC identification, phishing playbook, escalation, post-incident review
- **Scenario:** Malicious file hash investigation + phishing alert + data breach report

### Lab 14: Network Monitoring & Analysis
- **Tools:** Wireshark, tcpdump
- **Skills:** Packet capture, BPF filters, tool comparison (GUI vs CLI)
- **Scenario:** Captured live HTTP traffic + analyzed existing PCAP

### Lab 15: IDS & SIEM Tools
- **Tools:** Suricata, Splunk, Wazuh, Chronicle, jq
- **Skills:** Custom IDS rules, SPL queries, JSON parsing, cloud SIEM
- **Scenario:** Wrote Suricata rules + queried Splunk/Wazuh/Chronicle for threats

### Lab 16: Automate Cybersecurity Tasks with Python
- **Tools:** Python 3, re (regex), file I/O
- **Skills:** Functions, conditionals, loops, log parsing, allow-list management
- **Scenario:** Built scripts to update allow lists, analyze failed logins, parse web logs

### Lab 17: Put It to Work – Prepare for Cybersecurity Jobs
- **Skills:** Log analysis, professional organizations (ISACA, ISC2, SANS), TCREI prompting
- **Scenario:** SOC log analysis + career planning + AI-generated security awareness guide

---

## Skills Matrix

| Skill Area | Labs |
|------------|------|
| NIST CSF | 1, 5 |
| Network Analysis | 2, 3, 14, 15 |
| SIEM | 15, 17 |
| Python Automation | 16 |
| Linux/Bash | 8 |
| SQL | 7 |
| Incident Response | 4, 13, 17 |
| Risk Assessment | 1, 6, 9, 11 |
| Asset Security | 9, 10, 11 |
| Threat Modeling | 11, 12 |
| Cryptography/Hashing | 10 |
| Professional Development | 17 |

---

## Tools & Technologies Summary

| Category | Specific Tools |
|----------|----------------|
| Packet Analysis | Wireshark, tcpdump |
| IDS/IPS | Suricata |
| SIEM | Splunk, Wazuh, Google Chronicle |
| Operating System | Linux (Bash) |
| Database | MariaDB (SQL) |
| Programming | Python 3 |
| Security Frameworks | NIST CSF, MITRE ATT&CK, PASTA |
| Utilities | jq, OpenSSL, sha256sum, grep |

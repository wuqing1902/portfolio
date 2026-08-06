# Cybersecurity Lab Summary – 17 Labs

**Total Labs:** 17  
**Primary Focus:** Incident Response, Network Security, SIEM, NIST CSF, Python Automation

<br><br><br>

## About This Lab Collection

This repository contains 17 cybersecurity labs completed as part of a structured hands-on training program. Each lab simulates real-world scenarios — from internal audits and network attacks to SIEM investigations and Python automation. This is one component of a broader cybersecurity portfolio.

<br><br><br>

**Key skills demonstrated:**

- Network traffic analysis (Wireshark, tcpdump)
- Incident response and threat hunting
- SIEM querying (Splunk, Wazuh, Chronicle)
- NIST CSF and risk assessment frameworks
- Python scripting for security automation
- IDS rule writing (Suricata)
- Asset classification and access control

<br><br><br>

## Tools and Technologies

| Category | Tools |
|----------|-------|
| Network Analysis | Wireshark, tcpdump, Suricata |
| IDS/IPS | Suricata |
| SIEM | Splunk, Wazuh, Google Chronicle |
| Operating Systems | Linux (Bash), Windows |
| Database | MariaDB (SQL) |
| Programming | Python 3 |
| Security Frameworks | NIST CSF, MITRE ATT&CK, PASTA, Pyramid of Pain |
| Utilities | jq, OpenSSL, sha256sum, grep |
| Security Concepts | Least Privilege, MFA, RBAC, Encryption, Hashing |

<br><br><br>

## Lab Summaries

### [Lab 1: Internal IT Audit Documentation – Botium Toys](/cybersecurity/google/labs/01-internal-it-audit-botium-toys.md)
- **Framework:** NIST CSF
- **Skills:** Risk scoring, gap analysis, compliance mapping (PCI DSS, GDPR, SOC)
- **Scenario:** Audited a toy company's security posture, identified missing controls, recommended fixes

### [Lab 2: Analyze Network Layer Communication](/cybersecurity/google/labs/02-network-layer-communication.md)
- **Tools:** tcpdump
- **Skills:** DNS/ICMP analysis, root cause investigation
- **Scenario:** Users couldn't access website — identified UDP port 53 unreachable

### [Lab 3: Network Attack Analysis (SYN Flood – Wireshark)](/cybersecurity/google/labs/03-syn-flood-analysis.md)
- **Tools:** Wireshark
- **Skills:** TCP handshake analysis, DoS pattern recognition, mitigation strategies
- **Scenario:** Travel agency website down — identified SYN flood attack

### [Lab 4: OS Hardening – Web Server Attack Investigation](/cybersecurity/google/labs/04-os-hardening-web-server-attack.md)
- **Tools:** tcpdump
- **Skills:** Brute force detection, 2FA recommendation, incident documentation
- **Scenario:** Former employee brute-forced admin account, planted malware

### [Lab 5: NIST CSF Incident Report Analysis](/cybersecurity/google/labs/05-nist-csf-incident-report.md)
- **Framework:** NIST CSF (Identify, Protect, Detect, Respond, Recover)
- **Skills:** DDoS (ICMP flood) analysis, response planning, recovery strategy
- **Scenario:** Multimedia company hit by ICMP flood — applied CSF to manage incident

### [Lab 6: Network Hardening – Security Risk Assessment](/cybersecurity/google/labs/06-network-hardening-risk-assessment.md)
- **Skills:** Vulnerability assessment, MFA implementation, firewall hardening
- **Scenario:** Social media data breach — recommended MFA, password policies, firewall rules

### [Lab 7: Databases & SQL Security Analysis](/cybersecurity/google/labs/07-sql-security-analysis.md)
- **Tools:** MariaDB SQL
- **Skills:** SELECT, WHERE, JOIN, filtering login attempts
- **Scenario:** Investigated employee devices and login anomalies using SQL queries

### [Lab 8: Linux Commands in Bash Shell](/cybersecurity/google/labs/08-linux-bash-security.md)
- **Tools:** Bash, grep, chmod, useradd, man
- **Skills:** File navigation, permission management, user administration
- **Scenario:** Navigated logs, managed users, filtered security events

### [Lab 9: Introduction to Asset Security](/cybersecurity/google/labs/09-asset-security.md)
- **Skills:** Asset inventory, sensitivity classification, risk scoring (Likelihood × Severity)
- **Scenario:** Classified home network assets + bank operational risk assessment

### [Lab 10: Protect Organizational Assets](/cybersecurity/google/labs/10-protect-organizational-assets.md)
- **Tools:** OpenSSL, sha256sum, cmp
- **Skills:** Decryption (Caesar, AES-256), hashing, RBAC, MFA, account lifecycle
- **Scenario:** Data leak investigation + decryption challenges + access control improvement

### [Lab 11: Threats to Asset Security](/cybersecurity/google/labs/11-threat-modeling-asset-security.md)
- **Frameworks:** PASTA threat modeling
- **Skills:** Phishing email analysis, social engineering tactics, attack trees
- **Scenario:** Spear phishing executive + mobile app threat modeling

### [Lab 12: USB Drive Attack Vectors](/cybersecurity/google/labs/12-usb-attack-vectors.md)
- **Attack Type:** USB baiting / drop attack
- **Skills:** Attacker mindset, physical security, social engineering
- **Scenario:** Found USB with HR data — analyzed exploitation paths

### [Lab 13: Incident Investigation & Response](/cybersecurity/google/labs/13-incident-investigation-response.md)
- **Tools:** VirusTotal, MITRE ATT&CK, Pyramid of Pain
- **Skills:** IoC identification, phishing playbook, escalation, post-incident review
- **Scenario:** Malicious file hash investigation + phishing alert + data breach report

### [Lab 14: Network Monitoring & Analysis](/cybersecurity/google/labs/14-network-monitoring-analysis.md)
- **Tools:** Wireshark, tcpdump
- **Skills:** Packet capture, BPF filters, tool comparison (GUI vs CLI)
- **Scenario:** Captured live HTTP traffic + analyzed existing PCAP

### [Lab 15: IDS & SIEM Tools](/cybersecurity/google/labs/15-ids-siem-tools.md)
- **Tools:** Suricata, Splunk, Wazuh, Chronicle, jq
- **Skills:** Custom IDS rules, SPL queries, JSON parsing, cloud SIEM
- **Scenario:** Wrote Suricata rules + queried Splunk/Wazuh/Chronicle for threats

### [Lab 16: Automate Cybersecurity Tasks with Python](/cybersecurity/google/labs/16-python-security-automation.md)
- **Tools:** Python 3, re (regex), file I/O
- **Skills:** Functions, conditionals, loops, log parsing, allow-list management
- **Scenario:** Built scripts to update allow lists, analyze failed logins, parse web logs

### [Lab 17: Put It to Work – Prepare for Cybersecurity Jobs](/cybersecurity/google/labs/17-cybersecurity-career-readiness.md)
- **Skills:** Log analysis, professional organizations (ISACA, ISC2, SANS), TCREI prompting
- **Scenario:** SOC log analysis + career planning + AI-generated security awareness guide

<br><br><br>

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

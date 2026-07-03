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
| SIEM | Splunk, Wazuh, Google Chronicle |
| Operating Systems | Linux (Bash), Windows |
| Programming | Python 3, SQL (MariaDB) |
| Frameworks | NIST CSF, MITRE ATT&CK, PASTA, Pyramid of Pain |
| Security Concepts | Least Privilege, MFA, RBAC, Encryption, Hashing |

<br><br><br>


## Table of Contents
- [Lab 1: Internal IT Audit Documentation – Botium Toys](#lab-1-internal-it-audit-documentation--botium-toys)
- [Lab 2: Analyze Network Layer Communication](#lab-2-analyze-network-layer-communication)
- [Lab 3: Network Attack Analysis (Wireshark – SYN Flood)](#lab-3-network-attack-analysis-wireshark--syn-flood)
- [Lab 4: Apply OS Hardening Technique – Web Server Attack Investigation](#lab-4-apply-os-hardening-technique--web-server-attack-investigation)
- [Lab 5: Incident Report Analysis – NIST Cybersecurity Framework (CSF) Application](#lab-5-incident-report-analysis--nist-cybersecurity-framework-csf-application)
- [Lab 6: Network Hardening Analysis – Security Risk Assessment](#lab-6-network-hardening-analysis--security-risk-assessment)
- [Lab 7: Databases and SQL – Security Analysis & Data Investigation](#lab-7-databases-and-sql--security-analysis--data-investigation)
- [Lab 8: Linux Commands in the Bash Shell](#lab-8-linux-commands-in-the-bash-shell)
- [Lab 9: Introduction to Asset Security](#lab-9-introduction-to-asset-security)
- [Lab 10: Protect Organizational Assets](#lab-10-protect-organizational-assets)
- [Lab 11: Threats to Asset Security](#lab-11-threats-to-asset-security)
- [Lab 12: Vulnerabilities in Systems – Identify the Attack Vectors of a USB Drive](#lab-12-vulnerabilities-in-systems--identify-the-attack-vectors-of-a-usb-drive)
- [Lab 13: Incident Investigation and Response](#lab-13-incident-investigation-and-response)
- [Lab 14: Network Monitoring and Analysis](#lab-14-network-monitoring-and-analysis)
- [Lab 15: Network Traffic and Logs using IDS and SIEM Tools](#lab-15-network-traffic-and-logs-using-ids-and-siem-tools)
- [Lab 16: Automate Cybersecurity Tasks with Python](#lab-16-automate-cybersecurity-tasks-with-python)
- [Lab 17: Put It to Work – Prepare for Cybersecurity Jobs](#lab-17-put-it-to-work--prepare-for-cybersecurity-jobs)










<br><br><br><br>

---

<br><br><br><br>





# Lab 1: Internal IT Audit Documentation – Botium Toys 

**Framework aligned:** NIST Cybersecurity Framework (CSF)  
**Skills:** Risk Scoring | Gap Analysis | Compliance Mapping | Control Assessment  

<br><br>

## Objective

Conduct an internal IT audit for Botium Toys to evaluate security posture, identify risks, assess controls, check compliance with regulatory standards, and provide actionable recommendations.

<br><br>

## 1. Scope & Goals

| Area | Description |
|------|-------------|
| **Scope** | Entire security program; all assets, systems, internal processes, controls; compliance with regulatory standards |
| **Goals** | Assess assets & controls → Identify gaps → Recommend fixes → Align with NIST CSF |

<br><br>

## 2. Risk Assessment

### Assets Inventory (Summary)
- Employee endpoints (desktops, laptops, smartphones, remote workstations)
- Internal network (customer, vendor, internal data)
- Storefront systems (on‑site & online inventory)
- Business systems (accounting, DB, telecom, ecommerce, inventory mgmt)
- Internet access, legacy systems, data storage

### Risk Summary
- No asset classification  
- Missing key controls (technical, admin, physical)  
- Unrestricted PII/SPII & cardholder access  
- No encryption, no disaster recovery plan, no intrusion detection system  

### Control Best Practices Considered
- Asset identification & classification  
- Controls to reduce breach likelihood  
- Business impact analysis  
- GDPR, PCI DSS, SOC alignment  

**Risk Score:** 8/10 (High) – High risk of data loss or regulatory penalties without corrective action.

<br><br>

## 3. Control Categories

| Category | Examples | Purpose |
|----------|----------|---------|
| Administrative | Password policy, least privilege, separation of duties | Define responsibilities & policies |
| Technical | Firewall, IDS/IPS, encryption, backups | Prevent/detect/correct incidents |
| Physical | Locks, CCTV, alarms, safes | Limit unauthorized physical access |

**Control Types:** Preventative | Detective | Corrective | Deterrent

<br><br>

## 4. Controls Assessment Checklist

| Status | Control | Explanation |
|--------|---------|-------------|
| Missing | Least Privilege | All employees have excessive access |
| Missing | Disaster Recovery Plans | No continuity plan |
| Missing | Strong Password Policies | Minimal requirements |
| Missing | Separation of Duties | CEO overlaps critical roles |
| Implemented | Firewall | Rules actively enforced |
| Missing | Intrusion Detection System (IDS) | Not deployed |
| Missing | Backups | Critical data not backed up |
| Implemented | Antivirus | Installed & monitored |
| Partial | Manual Monitoring & Legacy Maintenance | Exists but unscheduled |
| Missing | Encryption | No encryption for sensitive data |
| Missing | Password Management System | Not used |
| Implemented | Physical Locks | Offices, storefront, warehouse |
| Implemented | CCTV | Installed & working |
| Implemented | Fire Detection/Prevention | Alarms & sprinklers functional |

<br><br>

## 5. Compliance Checklist

| Standard | Status | Requirement | Gap |
|----------|--------|-------------|-----|
| PCI DSS | Fail | Restrict cardholder data access | All employees have access |
| PCI DSS | Fail | Secure data processing & transmission | No encryption |
| PCI DSS | Fail | Encrypt transactions | Not implemented |
| PCI DSS | Fail | Secure password management | Weak policies + no mgmt system |
| GDPR | Pass | 72‑hour breach notification | Plan exists |
| GDPR | Fail | EU customer data privacy | No encryption |
| GDPR | Fail | Data classification & inventory | Assets listed but unclassified |
| GDPR | Pass | Privacy policies enforced | Enforced among staff |
| SOC 1/2 | Fail | User access policies | No least privilege or separation of duties |
| SOC 1/2 | Fail | Data confidentiality | No encryption |
| SOC 1/2 | Pass | Data integrity | Measures in place |
| SOC 1/2 | Fail | Authorized access only | Unrestricted internal access |

<br><br>

## 6. Recommendations (Prioritized)

### High Priority (Immediate)
- Implement **Least Privilege** & **Separation of Duties**
- Deploy **encryption** for data at rest and in transit
- Create **Disaster Recovery Plan**

### Medium Priority
- Install **IDS** and **Password Management System**
- Enforce **strong password policies**
- Schedule **legacy system monitoring**

### Ongoing
- Maintain physical controls (locks, CCTV, fire safety)
- Classify assets and enforce GDPR/PCI/SOC access rules

> Addressing these gaps will reduce risk, protect sensitive data, and improve security posture.

<br><br>

## 7. Reflection

This audit reinforced a **holistic cybersecurity approach** (administrative + technical + physical). Key learnings:

- Asset identification, risk scoring, and gap analysis  
- Applying compliance frameworks (GDPR, PCI DSS, SOC)  
- Translating findings into actionable recommendations  

**Demonstrates:** Cybersecurity principles, analytical thinking, and business continuity planning.

<br><br>

## 8. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| PII | Personally Identifiable Information |
| SPII | Sensitive PII |
| DRP | Disaster Recovery Plan |
| IDS | Intrusion Detection System |
| NIST CSF | National Institute of Standards and Technology Cybersecurity Framework |






<br><br><br><br>

---

<br><br><br><br>









# Lab 2: Analyze Network Layer Communication 

**Tools Used:** tcpdump  
**Protocols Analyzed:** DNS, ICMP  
**Skills:** Packet Analysis | Protocol Identification | Root Cause Analysis | Incident Investigation  

<br><br>

## Objective

Analyze network traffic using `tcpdump` to identify why users receive a **“destination port unreachable”** error when accessing a website, and determine the root cause of the DNS communication failure.

<br><br>

## 1. Scenario Overview

Users reported inability to access **yummyrecipesforme.com**, receiving the error message **“destination port unreachable.”**

As a cybersecurity analyst, I used `tcpdump` to capture and analyze network traffic while attempting to access the website, focusing on DNS and ICMP communication patterns.

<br><br>

## 2. Captured Traffic Summary

> **Note:** The following is a summarized representation of the captured `tcpdump` logs:

| Timestamp | Source | Destination | Protocol | Message Type |
|-----------|--------|-------------|----------|--------------|
| 13:24:32.192571 | 192.51.100.15:35084 | 203.0.113.2:53 | DNS (UDP) | A? yummyrecipesforme.com |
| 13:24:32.193400 | 203.0.113.2 | 192.51.100.15 | ICMP | UDP port 53 unreachable |
| 13:24:32.194100 | 192.51.100.15:35084 | 203.0.113.2:53 | DNS (UDP) | A? yummyrecipesforme.com (retry) |
| 13:24:32.194130 | 203.0.113.2 | 192.51.100.15 | ICMP | UDP port 53 unreachable |

**Pattern observed:** Each DNS query received an ICMP error instead of a valid DNS response.

<br><br>

## 3. Traffic Analysis Findings

### a. Protocols Identified

| Protocol | Role in Incident |
|----------|------------------|
| **UDP (DNS)** | Used by client to send domain resolution requests on port 53 |
| **ICMP** | Used by server to return error messages when DNS service is unavailable |

### b. Log Analysis Summary
- Client (**192.51.100.15**) sent DNS A‑record queries to DNS server (**203.0.113.2**) on **UDP port 53**
- Each request asked for the IP address of `yummyrecipesforme.com`
- Instead of a DNS reply, the server returned **ICMP “udp port 53 unreachable”** errors
- Multiple retries produced identical failures → issue is **persistent**

### c. Key Observations
- **Port 53** is the standard DNS port
- The DNS server is **responding with ICMP errors** instead of DNS replies
- This indicates the DNS service is **not reachable or not functioning properly**

<br><br>

## 4. Incident Timeline

| Event | Time |
|-------|------|
| Users report website access failure | ~13:20 |
| Traffic capture started | 13:24 |
| First DNS query + ICMP error observed | 13:24:32.192 |
| Repeated failures confirmed | 13:24:32.194 |
| Root cause identified | Post‑analysis |

<br><br>

## 5. Investigation Process

1. Reproduced the error by attempting to access the website
2. Captured live network traffic using `tcpdump`
3. Isolated DNS requests (UDP port 53)
4. Identified ICMP error responses
5. Verified repeated failure pattern
6. Concluded DNS service unavailability

<br><br>

## 6. Root Cause Analysis

### Most Likely Causes:
- **DNS server is down or not running** – Service failure on `203.0.113.2`
- **Firewall blocking port 53** – Network security rule misconfiguration
- **DNS service misconfiguration** – Incorrect listening port or binding

### Less Likely but Possible:
- **Denial of Service (DoS) attack** overwhelming the DNS server

<br><br>

## 7. Conclusion

The issue is caused by a **failure in DNS communication**. The client cannot retrieve the IP address of `yummyrecipesforme.com` because **UDP port 53 on the DNS server is unreachable**. This prevents domain resolution, resulting in users being unable to access the website.

<br><br>

## 8. Recommended Next Steps

| Priority | Action |
|----------|--------|
| Immediate | Verify DNS server service status on `203.0.113.2` |
| Immediate | Check firewall rules for port 53 blocking |
| Short‑term | Restart or reconfigure DNS service |
| Ongoing | Monitor for unusual traffic patterns (potential DoS) |

<br><br>

## 9. Skills Demonstrated

- Network traffic analysis using `tcpdump`
- Understanding of TCP/IP protocols (UDP, ICMP, DNS)
- Log interpretation and incident investigation
- Root cause analysis in cybersecurity incidents
- Technical documentation for troubleshooting

<br><br>

## 10. Reflection

This lab reinforced practical network troubleshooting skills. Key takeaways:

- How DNS resolution fails when port 53 is unreachable
- The role of ICMP in delivering network error messages
- Using packet analysis to isolate root cause without relying on application‑level logs

**Demonstrates:** Network analysis, protocol behavior understanding, and systematic incident investigation.

<br><br>

## 11. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| DNS | Domain Name System – translates domain names to IP addresses |
| ICMP | Internet Control Message Protocol – used for error reporting |
| UDP | User Datagram Protocol – connectionless transport protocol |
| A record | DNS record that maps a domain to an IPv4 address |
| Port 53 | Standard port for DNS traffic |
| tcpdump | Command‑line packet analyzer |






<br><br><br><br>

---

<br><br><br><br>













# Lab 3: Network Attack Analysis (Wireshark – SYN Flood)

**Tools Used:** Wireshark  
**Attack Type Analyzed:** SYN Flood (Denial of Service)  
**Skills:** Packet Analysis | Attack Pattern Recognition | TCP Handshake | Incident Response | Mitigation Strategies  

<br><br>

## Objective

Analyze a cybersecurity incident involving a travel agency's website that experienced connection timeouts. Using Wireshark logs, identify the type of network attack, examine its impact, and explain how it disrupted the web server's functionality.

<br><br>

## 1. Scenario Overview

A travel agency's website experienced connection timeouts, preventing employees and customers from accessing its sales pages. Automated alerts indicated a problem with the web server. A packet sniffer captured network traffic revealing a large number of TCP SYN requests from an unfamiliar IP address, overwhelming the web server.

<br><br>

## 2. Wireshark Log Analysis (TCP/HTTP)

| No. | Time | Source | Destination | Protocol | Info | Status |
|-----|------|--------|-------------|----------|------|--------|
| 47 | 3.144521 | 198.51.100.23 | 192.0.2.1 | TCP | 42584->443 [SYN] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 48 | 3.195755 | 192.0.2.1 | 198.51.100.23 | TCP | 443->42584 [SYN, ACK] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 49 | 3.246989 | 198.51.100.23 | 192.0.2.1 | TCP | 42584->443 [ACK] Seq=1 Win=5792 Len=120 | 🟢 Normal |
| 50 | 3.298223 | 198.51.100.23 | 192.0.2.1 | HTTP | GET /sales.html HTTP/1.1 | 🟢 Normal |
| 51 | 3.349457 | 192.0.2.1 | 198.51.100.23 | HTTP | HTTP/1.1 200 OK (text/html) | 🟢 Normal |
| 52 | 3.390692 | 203.0.113.0 | 192.0.2.1 | TCP | 54770->443 [SYN] Seq=0 Win=5792 Len=0 | 🔴 Attack |
| 53 | 3.441926 | 192.0.2.1 | 203.0.113.0 | TCP | 443->54770 [SYN, ACK] Seq=0 Win=5792 Len=120 | 🔴 Attack |
| 54 | 3.493160 | 203.0.113.0 | 192.0.2.1 | TCP | 54770->443 [ACK] Seq=1 Win=5792 Len=0 | 🔴 Attack |
| 55 | 3.544394 | 198.51.100.14 | 192.0.2.1 | TCP | 14785->443 [SYN] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 56 | 3.599628 | 192.0.2.1 | 198.51.100.14 | TCP | 443->14785 [SYN, ACK] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 77 | 7.330577 | 192.0.2.1 | 198.51.100.5 | HTTP | HTTP/1.1 504 Gateway Time-out (text/html) | 🟡 Timeout/Error |

**Status Legend:** 🟢 Normal | 🔴 Attack Traffic | 🟡 Error/Timeout

<br><br>

## 3. Normal vs. Attack Traffic Analysis

### Normal TCP/HTTP Communication

A normal connection between a legitimate user and the web server follows the **TCP three-way handshake**:

| Step | Direction | Packet Type | Purpose |
|------|-----------|-------------|---------|
| 1 | Client → Server | SYN | Requests connection |
| 2 | Server → Client | SYN-ACK | Acknowledges and reserves resources |
| 3 | Client → Server | ACK | Confirms connection established |

After handshake completion, HTTP traffic flows normally:
- **GET request** from client for specific webpage
- **200 OK response** from server with requested content

### Indicators of the Attack

The Wireshark log reveals several abnormal patterns:

| Indicator | Evidence from Logs |
|-----------|---------------------|
| Repeated SYN packets | Multiple SYN entries from attacker IP `203.0.113.0` |
| Single attacking source | Only one unfamiliar IP address generating SYN traffic |
| Resource exhaustion | Legitimate traffic (e.g., `198.51.100.14`) initially processed but later fails |
| Timeout errors | HTTP `504 Gateway Time-out` appears after attack intensifies |

<br><br>

## 4. Attack Identification

### Attack Type: **SYN Flood (Denial of Service - DoS)**

**Classification:** Layer 4 (Transport Layer) Denial of Service Attack

### Evidence Supporting Identification:

| Evidence | Explanation |
|----------|-------------|
| Single attacking IP | `203.0.113.0` sending repeated SYN packets |
| Incomplete handshakes | Attacker never completes the three-way handshake properly |
| Resource exhaustion | Server becomes unable to respond to legitimate SYN requests |
| Timeout errors | Employees receive `504 Gateway Time-out` instead of web content |

<br><br>

## 5. Attack Mechanism Explained

### How SYN Flood Works:

| Step | Action |
|------|--------|
| Step 1: | Attacker sends massive volume of SYN packets (spoofed or real) |
| Step 2: | Server responds with SYN-ACK and reserves resources for each connection |
| Step 3: | Attacker never sends final ACK, leaving connections "half-open" |
| Step 4: | Server's connection queue fills up |
| Step 5: | Legitimate SYN requests are dropped or timeout |

### Impact on the Travel Agency Website:

| Impact | Description |
|--------|-------------|
| Service unavailability | Employees cannot access sales webpage |
| Connection timeouts | Browsers display timeout errors |
| Resource exhaustion | Web server CPU/memory consumed by half-open connections |
| Business disruption | No online vacation package sales during attack |

<br><br>

## 6. Incident Timeline

| Time | Event |
|------|-------|
| Afternoon | Automated alerts trigger |
| T+0 min | Employees report connection timeouts |
| T+5 min | Packet capture initiated |
| T+10 min | SYN flood pattern identified |
| T+15 min | Attack confirmed as DoS (SYN Flood) |
| Post-incident | Mitigation strategies recommended |

<br><br>

## 7. Consequences of the Attack

| Category | Consequence |
|----------|-------------|
| **Business** | Disrupted operations – website inaccessible |
| **Customer** | Negative user experience – cannot book vacations |
| **Financial** | Potential revenue loss during downtime |
| **Reputational** | Customers may lose trust in travel agency |
| **Technical** | Web server resources exhausted |

<br><br>

## 8. Mitigation Strategies

### Immediate Response (During Attack)

| Action | Purpose |
|--------|---------|
| Block attacking IP (`203.0.113.0`) at firewall | Stop malicious traffic source |
| Enable SYN cookies | Handle TCP handshake without exhausting resources |
| Increase backlog queue size | Allow more pending connections |

### Long-term Prevention

| Strategy | Implementation |
|----------|----------------|
| **Rate limiting** | Limit SYN packets per second from single IP |
| **Firewall rules** | Detect and block anomalous SYN patterns |
| **SYN cookies** | Permanently enable on web servers |
| **DDoS protection** | Deploy cloud-based DDoS mitigation service |
| **Monitoring** | Set alerts for sudden SYN traffic spikes |

<br><br>

## 9. Comparison: Normal vs. Attack Traffic

| Characteristic | Normal Traffic | SYN Flood Attack |
|----------------|----------------|------------------|
| SYN packet frequency | Low, sporadic | High, continuous |
| Source IP diversity | Many legitimate users | Single or few IPs |
| Handshake completion | 100% complete | Incomplete (no final ACK) |
| Server response | 200 OK | 504 Timeout |
| Connection queue | Manageable | Exhausted |

<br><br>

## 10. Skills Demonstrated

- Network traffic analysis using Wireshark
- TCP handshake and protocol behavior understanding
- Attack pattern recognition (SYN flood)
- Incident investigation and root cause analysis
- Mitigation strategy development
- Technical documentation for security incidents

<br><br>

## 11. Reflection

This lab provided hands-on experience analyzing a real-world DoS attack scenario. Key takeaways:

- How SYN flood attacks exploit the TCP three-way handshake
- Recognizing attack patterns in packet capture logs
- The cascading impact of resource exhaustion on legitimate users
- Practical mitigation techniques (SYN cookies, rate limiting, IP blocking)

**Demonstrates:** Network security analysis, attack identification, and defensive strategy formulation.

<br><br>

## 12. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| SYN | Synchronize packet – initiates TCP connection |
| SYN-ACK | Synchronize-Acknowledge packet – server response |
| ACK | Acknowledge packet – completes handshake |
| SYN Flood | DoS attack exhausting server connection queue |
| Half-open connection | Connection awaiting final ACK |
| 504 Gateway Time-out | Server upstream timeout error |
| SYN cookies | Technique to handle SYN flood without resource exhaustion |
| DoS | Denial of Service – attack disrupting availability |










<br><br><br><br>

---

<br><br><br><br>














# Lab 4: Apply OS Hardening Technique – Web Server Attack Investigation

**Tools Used:** tcpdump  
**Attack Type Analyzed:** Brute Force Attack (Admin Account Compromise)  
**Protocols Analyzed:** HTTP, DNS  
**Skills:** Protocol Analysis | Incident Documentation | Root Cause Analysis | OS Hardening | 2FA Implementation  

<br><br>

## Objective

Investigate a security incident for **yummyrecipesforme.com** where visitors were redirected to a malicious website after downloading a disguised executable file. The objectives are to:

1. Identify the network protocols involved in the incident
2. Document the incident in detail with evidence
3. Recommend security measures to prevent future attacks

<br><br>

## 1. Scenario Overview

A former employee executed a **brute force attack** to gain administrative access to `yummyrecipesforme.com`, then modified the website to distribute malware. Visitors were prompted to download an executable file (disguised as a free recipe offer), which caused system slowdowns and redirected browsers to **greatrecipesforme.com** (a malicious website).

<br><br>

## 2. Network Protocol Identification

### Primary Protocols Involved

| Protocol | Role in Incident |
|----------|------------------|
| **HTTP (Port 80)** | Delivered malicious executable file and redirected traffic |
| **DNS (Port 53)** | Resolved domain names to IP addresses for both legitimate and malicious sites |

### Captured tcpdump Logs

| Timestamp | Source | Destination | Protocol | Message Type |
|-----------|--------|-------------|----------|---------------|
| 12:34:56 | 192.168.1.2:54321 | 8.8.8.8:53 | DNS | Query A: yummyrecipesforme.com |
| 12:34:56 | 8.8.8.8:53 | 192.168.1.2:54321 | DNS | Response A: 93.184.216.34 |
| 12:34:57 | 192.168.1.2:54322 | 93.184.216.34:80 | HTTP | GET /index.html |
| 12:34:58 | 93.184.216.34:80 | 192.168.1.2:54322 | HTTP | 200 OK (malicious file download) |
| 12:35:02 | 192.168.1.2:54323 | 8.8.8.8:53 | DNS | Query A: greatrecipesforme.com |
| 12:35:02 | 8.8.8.8:53 | 192.168.1.2:54323 | DNS | Response A: 203.0.113.45 |
| 12:35:03 | 192.168.1.2:54324 | 203.0.113.45:80 | HTTP | GET /index.html |

### Traffic Analysis Summary

| Step | Action | Implication |
|------|--------|-------------|
| 1 | Browser queries DNS for `yummyrecipesforme.com` | Normal domain resolution |
| 2 | HTTP request to legitimate website | User attempts to access content |
| 3 | Server responds with malicious file download | Website compromised |
| 4 | After execution, DNS query for `greatrecipesforme.com` | Malware triggers redirection |
| 5 | HTTP connection to malicious site | User redirected to attacker-controlled server |

<br><br>

## 3. Incident Documentation

### Incident Summary

| Aspect | Details |
|--------|---------|
| **What happened** | Visitors to `yummyrecipesforme.com` prompted to download executable file; after execution, browsers redirected to `greatrecipesforme.com` |
| **Impact** | User computers slowed down; website integrity compromised; admin locked out |
| **Attacker** | Former employee |
| **Attack method** | Brute force attack on administrative account |

### Investigation Steps

| Step | Action Taken |
|------|---------------|
| 1 | Created sandbox environment for safe analysis |
| 2 | Ran `tcpdump` to capture network traffic while visiting website |
| 3 | Downloaded and executed suspicious file in sandbox |
| 4 | Confirmed malicious redirection pattern |
| 5 | Analyzed DNS and HTTP logs |
| 6 | Inspected website source code (found malicious JavaScript) |

### Findings

| Finding | Details |
|---------|---------|
| **Root cause** | Brute force attack on admin account succeeded due to default password and no login attempt limits |
| **Malicious modification** | Embedded JavaScript prompted file downloads and enabled redirection |
| **Compromised assets** | Web server integrity; end-user computers |

### Sources of Evidence

- TCP/IP traffic captured via `tcpdump`
- Website source code analysis
- Customer reports
- Hosting provider feedback

<br><br>

## 4. Attack Timeline

| Time | Event |
|------|-------|
| Prior to incident | Former employee executes brute force attack |
| Attack success | Attacker gains admin access using default password |
| Post-compromise | Malicious JavaScript embedded in website |
| Customer visit | Users prompted to download executable file |
| Post-execution | Browsers redirected to `greatrecipesforme.com` |
| Detection | Website owner locked out; customers report issues |

<br><br>

## 5. Root Cause Analysis

### Primary Root Cause

| Cause | Explanation |
|-------|-------------|
| **No 2FA (Two-Factor Authentication)** | Only password required for admin access |
| **Default/weak password** | Attacker guessed or brute-forced easily |
| **No login attempt limits** | Unlimited brute force attempts possible |

### Contributing Factors

- Lack of account lockout policy
- No administrative access monitoring
- Missing web application firewall (WAF)

<br><br>

## 6. Recommended Security Measures

### Primary Recommendation: **Two-Factor Authentication (2FA)**

| Aspect | Description |
|--------|-------------|
| **What** | Require OTP (one-time passcode) via phone/email in addition to password |
| **Why** | Even if password compromised, attacker cannot access account without OTP |
| **Impact** | Prevents brute force and credential stuffing attacks |

### Supporting Recommendations

| Priority | Measure | Purpose |
|----------|---------|---------|
| High | Enforce strong, non-default passwords | Eliminate guessable credentials |
| High | Limit login attempts (e.g., 5 attempts then lockout) | Prevent brute force |
| Medium | Require regular password updates (e.g., 90 days) | Reduce credential lifetime |
| Medium | Implement account monitoring and alerting | Detect unauthorized access |
| Low | Deploy Web Application Firewall (WAF) | Block malicious requests |

<br><br>

## 7. Prevention Checklist

| Control | Status (Post-Implementation) | Description |
|---------|------------------------------|-------------|
| 2FA Enabled | Recommended | Admin accounts require OTP |
| Strong Password Policy | Recommended | Minimum length, complexity requirements |
| Login Attempt Limits | Recommended | 5 failed attempts = 15-min lockout |
| Account Monitoring | Recommended | Alerts for unusual admin logins |
| WAF | Optional | Additional defense layer |

<br><br>

## 8. Skills Demonstrated

- Network protocol analysis (HTTP, DNS) using `tcpdump`
- Incident documentation and evidence collection
- Root cause analysis of web server compromise
- Security control recommendation (2FA, password policy)
- Understanding of brute force attack vectors
- OS hardening principles for web servers

<br><br>

## 9. Reflection

This lab reinforced the critical relationship between **network analysis**, **incident response**, and **preventive security controls**. Key takeaways:

- How HTTP and DNS logs reveal attacker behavior patterns
- The importance of **2FA** as a defense against credential-based attacks
- Why default passwords and unlimited login attempts create unacceptable risk
- How a single compromised admin account can affect thousands of end users

**Demonstrates:** Protocol analysis, incident documentation, root cause identification, and practical security hardening recommendations.

<br><br>

## 10. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| Brute Force Attack | Repeated login attempts to guess credentials |
| 2FA (Two-Factor Authentication) | Requires two verification methods (password + OTP) |
| OTP | One-time passcode (time-based or SMS/email) |
| HTTP | Hypertext Transfer Protocol – web traffic |
| DNS | Domain Name System – resolves domain names to IPs |
| Sandbox | Isolated environment for safe malware analysis |
| WAF | Web Application Firewall – filters malicious web traffic |










<br><br><br><br>

---

<br><br><br><br>










# Lab 5: Incident Report Analysis – NIST Cybersecurity Framework (CSF) Application

**Framework Applied:** NIST Cybersecurity Framework (CSF) – Identify, Protect, Detect, Respond, Recover  
**Attack Type Analyzed:** DDoS (ICMP Flood)  
**Skills:** Incident Analysis | NIST CSF Application | Response Planning | Recovery Strategy | Monitoring Implementation  

<br><br>

## Objective

Analyze a network security incident using the **NIST Cybersecurity Framework (CSF)**. A multimedia company experienced a DDoS attack caused by an incoming flood of ICMP packets. The objectives are to:

1. Summarize the security event
2. Identify the type of attack and impacted systems
3. Implement protective measures to prevent similar attacks
4. Detect potential security threats using monitoring tools
5. Develop a response plan for future incidents
6. Outline recovery strategies to restore systems and services

<br><br>

## 1. Scenario Overview

A multimedia company experienced a **Distributed Denial of Service (DDoS) attack** caused by an incoming flood of ICMP packets. The attack disrupted internal network services for **two hours**, preventing normal operations. The cybersecurity team responded to contain the incident, restored critical services, and analyzed the vulnerability that enabled the attack.

<br><br>

## 2. Incident Summary

| Aspect | Details |
|--------|---------|
| **Event** | All internal network services suddenly stopped responding |
| **Cause** | DDoS attack via flood of ICMP packets |
| **Impact** | Disruption of all internal network services; critical systems temporarily unavailable |
| **Response** | Incoming ICMP traffic blocked; non-critical services stopped; critical services restored |
| **Duration** | Approximately 2 hours |

<br><br>

## 3. NIST CSF Framework Application

The NIST Cybersecurity Framework consists of **five core functions**. Each function was applied during this incident:

| Function | Description | Application in This Incident |
|----------|-------------|------------------------------|
| **Identify** | Understand assets, risks, and vulnerabilities | Identified attack type, affected systems, and root cause |
| **Protect** | Implement safeguards to limit impact | Configured firewall rules, updated policies |
| **Detect** | Discover incidents in real time | Deployed IDS, network monitoring, IP verification |
| **Respond** | Take action during/after incident | Isolated systems, restored critical services, analyzed logs |
| **Recover** | Restore normal operations | Brought services online, enforced firewall rules, conducted review |

<br><br>

## 4. Identify – Attack and Affected Systems

| Question | Answer |
|----------|--------|
| **Type of Attack** | DDoS attack using ICMP floods (ICMP echo requests/ping floods) |
| **Targeted Systems** | Entire internal network, including critical servers and network resources |
| **Scope** | Network-wide disruption; incoming ICMP traffic exploited unconfigured firewall rules |
| **Threat Actor** | Malicious external actor(s) leveraging unprotected network perimeter |
| **Root Vulnerability** | No rate limiting or filtering on incoming ICMP traffic |

### ICMP Flood Attack Explained

| Step | Description |
|------|-------------|
| 1 | Attacker sends massive volume of ICMP echo requests (pings) to target network |
| 2 | Server attempts to respond to each request with ICMP echo replies |
| 3 | Network bandwidth and server resources become exhausted |
| 4 | Legitimate traffic cannot be processed → denial of service |

<br><br>

## 5. Protect – Security Measures Implemented

| Priority | Measure | Purpose |
|----------|---------|---------|
| High | Firewall rule to rate-limit incoming ICMP packets | Prevent flood from consuming bandwidth |
| High | Configure IDS/IPS to filter suspicious ICMP traffic | Block malformed or excessive ICMP packets |
| Medium | Update network security policies | Enforce stricter control on incoming traffic |
| Ongoing | Continuous staff awareness training | Enable security team to recognize unusual traffic patterns |

### Firewall Rule Example (Conceptual)
| Field | Value |
|-------|-------|
| Rule: | Rate Limit ICMP |
| Condition: | Protocol = ICMP AND Direction = Inbound |
| Action: | Limit to 10 packets/second per source IP |
| Log: | Yes |

<br><br>

## 6. Detect – Monitoring Methods

| Method | Implementation | Detection Capability |
|--------|----------------|----------------------|
| **Source IP Verification** | Firewall checks for spoofed IP addresses | Prevents reflection attacks |
| **Network Monitoring Software** | Real-time traffic analysis dashboard | Alerts on abnormal traffic spikes |
| **Intrusion Detection System (IDS)** | Signature-based + anomaly-based detection | Identifies ICMP flood patterns |

### Detection Indicators

| Indicator | Normal State | Attack State |
|-----------|--------------|--------------|
| ICMP packets per second | < 100 | > 10,000 |
| Source IP diversity | Varied legitimate IPs | Single or spoofed IP range |
| Network latency | < 50ms | > 500ms or timeout |

<br><br>

## 7. Respond – Response Plan for Future Incidents

| Phase | Action | Responsible Party |
|-------|--------|-------------------|
| **Immediate (0-15 min)** | Isolate affected systems to prevent further disruption | Security Team Lead |
| **Short-term (15-60 min)** | Restore critical network resources first | Network Engineer |
| **Investigation (60-120 min)** | Analyze network logs to identify attack patterns | Security Analyst |
| **Reporting (Post-incident)** | Document incident; report to management and legal (if applicable) | Compliance Officer |

### Response Checklist

- [ ] Block attacking IP ranges at firewall
- [ ] Enable rate limiting on ICMP traffic
- [ ] Stop non-critical services to reduce load
- [ ] Restore critical services from backups (if needed)
- [ ] Preserve logs for forensic analysis
- [ ] Notify stakeholders (internal + external if required)

<br><br>

## 8. Recover – Recovery Plan

| Step | Action | Priority |
|------|--------|----------|
| 1 | Restore critical network services first (email, authentication, core apps) | High |
| 2 | Block external ICMP flood attacks at firewall (enforce rate limits) | High |
| 3 | Temporarily stop non-critical services during future attacks | Medium |
| 4 | Conduct post-incident review and implement improvements | Ongoing |

### Post-Incident Review Questions

| Question | Purpose |
|----------|---------|
| What was the root cause? | Identify vulnerability to patch |
| How quickly was the attack detected? | Improve detection capabilities |
| Was the response effective? | Refine response procedures |
| What would we do differently? | Update playbooks and policies |

<br><br>

## 9. Comparison: Before vs. After NIST CSF Implementation

| Aspect | Before Incident | After NIST CSF Application |
|--------|----------------|---------------------------|
| **ICMP traffic rules** | No rate limiting | Rate limit: 10 packets/sec per IP |
| **Monitoring** | Basic uptime monitoring | IDS + real-time traffic analysis |
| **Response plan** | Ad-hoc | Documented, phased response |
| **Recovery time** | ~2 hours | Target: <30 minutes |
| **Staff training** | Minimal | Continuous awareness program |

<br><br>

## 10. Tools and Concepts Used

| Tool/Concept | Application in This Lab |
|--------------|-------------------------|
| Firewall | Rate limiting, IP blocking |
| IDS/IPS | ICMP flood detection and filtering |
| Network Monitoring Software | Real-time traffic anomaly detection |
| DDoS Mitigation Strategies | Rate limiting, source IP verification |
| NIST Cybersecurity Framework | Structured incident management |

<br><br>

## 11. Skills Demonstrated

- Incident analysis using NIST CSF five functions (Identify, Protect, Detect, Respond, Recover)
- Identification of network vulnerabilities (unfiltered ICMP traffic)
- Implementation of security monitoring and detection tools (IDS, network monitoring)
- Development of response and recovery plans
- Professional documentation and reporting of cybersecurity incidents
- DDoS attack pattern recognition (ICMP flood)

<br><br>

## 12. Reflection

This lab reinforced the value of using a **structured framework** like NIST CSF for incident management. Key takeaways:

- How ICMP flood attacks exploit missing rate limiting and filtering
- The importance of **proactive monitoring** (detect before damage escalates)
- Why a **documented response plan** reduces confusion during active attacks
- The relationship between all five CSF functions – they work as an integrated cycle, not siloed steps

**Demonstrates:** Framework-based incident analysis, DDoS mitigation understanding, and comprehensive security program thinking.

<br><br>

## 13. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| NIST CSF | National Institute of Standards and Technology Cybersecurity Framework |
| DDoS | Distributed Denial of Service – attack from multiple sources |
| ICMP | Internet Control Message Protocol – used for ping and error reporting |
| ICMP Flood | DDoS attack sending excessive ICMP echo requests |
| IDS | Intrusion Detection System – monitors for malicious activity |
| IPS | Intrusion Prevention System – blocks detected threats |
| Rate Limiting | Restricting traffic volume per source |
| Spoofed IP | Falsified source IP address |

<br><br>

## 14. NIST CSF Quick Reference

| Function | Core Question |
|----------|---------------|
| **Identify** | What assets and risks exist? |
| **Protect** | How do we safeguard assets? |
| **Detect** | How do we find incidents quickly? |
| **Respond** | What actions do we take? |
| **Recover** | How do we restore operations? |









<br><br><br><br>

---

<br><br><br><br>










# Lab 6: Network Hardening Analysis – Security Risk Assessment

**Focus Area:** Network Hardening | Vulnerability Assessment  
**Attack Type Analyzed:** Data Breach (Credential Compromise)  
**Skills:** Vulnerability Identification | Risk Assessment | MFA Implementation | Firewall Hardening | Password Policy Enforcement  

<br><br>

## Objective

Assess network vulnerabilities and apply network hardening techniques to secure a social media organization's network following a data breach that compromised user names and addresses. The objectives are to:

1. Identify key network vulnerabilities
2. Select appropriate network hardening tools and methods
3. Explain the effectiveness of chosen hardening practices
4. Document recommendations for network security improvements

<br><br>

## 1. Scenario Overview

A social media organization recently experienced a **data breach** that compromised personal information, including user names and addresses. As a cybersecurity analyst, I identified vulnerabilities and recommended security hardening practices to reduce the likelihood of future attacks.

**Industry Context:** Social media platforms are high-value targets due to large volumes of PII (Personally Identifiable Information).

<br><br>

## 2. Incident Summary

| Aspect | Details |
|--------|---------|
| **Event** | Data breach compromising user names and addresses |
| **Impact** | Unauthorized access to PII; reputational damage; potential regulatory penalties |
| **Root Cause** | Weak authentication practices and insufficient network controls |
| **Response** | Vulnerability assessment conducted; hardening recommendations developed |

<br><br>

## 3. Identified Vulnerabilities

| # | Vulnerability | Risk Level | Potential Consequence |
|---|---------------|------------|----------------------|
| 1 | Employees share passwords | 🔴 High | Unauthorized access; no individual accountability |
| 2 | Database administrator account uses default credentials | 🔴 Critical | Complete database compromise |
| 3 | Firewalls lack rules to filter inbound/outbound traffic | 🔴 High | Unrestricted malicious traffic |
| 4 | Multifactor authentication (MFA) not implemented | 🟠 Medium-High | Single point of failure (password only) |

### Vulnerability Deep Dive

| Vulnerability | Why It Exists | Attack Vector |
|---------------|---------------|---------------|
| Password sharing | No policy enforcement; convenience over security | Insider threat; credential leakage |
| Default admin credentials | Poor initial configuration; never changed | Brute force; credential stuffing |
| No firewall rules | Unconfigured or misconfigured firewall | DoS, DDoS, unauthorized access |
| No MFA | Cost/perception barriers; lack of awareness | Phishing; credential theft |

> **If left unaddressed**, these vulnerabilities could lead to repeated data breaches and unauthorized network access.

<br><br>

## 4. Recommended Network Hardening Tools and Methods

### Primary Recommendations

| Priority | Tool/Method | Purpose | Implementation Timeline |
|----------|-------------|---------|------------------------|
| **Critical** | Change default database admin credentials | Eliminate easy attack vector | Immediate (Day 1) |
| **High** | Multi-Factor Authentication (MFA) | Add second authentication layer | Week 1 |
| **High** | Firewall rule configuration | Filter inbound/outbound traffic | Week 1 |
| **Medium** | Strong password policies | Enforce credential hygiene | Week 2 |
| **Ongoing** | Employee security training | Reduce password sharing | Monthly |

<br><br>

### 4.1 Multi-Factor Authentication (MFA)

| Aspect | Description |
|--------|-------------|
| **What it is** | Requires two or more verification factors: password + something you have (phone, token) or something you are (biometric) |
| **How it works** | User enters password → receives OTP via SMS/app → enters OTP to complete login |
| **Why effective** | Even if password is shared or stolen, attacker cannot access without second factor |
| **Password sharing impact** | Makes single-password access insufficient – sharing becomes useless |

**MFA Factor Types:**

| Factor Type | Examples |
|-------------|----------|
| Knowledge (something you know) | Password, PIN |
| Possession (something you have) | Smartphone, hardware token, smart card |
| Inherence (something you are) | Fingerprint, facial recognition, retina scan |

<br><br>

### 4.2 Strong Password Policies

| Policy Element | Recommendation | Purpose |
|----------------|----------------|---------|
| Minimum length | 12-16 characters | Increase brute force difficulty |
| Complexity | Uppercase + lowercase + numbers + symbols | Expand password space |
| Password rotation | Every 90 days | Limit credential lifetime |
| Reuse prevention | Remember last 10 passwords | Prevent cyclic password reuse |
| Account lockout | Lock after 5 failed attempts (15 min) | Prevent brute force |
| Password sharing | Explicitly prohibited in policy | Reduce insider risk |

<br><br>

### 4.3 Firewall Maintenance

| Activity | Frequency | Purpose |
|----------|-----------|---------|
| Rule review | Monthly | Remove outdated/unused rules |
| Traffic logging | Continuous | Detect suspicious patterns |
| Blocklist update | Weekly | Block known malicious IPs |
| Rule testing | Quarterly | Verify effectiveness |

**Firewall Rule Examples:**
| Rule | Explaination | Condition | Action |
|------|--------------|-----------|--------|
| Inbound Rule | Block unauthorized inbound | Source IP NOT in (trusted list) AND Destination = internal network | DENY |
| Outbound Rule | Prevent data exfiltration | Destination = known malicious IP | DENY + ALERT |
| ICMP Rule (prevents DoS) | Protocol = ICMP AND Packet Rate > 100/sec | RATE LIMIT to 10/sec |

<br><br>

## 5. Effectiveness of Recommendations

| Recommendation | Attack Mitigated | Effectiveness Rating | Explanation |
|----------------|------------------|---------------------|-------------|
| **MFA** | Credential theft, password sharing, brute force | ⭐⭐⭐⭐⭐ | Second factor stops 99.9% of account compromise attacks |
| **Strong password policies** | Brute force, dictionary attacks | ⭐⭐⭐⭐ | Increases time/cost for attackers |
| **Firewall rules** | DoS, DDoS, unauthorized access | ⭐⭐⭐⭐ | Controls traffic at perimeter |
| **Default credential change** | Immediate compromise | ⭐⭐⭐⭐⭐ | Eliminates known vulnerability |

### Why MFA is the Most Effective Control

| Benefit | Impact |
|---------|--------|
| Stops 99.9% of account hacks (Microsoft data) | Dramatically reduces breach risk |
| Makes shared passwords ineffective | Changes employee behavior |
| Protects against phishing | Attacker needs more than credentials |
| Low user friction (modern implementations) | High adoption rate |

<br><br>

## 6. Implementation Roadmap

| Phase | Timeline | Actions | Success Metric |
|-------|----------|---------|----------------|
| **Phase 1: Immediate** | Days 1-3 | Change default admin credentials; block suspicious IPs | Default creds removed |
| **Phase 2: Short-term** | Weeks 1-2 | Deploy MFA; configure firewall rules | 100% admin accounts on MFA |
| **Phase 3: Medium-term** | Weeks 3-4 | Enforce password policies; employee training | Password policy compliance >95% |
| **Phase 4: Ongoing** | Monthly/Quarterly | Rule reviews; vulnerability scans; refresher training | No high-risk findings |

<br><br>

## 7. Comparison: Before vs. After Hardening

| Security Aspect | Before Hardening | After Hardening |
|----------------|------------------|-----------------|
| **Admin authentication** | Default credentials only | MFA + strong password |
| **User authentication** | Single password (shared) | MFA + unique password |
| **Firewall** | No filtering rules | Inbound/outbound filtering + rate limiting |
| **Password policy** | None | 12 chars + complexity + rotation |
| **Breach risk** | High | Low-Medium |

<br><br>

## 8. Skills Demonstrated

- Vulnerability assessment and analysis
- Knowledge of network hardening tools and methods (MFA, firewalls, password policies)
- Security risk assessment reporting
- Practical recommendations for mitigating network threats
- Documentation and explanation of cybersecurity measures
- Implementation roadmap development

<br><br>

## 9. Tools and Concepts Used

| Tool/Concept | Application |
|--------------|-------------|
| Multi-Factor Authentication (MFA) | Prevent unauthorized access via credential theft |
| Password Policies | Enforce credential strength and rotation |
| Firewall Rules | Filter inbound/outbound malicious traffic |
| Network Vulnerability Assessment | Identify security gaps |
| Security Policy Documentation | Formalize hardening requirements |

<br><br>

## 10. Reflection

This lab reinforced the importance of **defense in depth** and **proactive network hardening**. Key takeaways:

- Default credentials are one of the most common and dangerous vulnerabilities
- MFA is the single most effective control against credential-based attacks
- Firewalls without configured rules provide no protection
- Password sharing is a cultural/behavioral issue, not just technical – requires policy + training
- Hardening is not one-time; requires ongoing maintenance and review

**Demonstrates:** Risk assessment methodology, security control selection, and practical network hardening implementation.

<br><br>

## 11. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| MFA | Multi-Factor Authentication – requires two or more verification methods |
| Network Hardening | Process of securing a network by reducing vulnerabilities |
| Default Credentials | Factory-set usernames/passwords (e.g., admin/admin) |
| Password Rotation | Regularly changing passwords to limit credential lifetime |
| Firewall Rule | Set of conditions determining allowed/denied traffic |
| Defense in Depth | Layered security approach with multiple controls |
| Credential Stuffing | Attack using stolen credentials from one site on another |
| PII | Personally Identifiable Information (names, addresses, etc.) |

<br><br>

## 12. Additional Recommendations for Future Improvement

| # | Recommendation | Priority | Purpose |
|---|----------------|----------|---------|
| 1 | Conduct regular vulnerability scans and patch updates | High | Identify new weaknesses |
| 2 | Implement network monitoring and IDS/IPS | Medium | Detect active attacks |
| 3 | Educate employees about secure authentication practices | Medium | Reduce password sharing |
| 4 | Establish formal information security policy | High | Document hardening requirements |
| 5 | Perform periodic penetration testing | Low | Validate security controls |

<br><br>

## 13. NIST CSF Mapping (Optional Reference)

| CSF Function | Lab Application |
|--------------|-----------------|
| **Identify** | Identified 4 key vulnerabilities |
| **Protect** | Recommended MFA, password policies, firewalls |
| **Detect** | Suggested monitoring + IDS/IPS |
| **Respond** | (Future improvement) Incident response plan |
| **Recover** | (Future improvement) Recovery procedures |














<br><br><br><br>

---

<br><br><br><br>












# Lab 7: Databases and SQL – Security Analysis & Data Investigation

**Tools Used:** MariaDB SQL  
**Focus Area:** Database Querying | Data Filtering | Table Joins  
**Skills:** SELECT Queries | WHERE Filters | AND/OR/NOT Operators | INNER/LEFT/RIGHT JOINs | Security Data Analysis  

<br><br>

## Objective

Learn to query, filter, and join data from a relational database using SQL. This lab provides practical experience in retrieving and analyzing information for security purposes, including investigating login attempts, employee device assignments, and departmental data.

<br><br>

## 1. Scenario Overview

As a cybersecurity analyst, I need to:
- Determine which employee devices must be updated
- Investigate user login activity for unusual events
- Analyze relationships between employees, machines, departments, and login attempts

**Data Sources:**
- `machines` table – employee device information
- `employees` table – employee details and department assignments
- `log_in_attempts` table – user login activity records

<br><br>

## 2. Lab Activities Summary

| Activity | Focus | Key SQL Concepts |
|----------|-------|------------------|
| 1 | Basic queries & sorting | SELECT, FROM, ORDER BY |
| 2 | Filtering with conditions | WHERE, LIKE pattern matching |
| 3 | Date/time & numeric filters | >, <, >=, <=, BETWEEN |
| 4 | Multiple conditions | AND, OR, NOT operators |
| 5 | Combining tables | INNER JOIN, LEFT JOIN, RIGHT JOIN |

<br><br>

## 3. Activity 1: Perform a SQL Query

**Objective:** Return information on employee devices and examine login attempts with sorting.

### Sample Data Structure

**`machines` table:**

| device_id | email_client | operating_system | OS_patch_date |
|-----------|--------------|------------------|---------------|
| 101 | Outlook | OS 1 | 2023-01-10 |
| 102 | Gmail | OS 2 | 2022-12-15 |
| 103 | Thunderbird | OS 2 | 2022-12-20 |
| 104 | Outlook | OS 3 | 2023-02-01 |

**`log_in_attempts` table:**

| event_id | username | login_date | login_time | country | success |
|----------|----------|------------|------------|---------|---------|
| 1 | alice | 2022-05-08 | 09:00:00 | USA | 1 |
| 2 | bob | 2022-05-09 | 18:30:00 | CAN | 0 |
| 3 | charlie | 2022-05-10 | 06:30:00 | MEX | 1 |
| 4 | diana | 2022-05-11 | 20:15:00 | USA | 0 |

### SQL Queries Executed

| Query # | Purpose | SQL Statement |
|---------|---------|---------------|
| 1 | View all devices | `SELECT * FROM machines;` |
| 2 | View specific columns | `SELECT device_id, email_client FROM machines;` |
| 3 | View device specs | `SELECT device_id, operating_system, OS_patch_date FROM machines;` |
| 4 | Investigate login locations | `SELECT event_id, country FROM log_in_attempts;` |
| 5 | Check after-hours logins | `SELECT username, login_date, login_time FROM log_in_attempts;` |
| 6 | View all login attempts | `SELECT * FROM log_in_attempts;` |
| 7 | Sort by date | `SELECT * FROM log_in_attempts ORDER BY login_date;` |
| 8 | Sort by date then time | `SELECT * FROM log_in_attempts ORDER BY login_date, login_time;` |

### Key Learning: ORDER BY

```sql
-- Single column sort
ORDER BY login_date;

-- Multi-column sort (date first, then time)
ORDER BY login_date, login_time;
```


## 4. Activity 2: Filter a SQL Query
Objective: Apply filters to retrieve specific information about employees, machines, and departments.

### Sample Data
**`machines` table:**

| device_id	| operating_system | 
| --------- | ---------------- | 
| 101 |	OS 1 |
| 102 |	OS 2 |
| 103 |	OS 2 |
| 104 |	OS 3 |


**`employees` table:**

| employee_id | name | department | office | device_id |
| ----------- | ---- | ---------- | ------ | --------- |
| 1 | Alice | Finance | North-101 | 101 | 
| 2 | Bob | Sales | South-109 | 102 |
| 3 | Charlie | Marketing | East-170 | 103 |
| 4 | Diana	| IT | West-220 | 104 |


### SQL Queries Executed
| Query | Purpose | SQL Statement |
|-------|---------|---------------|
| 1 | View device columns | SELECT device_id, operating_system FROM machines; |
| 2 | Filter OS 2 devices | SELECT device_id, operating_system FROM machines WHERE operating_system = 'OS 2'; |
| 3 | Finance department | SELECT * FROM employees WHERE department = 'Finance'; |
| 4 | Sales department | SELECT * FROM employees WHERE department = 'Sales'; |
| 5 | Specific office | SELECT * FROM employees WHERE office = 'South-109'; |
| 6 | South building (pattern) | SELECT * FROM employees WHERE office LIKE 'South-%'; |


### Key Learning: LIKE Pattern Matching
| Pattern | Meaning | Example Match |
|---------|---------|---------------|
| 'South-%' | Starts with "South-" | South-109, South-205 |
| '%East%' | Contains "East" | North-East, East-170 |
| '%109' | Ends with "109" | South-109, North-109 |


## 5. Activity 3: Apply More Filters in SQL
Objective: Filter data by dates, times, and numeric values using operators.

### **Sample Data:** `log_in_attempts`
| event_id | username | login_date | login_time | success | country |
|----------|----------|------------|------------|---------|---------|
| 100 | Alice | 2022-05-08 | 08:30:00 | 1 | USA |
| 101 | Bob | 2022-05-09 | 06:45:00 | 0 | CAN |
| 102 | Charlie | 2022-05-10 | 07:15:00 | 1 | MEX |
| 103 | Diana | 2022-05-11 | 06:30:00 | 0 | USA |
| 104 | Bob | 2022-05-12 | 08:00:00 | 1 | USA |


### SQL Queries Executed
| Filter Type | SQL Statement | Result Count |
|-------------|---------------|--------------|
| Date > value | WHERE login_date > '2022-05-09' | 3 rows |
| Date >= value | WHERE login_date >= '2022-05-09' | 4 rows |
| Date range | WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11' | 3 rows |
| Time < value | WHERE login_time < '07:00:00' | 2 rows |
| Time range | WHERE login_time BETWEEN '06:00:00' AND '07:00:00' | 2 rows |
| Numeric >= | WHERE event_id >= 100 | 5 rows |
| Numeric range | WHERE event_id BETWEEN 100 AND 150 | 5 rows |


### Key Learning: Comparison Operators
| Operator | Meaning | Use Case |
|----------|---------|----------|
| > | Greater than | After a specific date |
| >= | Greater than or equal | On or after a date |
| < | Less than | Before a specific time |
| <= | Less than or equal | On or before |
| BETWEEN | Inclusive range | Date or numeric ranges |


## 6. Activity 4: Filter with AND, OR, and NOT
Objective: Apply multiple conditions using logical operators.

### Sample Data
#### **`log_in_attempts` table:**

| event_id | username | login_date | login_time | success | country |
|---------|----------|------------|------------|---------|---------|
| 100 | Alice | 2022-05-08 | 08:30:00 | 1 | USA |
| 101 | Bob | 2022-05-09 | 19:00:00 | 0 | CAN |
| 102 | Charlie | 2022-05-10 | 17:15:00 | 1 | MEX |
| 103 | Diana | 2022-05-11 | 20:30:00 | 0 | USA |
| 104 | Eve | 2022-05-12 | 16:00:00 | 1 | MEX |

#### **`employees` table:**

| emp_id | username | department | office |
|--------|----------|------------|--------|
| 1 | Alice | Finance | East-170 |
| 2 | Bob | Sales | South-109|
| 3 | Charlie | Marketing | East-320 |
| 4 | Diana | Information Technology | West-205 |
| 5 | Eve | Marketing | East-170 |


### SQL Queries Executed
| Query | Logical Operator | SQL Statement | Security Relevance |
|------|------------------|----------------|--------------------|
| 1 | AND | WHERE login_time > '18:00' AND success = 0 | Failed after-hours logins |
| 2 | OR | WHERE login_date = '2022-05-08' OR login_date = '2022-05-09' | Suspicious date range |
| 3 | NOT | WHERE NOT country LIKE 'MEX%' | Exclude specific country |
| 4 | AND | WHERE department = 'Marketing' AND office LIKE 'East-%' | Dept in specific building |
| 5 | OR | WHERE department = 'Finance' OR department = 'Sales' | High-value departments |
| 6 | NOT | WHERE NOT department = 'Information Technology' | All except IT |


### Key Learning: Logical Operator Truth Table
| Condition A | Condition B | A AND B | A OR B | NOT A |
|-------------|-------------|---------|--------|-------|
| TRUE | TRUE | TRUE | TRUE | FALSE |
| TRUE | FALSE | FALSE | TRUE | FALSE |
| FALSE | TRUE | FALSE | TRUE | TRUE |
| FALSE | FALSE | FALSE | FALSE | TRUE |


## 7. Activity 5: Complete a Join
Objective: Use INNER JOIN, LEFT JOIN, and RIGHT JOIN to combine tables.

### Sample Data
#### **`employees` table:**

| emp_id | username | department | device_id |
|--------|----------|------------|-----------|
| 1 | Alice | Finance | 101 |
| 2 | Bob | Sales | 102 |
| 3 | Charlie | Marketing | 103 |
| 4 | Diana | IT | NULL |
| 5 | Eve | Marketing | 104 |

#### **`machines` table:**

| device_id | device_name | operating_system |
|-----------|-------------|------------------|
| 101 | Laptop-A | OS 1 |
| 102 | Laptop-B | OS 2 |
| 103 | Laptop-C | OS 2 |
| 105 | Laptop-E | OS 1 |

#### **`log_in_attempts` table:**

| event_id | username | login_date | login_time | success | 
| -------- | -------- | ---------- | ---------- | ------- | 
| 100 | Alice | 2022-05-08 | 08:30:00 |	1 |
| 101 | Bob | 2022-05-09 | 19:00:00 | 0 |
| 102 | Charlie | 2022-05-10 | 17:15:00 | 1 |
| 103 | Eve | 2022-05-11 | 20:30:00 | 0 |


### Join Results Summary
| Join Type | SQL Statement | Rows Returned | What It Shows |
|-----------|---------------|---------------|---------------|
| INNER JOIN | machines INNER JOIN employees ON machines.device_id = employees.device_id | 3 | Only matched records |
| LEFT JOIN | machines LEFT JOIN employees ON machines.device_id = employees.device_id | 4 | All machines + matches |
| RIGHT JOIN | machines RIGHT JOIN employees ON machines.device_id = employees.device_id | 5 | All employees + matches |
| INNER JOIN login | employees INNER JOIN log_in_attempts ON employees.username = log_in_attempts.username | 4 | Employees with login records |


### Key Learning: JOIN Types Visualized
| Join Type  | Result |
|------------|--------|
| INNER JOIN | Only rows with matches in both tables |
| LEFT JOIN | All left + matched right (NULL if no match) |
| RIGHT JOIN | All right + matched left (NULL if no match) |

#### INNER JOIN: 
| A | B | 
| ✓ | ✓ |
| ✓ | ✓ |

#### LEFT JOIN: 
| A | B | 
| ✓ | ✓ |
| ✓ | ✓ |
| ✓ | NULL |

#### RIGHT JOIN:
| A | B | 
| ✓ | ✓ |
| ✓ | ✓ |
| NULL | ✓ |




## 8. Security Applications of SQL
| Security Task | SQL Technique | Example Use Case |
|---------------|---------------|------------------|
| Incident investigation | WHERE filters | Find failed logins after hours |
| User behavior analysis | ORDER BY | Identify unusual login patterns |
| Asset management | JOIN | Match employees to devices |
| Compliance reporting | SELECT + filters | Generate audit reports |
| Anomaly detection | BETWEEN | Detect off-hours logins |
| Department isolation | AND / OR | Focus on sensitive departments |


## 9. Skills Demonstrated
| Skill | Application in Lab |
|-------|--------------------|
| SELECT queries | Retrieved specific columns |
| WHERE filters | Filtered based on conditions |
| Comparison operators | Used >, <, >=, <=, BETWEEN |
| Logical operators | Used AND, OR, NOT |
| Pattern matching | Used LIKE with % |
| Sorting | Used ORDER BY |
| Table joins | INNER, LEFT, RIGHT JOIN |
| Security data analysis | Investigated login anomalies |


## 10. Reflection
This lab provided hands-on experience with SQL for security analysis purposes. Key takeaways:

- SELECT statements form the foundation of data retrieval – knowing which columns to query saves time and reduces noise
- WHERE filters are essential for narrowing down security investigations (e.g., failed logins, specific time ranges)
- Logical operators (AND, OR, NOT) enable complex investigations that combine multiple conditions
- JOINs are critical for understanding relationships between entities (employees → devices → login attempts)
- ORDER BY helps identify patterns chronologically, which is crucial for incident timelines

Demonstrates: Practical SQL proficiency for security monitoring, incident investigation, and asset management.

## 11. Appendix: Key Terminology
	
| Term | Meaning |
|------|---------|
| SELECT | SQL statement to retrieve data from a database |
| FROM | Specifies which table to query |
| WHERE | Filters rows based on conditions |
| ORDER BY | Sorts results by specified columns |
| LIKE | Pattern matching with wildcards (%) |
| BETWEEN | Filters within an inclusive range |
| AND | Requires both conditions to be true |
| OR | Requires at least one condition to be true |
| NOT | Excludes rows matching the condition |
| INNER JOIN | Returns only matching rows from both tables |
| LEFT JOIN | Returns all rows from left table + matches from right |
| RIGHT JOIN | Returns all rows from right table + matches from left |
| Wildcard (%) | Matches any character(s) in LIKE patterns |

## 12. SQL Quick Reference Card
```sql
-- Basic query
SELECT column1, column2 FROM table_name;

-- Filtering
SELECT * FROM table_name WHERE condition;

-- Pattern matching
SELECT * FROM employees WHERE office LIKE 'East-%';

-- Date/time filtering
SELECT * FROM logins WHERE login_date > '2023-01-01';

-- Multiple conditions
SELECT * FROM logins WHERE login_time > '18:00' AND success = 0;

-- Sorting
SELECT * FROM logins ORDER BY login_date DESC;

-- Inner join
SELECT * FROM table1 INNER JOIN table2 ON table1.key = table2.key;

-- Left join
SELECT * FROM table1 LEFT JOIN table2 ON table1.key = table2.key;
```








<br><br><br><br>

---

<br><br><br><br>











# Lab 8: Linux Commands in the Bash Shell

**Tools Used:** Bash Shell | Linux Command Line  
**Focus Area:** System Navigation | File Management | User Administration | Permissions | Log Analysis   
**Skills:** pwd, ls, cd, cat, head, grep, mkdir, mv, rm, touch, nano, chmod, useradd, usermod, userdel, groupdel, man, whatis, apropos  

<br><br>

## Objective

Develop foundational Linux Bash skills for security analysis, including navigating directories, managing files, filtering data, controlling permissions, administering users, and accessing command-line help.

<br><br>

## 1. Scenario Overview

As a cybersecurity analyst working in a Linux environment, I need to:
- Navigate the file system to locate logs and reports
- Filter and search files for specific security events
- Create, move, and delete files and directories
- Manage file permissions to enforce access control
- Add and remove users and groups
- Find help for unfamiliar commands

<br><br>

## 2. Lab Activities Summary

| Activity | Focus | Key Commands | Security Relevance |
|----------|-------|--------------|-------------------|
| 1 | Finding files & navigation | pwd, ls, cd, cat, head | Locating logs and investigating file contents |
| 2 | Filtering with grep | grep, pipe (\|) | Searching logs for errors or specific users |
| 3 | Managing files | mkdir, mv, rm, touch, nano | Organizing evidence and cleaning up files |
| 4 | Managing permissions | chmod, ls -la | Restricting access to sensitive files |
| 5 | User management | useradd, usermod, chown, userdel | Controlling system access and ownership |
| 6 | Getting help | man, whatis, apropos | Discovering commands and options |

<br><br>

## 3. Activity 1: Find Files with Linux Commands

**Objective:** Navigate directories, locate files, and read file contents.

### Command Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `pwd` | Print working directory | `pwd` → `/home/analyst` |
| `ls -l` | List files with details | Shows permissions, owner, size, date |
| `cd [directory]` | Change directory | `cd /home/analyst/reports` |
| `cat [file]` | Display entire file | `cat Q1_added_users.txt` |
| `head -n [number] [file]` | Show first N lines | `head -n 10 server_logs.txt` |

### Commands Executed
```bash
# Navigate to reports directory and examine users
cd /home/analyst/reports
cd users
ls
cat Q1_added_users.txt

# Navigate to logs and preview content
cd /home/analyst/logs
ls
head -n 10 server_logs.txt
```

### Security Application
| Task	| Command | Purpose |
|-------|---------|---------|
| Locate log files | cd /var/log | Access system logs |
| Preview large logs | head -n 50 auth.log | Check recent authentication attempts |
| Read configuration | cat /etc/passwd | View user accounts |

<br><br>

## 4. Activity 2: Filter with grep
**Objective:** Use grep and piping to search for specific information.

### Command Reference
| Command | Purpose | Example | 
|---------|---------|---------|
| grep "pattern" [file] | Search for pattern in file | grep "error" server_logs.txt |
| command \| grep "pattern" | Pipe output to grep | ls \| grep "Q1" |


### Commands Executed
```bash
# Search for errors in logs
cd /home/analyst/logs
grep "error" server_logs.txt

# Find files with specific patterns
cd /home/analyst/reports/users
ls | grep "Q1"
ls | grep "access"

# Search for specific users
grep "jhill" Q2_deleted_users.txt
grep "Human Resource" Q4_added_users.txt
```


### Security Application
| Task | Command | Purpose | 
|------|---------|---------|
| Find failed logins | grep "Failed password" /var/log/auth.log | Investigate brute force attempts |
| Search by IP | grep "192.168.1.100" access.log | Track specific attacker |
| Exclude patterns | grep -v "success" login.log | Find only failures |
| Count matches | grep -c "error" server_logs.txt | Quantify issues |


### grep Options Reference
| Option | Meaning | Use Case |
|--------|---------|----------|
| -i | Case insensitive | Search without case sensitivity |
| -v | Invert match | Exclude matching lines |
| -c | Count | Count occurrences |
| -n | Show line numbers | Locate exact position |
| -r | Recursive | Search directories |

<br><br>

## 5. Activity 3: Manage Files with Linux Commands
**Objective:** Create, move, remove files and directories, and edit files using nano.

### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `mkdir [dir]` | Create directory | `mkdir /home/analyst/logs` |
| `rm [file]` | Remove file | `rm tempnotes.txt` |
| `rm -r [dir]` | Remove directory recursively | `rm -r /home/analyst/temp` |
| `mv [source] [dest]` | Move/rename file | `mv Q3patches.txt /home/analyst/reports` |
| `touch [file]` | Create empty file | `touch tasks.txt` |
| `nano [file]` | Edit file | `nano tasks.txt` |
| `clear` | Clear terminal screen | `clear` |


### Commands Executed
```bash
# Create and remove directories
mkdir /home/analyst/logs
rm -r /home/analyst/temp

# Move and delete files
mv /home/analyst/notes/Q3patches.txt /home/analyst/reports
rm /home/analyst/notes/tempnotes.txt

# Create and edit file
touch /home/analyst/notes/tasks.txt
nano /home/analyst/notes/tasks.txt
cat /home/analyst/notes/tasks.txt
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Create evidence directory | `mkdir incident_2024` | Organize investigation files |
| Move suspicious file | `mv suspect_file /quarantine/` | Isolate potential malware |
| Remove sensitive temp files | `rm -r /tmp/sensitive_data` | Secure data cleanup |
| Create case notes | `touch case_notes.txt && nano case_notes.txt` | Document findings |

<br><br>

## 6. Activity 4: Manage Authorization
**Objective:** Examine and modify file and directory permissions.

### Permission Structure
-rw-r--r-- 1 owner group size date filename
│││││││││
│││└─┴─┴─┴─ Other permissions (read/write/execute)
││└─────── Group permissions
│└──────── Owner permissions
└───────── File type (-=file, d=directory)


| Permission | Symbol | Numeric Value | Meaning |
|------------|--------|---------------|---------|
| Read | r | 4 | View contents |
| Write | w | 2 | Modify contents |
| Execute | x | 1 | Run as program |



### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `ls -la` | List all files with permissions | `ls -la` |
| `chmod [permissions] [file]` | Change file permissions | `chmod o-w project_k.txt` |


### Permission Formats
| Format | Example | Meaning |
|--------|---------|---------|
| Symbolic | `chmod o-w file.txt` | Remove write for others |
| Symbolic | `chmod go-rw file.txt` | Remove read/write for group and others |
| Symbolic | `chmod ug=r file.txt` | Set owner and group to read-only |
| Numeric | `chmod 755 file.txt` | Owner:rwx, Group:r-x, Other:r-x |


### Commands Executed
```bash
cd /home/researcher2/projects
ls -la

# Remove write permission for others
chmod o-w project_k.txt

# Restrict group permissions
chmod go-rw project_m.txt

# Adjust hidden file permissions
chmod ug=r .project_x.txt

# Remove execute permission for group on directory
chmod g-x drafts
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Check file permissions | `ls -la sensitive_file.txt` | Verify access restrictions |
| Remove world read | `chmod o-r /etc/shadow` | Protect password hashes |
| Make script executable | `chmod +x scan.sh` | Allow script execution |
| Restrict directory access | `chmod 700 /home/analyst/private` | Only owner can access |

<br><br>

## 7. Activity 5: Add and Manage Users with Linux Commands
**Objective:** Add, modify, and delete users and groups.

### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `sudo useradd [username]` | Add new user | `sudo useradd researcher9` |
| `sudo usermod -g [group] [user]` | Set primary group | `sudo usermod -g research_team researcher9` |
| `sudo usermod -a -G [group] [user]` | Add to secondary group | `sudo usermod -a -G sales_team researcher9` |
| `sudo chown [user] [file]` | Change file owner | `sudo chown researcher9 project_r.txt` |
| `sudo userdel [username]` | Delete user | `sudo userdel researcher9` |
| `sudo groupdel [groupname]` | Delete group | `sudo groupdel researcher9` |


### User vs Group Types
| Type | Description | Example |
|------|-------------|---------|
| Primary group | Default group for user's files | research_team |
| Secondary group | Additional group membership | sales_team |
| System user | Service account (no login) | www-data |


### Commands Executed
```bash
# Add new user
sudo useradd researcher9

# Set primary group
sudo usermod -g research_team researcher9

# Change file ownership
sudo chown researcher9 /home/researcher2/projects/project_r.txt

# Add to secondary group
sudo usermod -a -G sales_team researcher9

# Delete user and group
sudo userdel researcher9
sudo groupdel researcher9
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Create auditor account | `sudo useradd auditor` | Temporary investigation access |
| Remove departed employee | `sudo userdel -r jsmith` | Revoke access immediately |
| Change file ownership | `sudo chown newadmin config.ini` | Transfer responsibility |
| Verify group membership | `groups researcher9` | Check user's groups |

<br><br>

## 8. Activity 6: Get Help in the Command Line
**Objective:** Use man, whatis, and apropos to discover commands and options.

### Command Reference
| Command | Purpose | Example |
|---------|---------|---------|
| `whatis [command]` | Short description | `whatis cat` → "concatenate files and print" |
| `man [command]` | Manual page | `man cat` (full documentation) |
| `apropos [keyword]` | Search commands by keyword | `apropos "create new group"` |


### Commands Executed
```bash
# Get short descriptions
whatis cat
whatis rm
whatis rmdir

# Read manual pages
man cat
man useradd

# Search for commands by keyword
apropos "first part file"
apropos "create new group"
```


### Security Application
| Task | Command | Purpose |
|------|---------|---------|
| Find log viewing command | `apropos "view log"` | Discover tail, less, journalctl |
| Learn chmod syntax | `man chmod` | Understand permission options |
| Check command purpose | `whatis journalctl` | Quick command description |

<br><br>

## 9. Linux Command Quick Reference Card
### Navigation & File Management
```bash
pwd                    # Show current directory
ls -la                 # List all files with details
cd /path/to/dir        # Change directory
cat file.txt           # Display entire file
head -n 20 file.txt    # Show first 20 lines
tail -n 20 file.txt    # Show last 20 lines
```


### File Operations
```bash
mkdir new_dir          # Create directory
rm file.txt            # Delete file
rm -r directory        # Delete directory recursively
mv source destination  # Move or rename
cp source destination  # Copy file
touch newfile.txt      # Create empty file
nano file.txt          # Edit file
```


### Searching & Filtering
```bash
grep "pattern" file.txt          # Search in file
grep -i "pattern" file.txt       # Case insensitive
grep -v "pattern" file.txt       # Exclude pattern
ls | grep "keyword"              # Pipe to filter
```

### Permissions
```bash
ls -la                 # View permissions
chmod 755 file.txt     # Numeric: rwxr-xr-x
chmod u+x file.txt     # Add execute for owner
chmod go-rw file.txt   # Remove r/w for group/others
chown user:group file  # Change owner:group
```

### User Management (requires sudo)
```bash
sudo useradd username           # Add user
sudo userdel -r username        # Delete user with home dir
sudo usermod -aG group username # Add to secondary group
sudo groupadd groupname         # Create group
sudo groupdel groupname         # Delete group
```

### Getting Help
```bash
whatis command         # One-line description
man command            # Full manual
command --help         # Short help (many commands)
apropos keyword        # Search commands by keyword
```

<br><br>

## 10. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| Directory navigation | pwd, cd, ls to locate logs and reports |
| File content inspection | cat, head to read user lists and logs |
| Pattern searching | grep with piping to filter files and content |
| File management | mkdir, mv, rm, touch, nano for organizing evidence |
| Permission management | chmod, ls -la to restrict access |
| User administration | useradd, usermod, chown, userdel for access control |
| Command discovery | man, whatis, apropos to find help |

<br><br>

## 11. Reflection
This lab provided comprehensive hands-on experience with essential Linux Bash commands. Key takeaways:

- Navigation and file inspection (pwd, cd, ls, cat, head) are foundational for locating and examining logs during incident investigation
- grep with piping enables efficient searching through large log files – critical for identifying specific events like failed logins or error patterns
- File management commands (mkdir, mv, rm, touch, nano) help organize investigation artifacts and document findings
- Permission management (chmod, ls -la) ensures sensitive files are protected according to the principle of least privilege
- User administration (useradd, usermod, userdel) is essential for onboarding/offboarding and maintaining proper access control
- Help commands (man, whatis, apropos) enable self-sufficient learning and discovery of new commands

Demonstrates: Practical Linux proficiency for security monitoring, incident investigation, log analysis, and system administration.

<br><br>

## 12. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Bash | Bourne Again SHell – default Linux command-line interpreter |
| Directory | Linux term for folder |
| Piping (\|) | Sends output of one command as input to another |
| grep | Global Regular Expression Print – searches for patterns |
| Permission | Access control setting (read, write, execute) |
| Owner | User who owns a file/directory |
| Group | Collection of users with shared permissions |
| chmod | Change mode – modifies permissions |
| sudo | Superuser do – executes command with elevated privileges |
| Home directory | User's personal directory (/home/username) |
| Manual page | Built-in documentation for Linux commands |

<br><br>

## 13. Common Security Scenarios & Linux Commands
| Scenario | Linux Command |
|----------|---------------|
| Investigate failed SSH logins | `grep "Failed password" /var/log/auth.log` |
| Find large log files | `find /var/log -size +100M` |
| Monitor live log | `tail -f /var/log/syslog` |
| Check disk space | `df -h` |
| Find files owned by user | `find /home -user jsmith` |
| Count unique IPs in log | `grep "Failed" auth.log \| awk '{print $11}' \| sort \| uniq -c` |
| Backup directory | `cp -r /important/data /backup/` |






<br><br><br><br>

---

<br><br><br><br>







# Lab 9: Introduction to Asset Security

**Focus Area:** Asset Management | Risk Assessment | Asset Classification  
**Skills:** Asset Inventory Creation | Sensitivity Classification | Risk Scoring | Likelihood & Severity Assessment | Risk Prioritization  

<br><br>

## Objective

Understand asset management and risk assessment in a cybersecurity context. This lab focuses on:
1. Classifying assets connected to a home network based on sensitivity
2. Scoring risks based on likelihood and severity to prioritize security resources

<br><br>

## 1. Scenario Overview

Asset security is the foundation of any cybersecurity program. Organizations cannot protect what they don't know exists. This lab simulates two real-world scenarios:

| Activity | Scenario | Purpose |
|----------|----------|---------|
| **Activity 1** | Home network asset inventory | Identify, document, and classify all connected devices |
| **Activity 2** | Bank operational risk assessment | Evaluate risks, calculate scores, and prioritize responses |

<br><br>

## 2. Activity 1: Classify Assets Connected to a Home Network

**Objective:** Create an inventory of devices connected to a home network, identify their characteristics, and classify them based on sensitivity to risk.

### Asset Classification Framework

| Sensitivity Level | Definition | Example | Protection Required |
|-------------------|------------|---------|---------------------|
| **Restricted** | Most sensitive; breach causes severe damage | Financial data, PII, medical records | Encryption, strict access controls, monitoring |
| **Confidential** | Sensitive but not critical; breach causes moderate damage | Private photos, internal documents | Access controls, basic encryption |
| **Internal-only** | Not sensitive but not public | Guest devices, media players | Basic network security |
| **Public** | No impact if disclosed | Marketing materials | Minimal protection |

### Asset Inventory Table

| Asset | Network Access | Owner | Location | Notes | Sensitivity |
|-------|---------------|-------|----------|-------|-------------|
| Network router | Continuous | ISP | On-premises | 2.4 GHz and 5 GHz connections; all devices connect to 5 GHz | Confidential |
| Desktop | Occasional | Homeowner | On-premises | Contains private information, like photos | Restricted |
| Guest smartphone | Occasional | Friend | On/Off-premises | Connects to home network | Internal-only |
| External hard drive | Occasional | Homeowner | On-premises | Contains music and movies | Confidential |
| Streaming media player | Continuous | Homeowner | On-premises | Payment card information stored for rentals | Internal-only |
| Portable game console | Occasional | Friend | On/Off-premises | Has camera and microphone | Internal-only |

### Asset Analysis by Sensitivity

| Sensitivity | Assets | Risk Level | Recommended Controls |
|-------------|--------|------------|----------------------|
| **Restricted** | Desktop | 🔴 High | Full disk encryption, strong password, regular backups |
| **Confidential** | Router, External HDD | 🟠 Medium-High | Secure configuration, access logging |
| **Internal-only** | Guest phone, Media player, Game console | 🟡 Medium | Network segmentation (guest Wi-Fi) |

### Security Observations

| Observation | Implication | Recommendation |
|-------------|-------------|----------------|
| Guest devices connect to main network | Potential lateral movement | Set up guest Wi-Fi network |
| Streaming device stores payment info | Financial data at risk | Use separate account with spending limits |
| Desktop contains private photos | Personal data exposure risk | Enable encryption + strong authentication |

### Reflection - Activity 1

This activity highlighted the importance of maintaining an accurate inventory of all network-connected devices. Evaluating network access, ownership, location, and stored information helped classify assets and prioritize their protection. Sensitive devices were labeled with higher sensitivity to enforce a "need-to-know" access approach.

**Key takeaways:**
- Asset inventory is the first step in any security program
- Different sensitivity levels require different protection strategies
- Guest devices should be isolated from trusted networks
- Even home networks have Restricted-level assets

**Future improvements:**
- Track non-networked assets (USB drives, paper records)
- Implement additional security measures for shared devices
- Regular inventory audits (quarterly)

<br><br>

## 3. Activity 2: Score Risks Based on Likelihood and Severity

**Objective:** Perform a risk assessment for a bank's operational environment, evaluate the likelihood and severity of potential security risks, and prioritize cybersecurity resources.

### Risk Assessment Framework

**Risk Formula:** `Risk Score = Likelihood × Severity`

| Score Range | Priority Level | Action Required |
|-------------|----------------|-----------------|
| 1-2 | Low | Monitor, accept risk |
| 3-4 | Medium | Plan mitigation |
| 6-8 | High | Implement controls |
| 9 | Critical | Immediate action required |

### Likelihood Scale

| Score | Level | Definition | Frequency |
|-------|-------|------------|-----------|
| 1 | Rare | May occur once every few years | <5% chance annually |
| 2 | Likely | Could occur annually | 5-50% chance annually |
| 3 | High | Likely to occur multiple times per year | >50% chance annually |

### Severity Scale

| Score | Level | Financial Impact | Operational Impact | Reputational Impact |
|-------|-------|------------------|---------------------|---------------------|
| 1 | Low | <$10K | Minor disruption | Limited |
| 2 | Moderate | $10K-$100K | Temporary outage | Local negative attention |
| 3 | High | >$100K | Extended outage | Widespread negative attention, regulatory action |

### Risk Register Table

| Asset | Risk | Description | Likelihood | Severity | Priority (Score) |
|-------|------|-------------|------------|----------|------------------|
| Funds | Business email compromise | Employee tricked into sharing confidential information | 2 | 2 | 4 |
| Funds | Compromised user database | Customer data poorly encrypted | 2 | 3 | 6 |
| Funds | Financial records leak | Database server of backed-up data publicly accessible | 3 | 3 | 9 |
| Funds | Theft | Bank's safe left unlocked | 1 | 3 | 3 |
| Funds | Supply chain disruption | Delivery delays due to natural disasters | 1 | 2 | 2 |

### Risk Matrix Visualization
| Likelihood \ Severity | Low (1)        | Moderate (2)        | High (3)              |
|----------------------|----------------|----------------------|------------------------|
| Rare (1)             | [1] Theft      | [2] Supply Chain     | [3] Theft (Sev 3)      |
| Likely (2)           | [2] BEC        | [4] ★ User DB        | [6] ★★                 |
| High (3)             | [3]            | [6] ★★               | [9] ★★★ Records Leak   |

**Legend:**  
- ★ = Medium Priority  
- ★★ = High Priority  
- ★★★ = Critical Priority


### Detailed Risk Analysis

| Risk | Likelihood Justification | Severity Justification | Priority |
|------|-------------------------|----------------------|----------|
| **Financial records leak** | 3 – Database publicly accessible → frequent risk | 3 – Severe financial, regulatory, reputational impact | **9 (Critical)** |
| **Compromised user database** | 2 – Customer data frequently targeted | 3 – Regulatory fines (GDPR, CCPA) + reputational damage | **6 (High)** |
| **Business email compromise** | 2 – Employees occasionally fall for phishing | 2 – Moderate financial/data loss | **4 (Medium)** |
| **Theft** | 1 – Low-crime area | 3 – Critical operational impact if occurs | **3 (Low-Medium)** |
| **Supply chain disruption** | 1 – Natural disasters unpredictable | 2 – Operational delays | **2 (Low)** |

### Risk Priority Action Plan

| Priority | Risk | Action | Timeline | Responsible |
|----------|------|--------|----------|-------------|
| **Critical (9)** | Financial records leak | Immediately secure public database; audit access logs | 24 hours | IT Security Lead |
| **High (6)** | Compromised user database | Implement encryption at rest and in transit | 1 week | Database Admin |
| **Medium (4)** | Business email compromise | Deploy email filtering; conduct phishing training | 2 weeks | Security Awareness Team |
| **Low (3)** | Theft | Install safe alarm; review physical security | 1 month | Facilities Manager |
| **Low (2)** | Supply chain disruption | Develop contingency plan; identify backup suppliers | 3 months | Operations Manager |

### External Risk Factors

| Factor | Impact on Bank | Mitigation |
|--------|---------------|------------|
| Multiple external entity interactions | Increased data compromise risk | Vendor risk assessments |
| Regulatory environment (GDPR, CCPA) | High compliance risk | Regular compliance audits |
| Low local crime rate | Reduced theft priority | Still maintain baseline physical security |

### Reflection - Activity 2

This activity demonstrated the process of evaluating security risks systematically. By assigning likelihood and severity scores, I calculated overall risk priorities to guide cybersecurity decision-making.

**Key takeaways:**
- Risk scoring provides objective prioritization (not just gut feeling)
- The highest priority risk (financial records leak) had both high likelihood AND high severity
- Low-likelihood risks can still be high-severity (theft) but may be deprioritized
- External factors (regulations, third-party relationships) expand risk surface

**The risk formula (Likelihood × Severity) reveals:**
- Critical risks: High × High = 9
- High risks: High × Moderate OR Moderate × High = 6
- Medium risks: Moderate × Moderate = 4
- Low risks: Rare × Anything = 1-3

**Future improvements:**
- Integrate historical incident data to refine likelihood estimates
- Add risk velocity (how quickly risk materializes)
- Include risk appetite tolerance thresholds

<br><br>

## 4. Asset Security Best Practices Summary

| Practice | Description | Application |
|----------|-------------|-------------|
| **Asset Inventory** | Maintain complete list of all assets | Tracked 6 home network devices |
| **Asset Classification** | Label by sensitivity level | Restricted → Internal-only |
| **Risk Assessment** | Calculate likelihood × severity | Identified critical risk (score 9) |
| **Risk Prioritization** | Address highest scores first | Records leak prioritized |
| **Continuous Monitoring** | Regular reassessment | Quarterly inventory audits recommended |

<br><br>

## 5. Skills Demonstrated

| Skill | Application in Lab |
|-------|-------------------|
| Asset inventory creation | Documented 6 network-connected devices with characteristics |
| Sensitivity classification | Assigned Restricted, Confidential, Internal-only labels |
| Risk identification | Identified 5 distinct risks for bank environment |
| Likelihood assessment | Rated risks as Rare (1), Likely (2), or High (3) |
| Severity assessment | Rated impact as Low (1), Moderate (2), or High (3) |
| Risk scoring | Calculated priority scores using Likelihood × Severity |
| Risk prioritization | Ranked risks from Critical (9) to Low (2) |
| Action planning | Developed timeline-based mitigation strategies |

<br><br>

## 6. Tools and Concepts Used

| Tool/Concept | Application |
|--------------|-------------|
| Asset Inventory Table | Documented device characteristics |
| Sensitivity Classification Framework | Assigned protection levels |
| Risk Register | Structured risk documentation |
| Risk Matrix (5×5) | Visualized likelihood vs. severity |
| Risk Formula (L×S) | Calculated numerical priorities |
| Priority Action Plan | Mapped risks to mitigation timelines |

<br><br>

## 7. Reflection - Full Lab

This lab reinforced the foundational relationship between **asset management** and **risk assessment** in cybersecurity.

**Connection to real-world security:**
- Organizations cannot protect what they haven't identified
- Not all assets require the same level of protection
- Risk scoring enables data-driven decisions, not guesswork
- Home networks mirror organizational risks (just smaller scale)

**Key insights:**
| Concept | Insight |
|---------|---------|
| Asset inventory | Even home networks have Restricted-level assets (personal data) |
| Classification | Guest devices on main network create unnecessary risk |
| Risk scoring | Critical risks require immediate action (score 9) |
| Prioritization | Low-likelihood + high-severity = medium priority (score 3) |

**Demonstrates:** Asset security fundamentals, risk assessment methodology, and practical security decision-making applicable to both home and enterprise environments.

<br><br>

## 8. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| **Asset** | Anything of value to an organization (hardware, data, people) |
| **Asset Inventory** | Complete list of all assets with characteristics |
| **Asset Classification** | Labeling assets by sensitivity level |
| **Risk** | Potential for loss or damage |
| **Likelihood** | Probability of risk occurring |
| **Severity** | Impact magnitude if risk occurs |
| **Risk Score** | Likelihood × Severity (numerical priority) |
| **Risk Register** | Document tracking identified risks |
| **Risk Matrix** | Grid visualizing likelihood vs. severity |
| **Business Email Compromise (BEC)** | Phishing attack targeting employees for data/funds |
| **PII** | Personally Identifiable Information |
| **Need-to-know** | Access principle: only provide necessary access |

<br><br>

## 9. Risk Assessment Quick Reference

### Risk Score Calculation
- Risk Score = Likelihood (1-3) × Severity (1-3)
- Possible scores: 1, 2, 3, 4, 6, 9


### Priority Matrix

| Score | Priority | Action |
|-------|----------|--------|
| 9 | Critical | Immediate action (24 hours) |
| 6 | High | Short-term action (1 week) |
| 4 | Medium | Planned action (2-4 weeks) |
| 2-3 | Low | Monitor or accept |
| 1 | Very Low | No action needed |

### Likelihood × Severity Heat Map
| Likelihood \ Severity | 1 (Low) | 2 (Moderate) | 3 (High) |
|----------------------|--------|--------------|----------|
| 1 (Rare)             | 1 🟢   | 2 🟢         | 3 🟡     |
| 2 (Likely)           | 2 🟢   | 4 🟡         | 6 🟠     |
| 3 (High)             | 3 🟡   | 6 🟠         | 9 🔴     |

**Legend:**
- 🟢 Low (1–2)
- 🟡 Medium (3–4)
- 🟠 High (6)
- 🔴 Critical (9)













<br><br><br><br>

---

<br><br><br><br>














# Lab 10: Protect Organizational Assets

**Focus Area:** Data Protection | Encryption | Hashing | Access Control | Least Privilege  
**Standards Referenced:** NIST SP 800-53 (AC-6)  
**Skills:** Data Handling Policies | Encryption/Decryption | Hash Generation (SHA-256) | File Integrity Verification | RBAC | Account Lifecycle Management | MFA  

<br><br>

## Objective

Protect organizational data through secure handling practices, encryption, hashing, and access control improvements. This lab consists of four activities simulating real-world cybersecurity scenarios.

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Key Tools/Concepts | Security Relevance |
|----------|-------|-------------------|-------------------|
| 1 | Data handling & least privilege | NIST SP 800-53 AC-6, role-based access | Prevent data leaks |
| 2 | Decrypt encrypted messages | Caesar cipher, OpenSSL (AES-256-CBC) | Recover encrypted data |
| 3 | Create hash values | SHA-256, sha256sum, cmp | File integrity verification |
| 4 | Improve AAA (Authentication, Authorization, Accounting) | RBAC, MFA, account lifecycle | Access control enforcement |

<br><br>

## 2. Activity 1: Determine Appropriate Data Handling Practices

**Objective:** Analyze a data leak incident and recommend improvements using the principle of least privilege.

### Incident Summary

| Aspect | Details |
|--------|---------|
| **What happened** | Employee mistakenly shared entire folder of sensitive internal documents instead of limited materials |
| **Root cause** | Access to folder was not properly restricted or revoked after meeting |
| **Key failure** | Manager failed to remove access post-meeting; poor access control oversight |

### NIST SP 800-53: AC-6 - Least Privilege

| Aspect | Description |
|--------|-------------|
| **Purpose** | Ensure users are granted only minimum access necessary to perform tasks |
| **Key principle** | "Need-to-know" + "need-to-do" |
| **Implementation strategies** | Role-based access, time-bound access, regular access reviews |
| **Enhancements** | Privilege separation, parameterized access, monitoring privileged actions |

### Least Privilege Implementation Model

| Step | Process                  | Description                                      |
|------|--------------------------|--------------------------------------------------|
| 1    | User Request             | User requests access to a resource               |
| 2    | Role Evaluation          | System checks user's role/permissions            |
| 3    | Minimum Required Access  | Determine least privilege needed                 |
| 4    | Access Granted           | Only necessary access is provided                |
| 5    | Review & Revocation      | Periodic audit and removal of excess privileges  |


### Root Cause Analysis

| Cause Category | Specific Issue |
|----------------|----------------|
| **Policy** | No automatic access revocation |
| **Human** | Manager forgot to remove access |
| **Technical** | No time-based access controls |
| **Oversight** | No audit of folder permissions |

### Recommendations & Justification

| Recommendation | Implementation | Justification |
|----------------|----------------|---------------|
| Restrict access based on user roles | Implement RBAC | Ensures only authorized users view sensitive data |
| Automatically revoke access after defined period | Time-bound access controls | Reduces risk of forgotten permissions |
| Regular access reviews (monthly/quarterly) | Scheduled audits | Catches orphaned permissions |
| Enable access logging | Audit trails | Detect unauthorized access attempts |

<br><br>

## 3. Activity 2: Decrypt an Encrypted Message

**Objective:** Use Linux commands to decrypt encrypted data and recover hidden messages.

### Decryption Process Flow
| Step | Task | 
|------|------| 
| Step 1: | Navigate directories (ls, cd) |
| Step 2: | Read instructions (cat README.txt) |
| Step 3: | Find hidden files (ls -a) |
| Step 4: | Decrypt Caesar cipher (tr command) |
| Step 5: | Decrypt AES file (openssl) |
| Step 6: | View recovered content (cat) |


### Key Commands Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `ls` | List directory contents | `ls` |
| `ls -a` | List all files (including hidden) | `ls -a` |
| `cat [file]` | Display file contents | `cat README.txt` |
| `cd [directory]` | Change directory | `cd caesar` |
| `tr [set1] [set2]` | Translate/transform characters | `tr "d-za-cD-ZA-C" "a-zA-Z"` |
| `openssl aes-256-cbc -d` | Decrypt AES-256-CBC | See below |
| `cat [file]` | View recovered content | `cat Q1.recovered` |

### Caesar Cipher Decryption

```bash
# Caesar cipher with left shift of 3
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```

How it works:

| Cipher | Plaintext | Explanation |
|--------|-----------|-------------|
| d | a | Shift back by 3 |
| e | b | Shift back by 3 |
| f | c | Shift back by 3 |
| a | x | Wrap-around shift |	


OpenSSL AES-256-CBC Decryption
```bash
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```

| Parameter | Meaning |
|-----------|---------|
| `aes-256-cbc` | AES algorithm, 256-bit key, CBC mode |
| `-pbkdf2` | Password-Based Key Derivation Function 2 |
| `-a` | Base64 encode/decode |
| `-d` | Decrypt mode |
| `-in [file]` | Input encrypted file |
| `-out [file]` | Output decrypted file |
| `-k [password]` | Decryption password |


Commands Executed
```bash
# Navigate and explore
ls
cat README.txt
cd caesar
ls -a

# Decrypt Caesar cipher
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"

# Decrypt AES file
cd ~
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
cat Q1.recovered
```


Encryption Types Compared
| Type | Example | Strength | Use Case |
|------|---------|----------|----------|
| Classical cipher | Caesar cipher (shift) | Very weak | Historical/educational |
| Symmetric encryption | AES-256-CBC | Strong | Bulk data encryption |
| Asymmetric encryption | RSA | Strong | Key exchange, digital signatures |



Reflection - Activity 2
This activity strengthened understanding of encryption and decryption processes. It demonstrated how classical ciphers (Caesar) and modern encryption (AES-256-CBC) can be reversed using correct tools and commands, reinforcing the importance of protecting sensitive data.

<br><br>

## 4. Activity 3: Create Hash Values
**Objective:** Generate and compare hash values to verify file integrity.

| Hash Function Properties | Description |
|-------------------------|-------------|
| Deterministic | Same input always produces same hash |
| One-way | Cannot reverse hash to original input |
| Collision-resistant | Two different inputs unlikely to produce same hash |
| Avalanche effect | Small change in input → completely different hash |


SHA-256 Hash Example
```
Input: "Hello World"
SHA-256: a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e

Input: "Hello World " (added space)
SHA-256: 1a460c5b0ebcaf175154be8b5472fca1a8d5d80c7e32f72d1f68e6be4175a25a
```

Commands Executed
```bash
# Display file contents
cat file1.txt
cat file2.txt

# Generate SHA-256 hashes
sha256sum file1.txt
sha256sum file2.txt

# Save hashes to files
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash

# View saved hashes
cat file1hash
cat file2hash

# Compare hashes
cmp file1hash file2hash
```


Hash Comparison Visualization
- File 1 Process: file1.txt → sha256sum → file1hash  
- File 1 Process: file2.txt → sha256sum → file2hash  
- file1hash vs file2hash → cmp → "Different - No match"


Findings
| Observation | Implication |
|-------------|-------------|
| Files appeared identical when viewed with cat | Human-readable content was the same |
| Hash values were different | Hidden differences exist (whitespace, line endings, metadata) |
| cmp reported files differ | Security tool detected tampering |


Why Hashes Differ for Seemingly Identical Files
| Hidden Difference | Example |
|------------------|---------|
| Whitespace | Trailing space, tab vs. space |
| Line endings | LF (Unix) vs. CRLF (Windows) |
| Encoding | UTF-8 vs. ASCII |
| Hidden characters | Null bytes, special characters |
| Metadata | File timestamps (some hash algorithms include) |


Integrity Verification Workflow
Original File → sha256sum → Original Hash  
Received File → sha256sum → New Hash  

Original Hash vs New Hash → Compare  
Result:  
- Match → Intact 
- Mismatch → Tampered 


Reflection - Activity 3
This activity highlighted the importance of hashing for ensuring data integrity. It showed how security professionals can detect even the smallest modifications to files, which is critical for identifying tampering or malicious changes.

Key takeaway: Even a single character difference (including invisible characters) produces a completely different hash value.

<br><br>

## 5. Activity 4: Improve Authentication, Authorization, and Accounting (AAA)
**Objective:** Analyze an access control incident and recommend improvements.

Incident Data
Employee Record:

Name	Role	Status	Authorization	IP Address	End Date
Robert Taylor Jr.	Legal attorney	Contractor	Admin	152.207.255.255	12/27/2019
Log Evidence:
```
Event Type: Information
Date: 10/03/2023
Time: 8:29:57 AM
User: Legal\Administrator
IP Address: 152.207.255.255
Action: Payroll event added (FAUX_BANK)
```


### Incident Timeline

| Date | Event Description | Notes |
|------|-------------------|-------|
| 2019-12-27 | Contractor contract ends                               | Account should be deactivated   |
| 2023-10-03 | Payroll event executed using same account              | Unauthorized / suspicious use   |
| Current    | Account still active with admin privileges             | Critical security risk ⚠️       |


Issues Identified
| # | Issue | Severity | Risk |
|---|-------|----------|------|
| 1 | Contractor account active 4 years after contract end | 🔴 Critical | Unauthorized access |
| 2 | User had administrative privileges | 🔴 Critical | Excessive permissions |
| 3 | No automatic account expiration | 🟠 High | Orphaned accounts |
| 4 | Payroll action from non-payroll role | 🔴 Critical | Segregation of duties violation |


Account Lifecycle Management Gaps

| Lifecycle Stage | Status | Description |
|-----------------|--------|-------------|
| Provisioning | ✓ | Account created |
| Active | ✓ | Account in use |
| Review | ✗ | No periodic review |
| De-provisioning | ✗ | Account never removed |


Recommendations
| Priority | Recommendation | Implementation | MITRE ATT&CK Mapping |
|----------|---------------|----------------|----------------------|
| Critical | Implement automatic account expiration | Set end date in identity management system | T1078 - Valid Accounts |
| Critical | Apply RBAC with limited privileges | Legal attorneys should not have payroll access | T1098 - Account Manipulation |
| High | Enable MFA for all admin accounts | Require second factor for sensitive actions | T1557 - Man-in-the-Middle |
| High | Conduct quarterly access reviews | Automated certification campaigns | TA0006 - Credential Access |
| Medium | Enable logging for all admin actions | SIEM integration | TA0007 - Discovery |


Least Privilege Applied to Robert Taylor Jr.
| Before | After |
|--------|-------|
| Legal\Administrator | Legal\Legal_Reviewer |
| Access to payroll system | Access to legal documents only |
| Admin privileges | Read-only for most systems |
| Active indefinitely | Account expires with contract |


Reflection - Activity 4
This activity highlighted the importance of proper account lifecycle management and access control enforcement. Retaining active accounts for former employees and granting excessive privileges significantly increases security risks.

Key takeaways:
- Accounts must be de-provisioned immediately upon employment termination
- Administrative privileges should be rare and tightly controlled
- Segregation of duties prevents single-user abuse
- Regular access reviews catch orphaned accounts

<br><br>

## 6. AAA Framework Summary
| Component | Definition | Controls Implemented |
|-----------|------------|----------------------|
| Authentication | Verifying user identity | MFA, strong passwords |
| Authorization | Determining access rights | RBAC, least privilege |
| Accounting | Tracking user actions | Logging, audit trails |


Security Controls Comparison
| Control | Before Incident | After Recommendations |
|---------|-----------------|----------------------|
| Account expiration | Manual (forgotten) | Automatic |
| Access reviews | None | Quarterly |
| MFA | Not enabled | Required for admin |
| Privilege level | Admin (excessive) | Role-appropriate |
| Segregation of duties | Violated | Enforced |

<br><br>

## 7. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| Least privilege implementation | Analyzed data leak; recommended role-based restrictions |
| NIST framework application | Applied NIST SP 800-53 AC-6 |
| Encryption/decryption | Used Caesar cipher and AES-256-CBC decryption |
| Hash generation | Generated SHA-256 hashes with sha256sum |
| File integrity verification | Compared hashes using cmp |
| Access control analysis | Identified unauthorized payroll access |
| Account lifecycle management | Recommended automatic expiration |
| Security control recommendations | Proposed MFA, RBAC, access reviews |

<br><br>

## 8. Tools and Concepts Used
| Tool/Concept | Application |
|--------------|-------------|
| NIST SP 800-53 AC-6 | Least privilege framework |
| Caesar cipher | Classical encryption decryption |
| OpenSSL (AES-256-CBC) | Modern symmetric decryption |
| SHA-256 | Cryptographic hashing |
| sha256sum | Linux hash generation |
| cmp | File comparison |
| RBAC | Role-based access control |
| MFA | Multi-factor authentication |
| AAA framework | Authentication, Authorization, Accounting |

<br><br>

## 9. Reflection - Full Lab
This lab provided practical experience in securing data through multiple approaches: data handling policies, encryption, hashing, and access control mechanisms.

Key takeaways from each activity:

| Activity | Key Insight |
|----------|--------------|
| Activity 1 | Least privilege requires both policy AND technical enforcement |
| Activity 2 | Encryption is reversible with proper keys/tools |
| Activity 3 | Hashes detect invisible tampering (whitespace, encoding) |
| Activity 4 | Account lifecycle management is often the weakest link |
| Demonstrates | Practical data protection skills including encryption, hashing, access control, and security policy implementation. |

<br><br>

## 10. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Least Privilege | Users get minimum access necessary for their role |
| NIST SP 800-53 | Security and privacy controls catalog |
| Caesar cipher | Classical substitution cipher shifting letters |
| AES-256-CBC | Advanced Encryption Standard, 256-bit key, Cipher Block Chaining mode |
| OpenSSL | Open-source cryptography toolkit |
| SHA-256 | Secure Hash Algorithm (256-bit output) |
| Hash | Fixed-size output from hash function |
| cmp | Linux command to compare files byte by byte |
| RBAC | Role-Based Access Control |
| MFA | Multi-Factor Authentication |
| AAA | Authentication, Authorization, Accounting |
| Segregation of duties | Single user cannot perform conflicting actions |
| Orphaned account | Active account without a valid user |

<br><br>

## 11. Command Quick Reference
Encryption/Decryption
```bash
# Generate SHA-256 hash
sha256sum filename.txt

# Compare files
cmp file1 file2

# Caesar cipher decryption (left shift 3)
cat encrypted.txt | tr "d-za-cD-ZA-C" "a-zA-Z"

# AES-256-CBC decryption
openssl aes-256-cbc -pbkdf2 -a -d -in encrypted.aes -out decrypted.txt -k password

# AES-256-CBC encryption
openssl aes-256-cbc -pbkdf2 -a -e -in plaintext.txt -out encrypted.aes -k password
```


File Navigation
```bash
ls -a          # List all files including hidden
cat file.txt   # Display file contents
cd directory   # Change directory
```








<br><br><br><br>

---

<br><br><br><br>







# Lab 11: Threats to Asset Security

**Focus Area:** Threat Identification | Social Engineering | Phishing Analysis | Threat Modeling  
**Frameworks Applied:** PASTA (Process for Attack Simulation and Threat Analysis)  
**Skills:** Email Header Analysis | Phishing Detection | Social Engineering Tactics | Threat Actor Profiling | Attack Modeling | Risk Assessment | Security Control Recommendations  

<br><br>

## Objective

Identify and analyze threats to organizational assets, with particular emphasis on social engineering attacks and application security. This lab demonstrates practical skills in:

1. Detecting and analyzing phishing emails to prevent social engineering attacks
2. Applying the PASTA threat model to assess risks and vulnerabilities in software applications
3. Implementing professional procedures for documenting and mitigating potential security threats

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Key Tools/Concepts | Security Relevance |
|----------|-------|-------------------|-------------------|
| 1 | Phishing email analysis | Email headers, URL inspection, social engineering tactics | Prevent credential theft and malware installation |
| 2 | PASTA threat modeling | 7-stage framework, attack trees, risk analysis | Proactive security assessment before deployment |

<br><br>

## 2. Activity 1: Filter Malicious Emails

**Objective:** Detect and analyze phishing emails to prevent social engineering attacks.

### Scenario

As a security analyst at **Imaginary Bank**, investigate a suspicious spear phishing email received by an executive. The email claimed the executive was added to a collaboration group called "Execs" and prompted them to download "ExecuTalk" software.

### Email Header Analysis – Indicators of Phishing

| Indicator | Suspicious Element | Why It's Malicious |
|-----------|-------------------|-------------------|
| **Sender domain** | `imaginarybank@gmail.org` | Official domain should be `@imaginarybank.com` |
| **Subject line** | "RE: You are been added to an ecsecutiv's groups" | Misspelling ("ecsecutiv's"), poor grammar |
| **Reply-to address** | (Not shown - would likely differ) | Often different from sender address |
| **Return-Path** | (Not shown - would likely differ) | Should match legitimate organizational domain |

### Email Body Analysis – Legitimate Appearance Tactics

| Tactic | Example in Email | Purpose |
|--------|-----------------|---------|
| **Platform compatibility** | Download options for Mac, Windows, Android | Appears legitimate and well-developed |
| **Official sounding group** | "Execs" group | Creates sense of internal authority |
| **Branding** | "ExecuTalk© All rights reserved" | Adds fake legitimacy |
| **Urgency** | "This invitation will expire in 48 hours" | Pressures quick action without thinking |
| **Call to action** | Prominent download buttons | Directs user to malicious site |

### Malicious Indicator – The URL

| Element | Finding | Verdict |
|---------|---------|---------|
| **Linked URL** | Not associated with organization's official domain | 🔴 **Malicious** |
| **Expected domain** | `*.imaginarybank.com` | N/A |
| **Actual destination** | Unknown external domain | Credential harvesting page |

### Phishing Email Anatomy
```
From: imaginarybank@gmail.org
To: executive@imaginarybank.com
Subject: RE: You are been added to an ecsecutiv's groups

Dear Executive,

You have been added to the Execs collaboration group.
Download ExecuTalk to join:

[Download for Mac] [Download for Windows]
[Download for Android]

This invitation will expire in 48 hours!

ExecuTalk© All rights reserved. 
```

#### Phishing Email Explaination

| Component | Indicator | Why It’s Suspicious |
|-----------|-----------|---------------------|
| From | imaginarybank@gmail.org | Mismatched / fake domain |
| Subject | "ecsecutiv's groups" | Spelling/grammar errors |
| Message | Generic greeting | Lack of personalization |
| Links | Download buttons | Potential malware delivery |
| Urgency | "Expires in 48 hours" | Pressures user to act quickly |
| Branding | ExecuTalk© | Fake or spoofed branding |
| Outcome | Login page | Credential harvesting |


#### Phishing Email Analysis

| Stage | Attack Technique | Security Weakness Exploited |
|-------|------------------|-----------------------------|
| Email Spoofing | Fake sender domain | Lack of email filtering |
| Social Engineering | Urgency + authority | User awareness gap |
| Delivery | Malicious links/downloads | No link inspection |
| Exploitation | Fake login page | Credential reuse / weak MFA |
| Impact | Account compromise | Lack of monitoring |

**Attack Type:** Phishing (Social Engineering)  
**Key Indicators:**
- Suspicious sender domain
- Spelling/grammar mistakes
- Urgent language
- Unverified download links

**Mitigation:**
- User awareness training
- Email filtering (SPF, DKIM, DMARC)
- Multi-Factor Authentication (MFA)


### Threat Actor Tactics – Social Engineering Techniques

| Technique | Example in Email | Psychological Principle |
|-----------|-----------------|----------------------|
| **Urgency/Pressure** | "Invitation will expire in 48 hours" | Scarcity – act now or lose opportunity |
| **Authority/Trust** | Pretended to come from board of bank | Authority – comply with perceived superior |
| **Familiarity** | "Execs" group name | Liking/familiarity – appears internal |
| **Reciprocity** | "You have been added" (unsolicited) | Reciprocity – feel obliged to respond |

### Risk Assessment – Consequences of Successful Attack

| Impact Area | Potential Consequence | Severity |
|-------------|----------------------|----------|
| **Credential compromise** | Executive credentials stolen → access to corporate systems | 🔴 Critical |
| **Malware installation** | Ransomware, keyloggers, backdoors | 🔴 Critical |
| **Data breach** | Customer banking information exposed | 🔴 Critical |
| **Financial loss** | Unauthorized transfers, fraud | 🔴 Critical |
| **Reputational damage** | Loss of customer trust, regulatory fines | 🟠 High |

### Recommended Actions

| Priority | Action | Responsible Party |
|----------|--------|-------------------|
| **Immediate** | Block sender domain (`@gmail.org`) | Email Security Admin |
| **Immediate** | Add email gateway rules to quarantine similar emails | Email Security Admin |
| **Short-term** | Alert employees about this phishing attempt | Security Awareness Team |
| **Short-term** | Report incident to internal security team | Security Analyst |
| **Ongoing** | Log incident for threat intelligence | SOC Team |

### Preventive Measures – Lessons Learned

| Measure | Implementation | Purpose |
|---------|----------------|---------|
| **Employee training** | Regular phishing simulations | Recognize social engineering tactics |
| **SPF, DKIM, DMARC** | Email authentication protocols | Prevent domain spoofing |
| **Email security tools** | Sandboxing, link rewriting | Filter malicious attachments/URLs |
| **Reporting mechanism** | "Report Phishing" button | Encourage user reporting |

### Email Authentication Protocols

| Protocol | Purpose | How It Helps |
|----------|---------|--------------|
| **SPF** | Specifies authorized sending servers | Prevents forged sender addresses |
| **DKIM** | Digital signature on emails | Verifies email wasn't altered |
| **DMARC** | Policy for handling failed SPF/DKIM | Tells receivers what to do with suspicious emails |

<br><br>

## 3. Activity 2: Apply the PASTA Threat Model Framework

**Objective:** Assess risks and vulnerabilities in a software application using the PASTA framework.

### Scenario

As part of a security team evaluating a new mobile app for sneaker enthusiasts, assess risks and vulnerabilities before launch using the PASTA framework.

### Application Assumptions & Scope

| Aspect | Details |
|--------|---------|
| **Platforms** | iOS and Android devices |
| **Payment processing** | Third-party APIs |
| **Data storage** | Central SQL database |
| **User authentication** | Member profiles (internal or external accounts) |
| **Security requirement** | PCI-DSS compliance for payment handling |

### PASTA Framework – 7 Stages Overview

| Stage | Name | Focus | Output |
|-------|------|-------|--------|
| I | Define Business & Security Objectives | What must be protected? | Security requirements |
| II | Define Technical Scope | What technologies are used? | Asset inventory |
| III | Decompose Application | How does data flow? | Architecture diagram |
| IV | Threat Analysis | What could go wrong? | Threat list |
| V | Vulnerability Analysis | Where are weaknesses? | Vulnerability list |
| VI | Attack Modeling | How could attacks happen? | Attack trees |
| VII | Risk Analysis & Impact | What are the priorities? | Risk mitigation plan |

<br><br>

### Stage I: Define Business and Security Objectives

| Objective Type | Specific Requirement |
|----------------|---------------------|
| **Business** | Users can create member profiles internally or via external accounts |
| **Business** | App must process financial transactions securely |
| **Security** | Ensure PCI-DSS compliance for payment handling |
| **Security** | Protect user PII and payment data |

<br><br>

### Stage II: Define Technical Scope

**Technologies Used:**

| Technology | Purpose |
|------------|---------|
| **API** | Communication between app, payment processor, and database |
| **PKI** | Public Key Infrastructure for secure key exchange |
| **AES** | Encryption for data at rest |
| **SHA-256** | Hashing for password storage and integrity |
| **SQL** | Database queries for user and inventory data |

**Prioritized Asset:** **APIs** – handle sensitive data between multiple systems, creating larger attack surface

<br><br>

### Stage III: Decompose Application

**Data Flow Diagram:**
- User → Mobile App → API Gateway → Payment API → Bank  
- User → SQL Database (user data, inventory)
- User → Product Search → Database Query


**Data Flow Path Analyzed:** `User ↔ Product Search Process ↔ Database`

| Component | Function | Trust Boundary |
|-----------|----------|----------------|
| User | Initiates search requests | Untrusted |
| Mobile App | Displays interface | Semi-trusted |
| API Gateway | Routes requests | Trusted (internal) |
| SQL Database | Stores inventory data | Trusted (internal) |

<br><br>

### Stage IV: Threat Analysis

**Identified Threats:**

| Threat Category | Specific Threat | Target |
|-----------------|-----------------|--------|
| **Injection attacks** | SQL injection via search queries | Database |
| **Session hijacking** | Cookie theft, token replay | User sessions |
| **Broken authentication** | Weak password policies | User accounts |
| **API abuse** | Rate limiting bypass | API endpoints |

**Threat Actor Profiles:**

| Actor Type | Motivation | Capability | Target |
|------------|------------|------------|--------|
| **Internal - Disgruntled employee** | Revenge, financial gain | High (system access) | Database, payment data |
| **Internal - Developer with excessive access** | Curiosity, mistake | High (code access) | Backdoors, credentials |
| **External - Hacker** | Financial gain, notoriety | Medium-High | Payment data, credentials |
| **External - Competitor** | Business intelligence | Medium | Inventory, user base |

<br><br>

### Stage V: Vulnerability Analysis

**Identified Vulnerabilities:**

| Vulnerability | Affected Component | Root Cause |
|---------------|-------------------|------------|
| SQL injection risk | Database queries | Lack of prepared statements |
| Broken API tokens | API authentication | Weak session management |
| Weak password policy | User authentication | No complexity requirements |
| Missing input validation | Search function | User input not sanitized |

**Likelihood and Impact Assessment:**

| Vulnerability | Likelihood | Impact | Risk Level |
|---------------|------------|--------|------------|
| SQL Injection | High (3) | Critical (3) | **9 (Critical)** |
| Session Hijacking | Medium (2) | High (3) | **6 (High)** |
| Weak Passwords | High (3) | Medium (2) | **6 (High)** |
| Missing Input Validation | Medium (2) | Medium (2) | **4 (Medium)** |

<br><br>

### Stage VI: Attack Modeling

**Attack Tree – Compromise User Data**

| Main Attack Vector | Technique | Method | Impact | Mitigation |
|--------------------|-----------|--------|--------|------------|
| SQL Injection | Injection | UNION-based | Database data exposure | Input validation, prepared statements |
| SQL Injection | Injection | Boolean-based / Blind | Database data exposure | Input validation, prepared statements |
| Session Hijacking | Exploitation | Cross-Site Scripting (XSS) | Session takeover | HTTPS, secure cookies, CSP |
| Session Hijacking | Network Attack | Packet sniffing | Session takeover | HTTPS, secure cookies, CSP |
| Credential Theft | Password Attack | Brute force | Account compromise | MFA, rate limiting, password policies |
| Credential Theft | Credential Reuse | Credential stuffing | Account compromise | MFA, rate limiting, password policies |


**Threat Modeling Technique:** Attack Tree  
**Goal:** Identify multiple paths to compromise user data  

**Key Risks:**
- Injection vulnerabilities
- Weak session management
- Poor authentication controls


**Attack Vector Analysis:**

| Attack Vector | Precondition | Difficulty | Impact |
|---------------|--------------|------------|--------|
| SQL Injection | Un-sanitized user input | Medium | Critical |
| Session Hijacking | Insecure token handling | Medium | High |
| Brute Force | No rate limiting | Low | Medium |
| Credential Stuffing | Password reuse | Low | Medium |

<br><br>

### Stage VII: Risk Analysis and Impact

**Recommended Security Controls:**

| Control Category | Specific Control | Threat Mitigated |
|-----------------|-----------------|------------------|
| **Cryptographic** | SHA-256 hashing for passwords | Credential theft |
| **Access Control** | Principle of least privilege | Insider threats |
| **Authentication** | Two-factor authentication (2FA) | Credential theft |
| **API Security** | Rate limiting and monitoring | API abuse, DoS |
| **Input Validation** | Prepared statements | SQL injection |
| **Session Management** | Secure cookie flags, short timeouts | Session hijacking |
| **Incident Response** | Documented response procedures | All threats |

**Additional Security Controls:**

| Control | Implementation | Priority |
|---------|----------------|----------|
| Regular vulnerability scans | Weekly automated scans | High |
| Penetration testing | Quarterly (or after major changes) | High |
| Secure coding training | Developer onboarding + annual refresher | Medium |
| Code review process | Mandatory for all pull requests | Medium |
| Security logging | Centralized SIEM integration | High |

<br><br>

### PASTA Stage Summary Table

| Stage | Key Findings |
|-------|--------------|
| I (Objectives) | PCI-DSS compliance required; protect payment data |
| II (Technical Scope) | APIs prioritized (highest attack surface) |
| III (Decompose) | Data flows through API → Payment → Database |
| IV (Threats) | SQL injection, session hijacking identified |
| V (Vulnerabilities) | Prepared statements missing; weak session management |
| VI (Attack Modeling) | Attack tree shows multiple compromise paths |
| VII (Risk Analysis) | Critical risk: SQL injection (score 9) |

<br><br>

## 4. Threat Actor Profile Summary

| Actor Type | Motivation | Target | Common Techniques |
|------------|------------|--------|------------------|
| **Phishing attacker** | Credential theft | Executives, privileged users | Spear phishing, urgency tactics |
| **Internal threat** | Revenge, financial gain | Database, payment systems | Excessive privileges, abuse of access |
| **External hacker** | Financial gain | Payment data, user accounts | SQL injection, API abuse |
| **Competitor** | Business intelligence | Inventory, user base | Reconnaissance, scraping |

<br><br>

## 5. Skills Demonstrated

| Skill | Application in Lab |
|-------|-------------------|
| Email header analysis | Identified spoofed sender domain |
| Phishing indicator identification | Found misspellings, urgency tactics, suspicious URLs |
| Social engineering tactic analysis | Recognized authority, urgency, familiarity techniques |
| Risk assessment | Evaluated consequences of successful phishing |
| PASTA framework application | Applied all 7 stages to mobile app assessment |
| Threat actor profiling | Identified internal and external threat actors |
| Attack modeling | Created attack tree for data compromise |
| Vulnerability analysis | Identified SQL injection, session hijacking risks |
| Security control recommendations | Proposed 2FA, rate limiting, prepared statements |

<br><br>

## 6. Tools and Concepts Used

| Tool/Concept | Application |
|--------------|-------------|
| PASTA Framework | 7-stage threat modeling |
| Attack trees | Visualized attack paths to compromise data |
| Social engineering principles | Authority, urgency, familiarity, reciprocity |
| Email authentication (SPF/DKIM/DMARC) | Preventive measures for phishing |
| SQL injection | Identified as critical vulnerability |
| Session hijacking | Identified as high-risk threat |
| 2FA | Recommended authentication control |
| Rate limiting | Recommended API protection |

<br><br>

## 7. Reflection

Through these two activities, I enhanced practical skills in asset security and threat analysis.

**Activity 1 takeaways:**
- Phishing emails often combine multiple social engineering tactics (urgency + authority + familiarity)
- Email header analysis is as important as content analysis
- The URL is the most reliable malicious indicator
- Preventive measures (SPF, DKIM, DMARC) are essential but user training remains critical

**Activity 2 takeaways:**
- PASTA provides structured approach to threat modeling (not just brainstorming)
- Decomposing the application reveals data flow paths that might otherwise be overlooked
- Attack trees help visualize how multiple attack paths can achieve the same objective
- Risk scoring (Likelihood × Impact) guides prioritization

**Demonstrates:** Threat identification, social engineering detection, structured threat modeling, and proactive security assessment.

<br><br>

## 8. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| **PASTA** | Process for Attack Simulation and Threat Analysis – 7-stage threat modeling framework |
| **Spear phishing** | Targeted phishing against specific individual or organization |
| **Social engineering** | Psychological manipulation to trick users into security mistakes |
| **SPF** | Sender Policy Framework – email authentication protocol |
| **DKIM** | DomainKeys Identified Mail – email digital signature |
| **DMARC** | Domain-based Message Authentication, Reporting & Conformance |
| **Attack tree** | Hierarchical diagram showing attack paths to achieve objective |
| **Session hijacking** | Stealing user session token to impersonate legitimate user |
| **SQL injection** | Injecting malicious SQL queries through user input |
| **Threat actor profile** | Description of attacker's motivation, capability, and targets |
| **PCI-DSS** | Payment Card Industry Data Security Standard |
| **API** | Application Programming Interface |

<br><br>

## 9. PASTA Quick Reference – 7 Stages

| Stage | Key Question | Output |
|-------|--------------|--------|
| I | What must we protect? | Security objectives |
| II | What technologies are used? | Asset list |
| III | How does data flow? | Architecture diagram |
| IV | What could go wrong? | Threat list |
| V | Where are we weak? | Vulnerability list |
| VI | How could attacks happen? | Attack trees |
| VII | What do we fix first? | Risk mitigation plan |

<br><br>

## 10. Phishing Email Checklist for Analysts

| Check | What to Look For | Suspicious Indicators |
|-------|-----------------|----------------------|
| () | Sender email address | Different domain, misspellings |
| () | Subject line | Grammar errors, urgency words |
| () | Greeting | Generic ("Dear User") vs. personalized |
| () | Links | Hover to see actual URL; check domain |
| () | Attachments | Unexpected files (.exe, .zip, .js) |
| () | Urgency | "Act now", "48 hours", "immediate action" |
| () | Request | Asking for credentials, payment, personal info |
| () | Branding | Logo quality, copyright notices, legal language |












<br><br><br><br>

---

<br><br><br><br>













# Lab 12: Vulnerabilities in Systems – Identify the Attack Vectors of a USB Drive

**Focus Area:** Physical Media Vulnerabilities | Social Engineering | USB Baiting Attacks  
**Attack Type Analyzed:** USB Drive Baiting / Drop Attack   
**Skills:** Attack Vector Identification | Attacker Mindset Analysis | Risk Assessment | Mitigation Strategy Development | Physical Security Controls  

<br><br>

## Objective

Assess the potential security risks of an unknown USB drive and analyze how sensitive information can be exploited by an attacker.

<br><br>

## 1. Scenario Overview

A USB drive is found containing a mixture of personal and work-related files belonging to **Jorge Bailey**, the Human Resource Manager at **Rhetorical Hospital**.

| Aspect | Details |
|--------|---------|
| **Device** | Unknown USB drive |
| **Owner** | Jorge Bailey, HR Manager |
| **Organization** | Rhetorical Hospital |
| **File types** | Personal (family/pet photos) + Work (new hire letters, employee shift schedules) |

<br><br>

## 2. USB Drive Content Analysis

### File Type Breakdown

| Category | Content Examples | Sensitivity Level | Risk if Exposed |
|----------|-----------------|-------------------|-----------------|
| **Personal files** | Family photos, pet photos | Internal-only | Social engineering material |
| **Work files - HR** | New hire letters | Restricted | PII exposure |
| **Work files - Operations** | Employee shift schedules | Confidential | Operational pattern disclosure |

### Security Concern – Data Co-mingling

| Issue | Risk |
|-------|------|
| Personal + work files on same device | If device is lost/stolen, both personal and organizational data exposed |
| No encryption | Anyone with USB access can read all files |
| No access controls | No password or authentication required |

> **Critical observation:** Storing personal and sensitive work information on the same device significantly increases the risk of accidental exposure or exploitation.

<br><br>

## 3. Attacker Mindset Analysis

### How an Attacker Thinks after found an USB Drive
- "What information can I extract from this?" 
- "How can I use this to my advantage?" 
- "What systems can I access?" 
- "Who can I target with this information?" 


### Information Extraction – Work Documents

| Document Type | Information Revealed | Potential Attack Use |
|---------------|---------------------|---------------------|
| New hire letters | Employee names, addresses, SSNs (potentially) | Identity theft, spear phishing |
| Shift schedules | Employee work patterns, when building is less staffed | Physical intrusion, targeted timing |
| Timesheets | Employee IDs, department information | Credential harvesting |

### Information Extraction – Personal Files

| File Type | Information Revealed | Potential Attack Use |
|-----------|---------------------|---------------------|
| Family photos | Names of family members, faces | Personal social engineering |
| Pet photos | Pet names (often used as passwords) | Password guessing |
| Vacation photos | Travel patterns (home empty) | Physical burglary |

### Attacker Objectives

| Objective | Method | Target |
|-----------|--------|--------|
| **Network access** | Infect USB with malware, wait for insertion | Hospital network |
| **Credential theft** | Keylogger on USB | Employee passwords |
| **Ransomware deployment** | Auto-executing malware | Hospital data/files |
| **Identity theft** | Extract PII from HR documents | Employees |
| **Spear phishing** | Use personal info to craft convincing emails | Jorge or his family |

<br><br>

## 4. USB Baiting Attack Chain

### How USB Drop Attacks Work

| Step | Actor | Action | Outcome | Security Control Missing |
|------|-------|--------|---------|--------------------------|
| 1 | Attacker | Prepares malicious USB | Malware ready | Device control / malware scanning |
| 2 | Attacker | Drops USB in target location | Device discovered | Physical security awareness |
| 3 | Employee | Picks up and inserts USB | Malware triggered | USB port restriction |
| 4 | System | Executes malicious payload | System compromised | Endpoint detection (EDR) |
| 5 | Network | Malware spreads | Full network compromise | Monitoring & incident response | 


### Why USB Baiting Works (Psychology)

| Psychological Factor | Why It's Effective |
|---------------------|-------------------|
| **Curiosity** | "What's on this USB?" |
| **Opportunity** | Free device, perceived value |
| **Helpfulness** | "Maybe someone lost this – I should check for owner info" |
| **Convenience** | Need a USB for work, found one available |
| **Lack of awareness** | "How dangerous can a USB be?" |

<br><br>

## 5. Risk Assessment

### Attack Scenarios & Impact

| Scenario | Likelihood | Impact | Risk Level |
|----------|------------|--------|------------|
| Malicious USB with AutoPlay malware | Medium | Critical | **High** |
| Sensitive data extraction from USB | High | High | **High** |
| Employee inserts USB into personal computer | Medium | Medium | **Medium** |
| USB sold/given to third party | Low | High | **Medium** |

### Potential Malware Types on Malicious USB

| Malware Type | Function | Impact |
|--------------|----------|--------|
| **Ransomware** | Encrypts files, demands payment | Operational shutdown |
| **Keylogger** | Records keystrokes (passwords) | Credential theft |
| **Spyware** | Monitors activity, exfiltrates data | Data breach |
| **Backdoor** | Remote access for attacker | Persistent compromise |
| **Worm** | Self-propagates across network | Widespread infection |

### Consequences of Successful Attack

| Consequence | Description | Severity |
|-------------|-------------|----------|
| **Network compromise** | Attacker gains foothold in hospital network | 🔴 Critical |
| **Data breach** | Patient/employee PII exposed | 🔴 Critical |
| **Ransomware** | Hospital operations disrupted | 🔴 Critical |
| **Identity theft** | Employee identities stolen | 🟠 High |
| **Regulatory fines** | HIPAA violations possible | 🟠 High |

<br><br>

## 6. Mitigation Strategies

### Control Categories

| Control Type | Definition | Examples |
|--------------|------------|----------|
| **Technical** | Technology-based controls | Disable AutoPlay, antivirus, device control |
| **Operational** | Process-based controls | Routine scans, incident response |
| **Managerial** | Policy/training controls | Employee awareness, acceptable use policy |

### Recommended Mitigations

| Priority | Control Type | Measure | Purpose |
|----------|--------------|---------|---------|
| **High** | Technical | Disable AutoPlay/AutoRun on all company PCs | Prevent automatic malware execution |
| **High** | Technical | Implement USB device control (allowlisting) | Only approved USBs can be used |
| **High** | Managerial | Employee security awareness training | Teach risks of unknown USBs |
| **Medium** | Operational | Routine antivirus scans on all endpoints | Detect malware if inserted |
| **Medium** | Technical | Endpoint Detection and Response (EDR) | Monitor for suspicious USB activity |
| **Medium** | Managerial | Clear policy on personal USB drives | Prohibit personal/work data mixing |
| **Low** | Operational | Physical security (lost & found procedure) | Proper handling of found devices |

### Security Controls Matrix

| Threat | Technical Control | Operational Control | Managerial Control |
|--------|------------------|---------------------|---------------------|
| Malicious USB insertion | Disable AutoPlay, Device Control | Incident response plan | Acceptable use policy |
| Data exposure from lost USB | Encryption | Asset tracking | Data handling policy |
| Employee inserting unknown USB | USB port blocking | Reporting procedure | Security awareness training |
| Malware spread | Antivirus, EDR | Network segmentation | Security policy enforcement |

<br><br>

## 7. Data Protection Best Practices

### For Organizations

| Practice | Implementation |
|----------|----------------|
| **Encrypt all company USBs** | BitLocker To Go, LUKS |
| **Implement DLP (Data Loss Prevention)** | Block unauthorized USB transfers |
| **Regular audits** | Review USB usage logs |
| **Lost & found procedure** | Destroy or securely wipe found USBs |

### For Employees

| Practice | Why It Matters |
|----------|----------------|
| **Never use unknown USBs** | Could contain malware |
| **Separate personal and work data** | Limits exposure if one is compromised |
| **Report lost USBs immediately** | Enable quick revocation/response |
| **Use encrypted USBs for work** | Protects data if lost |
| **Don't share USBs between people** | Maintains accountability |

<br><br>

## 8. Incident Response – Found USB Drive

### Proper Handling Procedure

| Step | Action | Rationale |
|------|--------|-----------|
| 1 | **DO NOT insert the USB** | Prevents potential malware execution |
| 2 | Report to security team | Professional handling required |
| 3 | Security team examines in isolated environment | Safe analysis without network risk |
| 4 | If legitimate lost device, return to owner after verification | Prevents data exposure |
| 5 | If malicious, preserve as evidence | For investigation/legal action |

### What NOT to Do

| Don't | Why It's Dangerous |
|----------|-------------------|
| Inserting into personal computer | No corporate protection |
| Checking for owner info on work PC | Could infect network |
| Sharing with colleagues | Multiplies exposure |
| Throwing away | Evidence lost, no investigation |

<br><br>

## 9. Reflection

This activity highlighted the dangers of seemingly harmless devices like USB drives and how human behavior can be exploited to gain access to sensitive information.

**Key takeaways:**

| Takeaway | Implication |
|----------|-------------|
| Personal + work data on same device | Single point of failure for both personal and organizational security |
| Attacker mindset is different from defender mindset | Attackers look for any information, not just "critical" data |
| Psychological factors (curiosity, helpfulness) are exploited | Technical controls alone are insufficient |
| USB baiting is a social engineering attack, not just technical | Requires awareness training, not just antivirus |

**Reinforced concepts:**
- Separating personal and work-related files
- Maintaining awareness of social engineering tactics
- Applying strict security measures for device usage
- Practicing risk assessment in controlled environments

**Demonstrates:** Attack vector identification, attacker mindset analysis, practical risk assessment, and layered mitigation strategies.

<br><br>

## 10. Skills Demonstrated

| Skill | Application in Lab |
|-------|-------------------|
| Attack vector identification | Identified USB drive as physical attack vector |
| Attacker mindset analysis | Analyzed how attacker would extract/extract value from found USB |
| Information classification | Categorized files by sensitivity and risk |
| Social engineering recognition | Identified psychological tactics exploited in USB baiting |
| Risk assessment | Evaluated likelihood, impact, and consequences |
| Mitigation strategy | Developed technical, operational, and managerial controls |
| Incident response procedure | Outlined proper found USB handling |
| Security control mapping | Mapped controls to threat categories |

<br><br>

## 11. Tools and Concepts Used

| Tool/Concept | Application |
|--------------|-------------|
| USB baiting attack | Analyzed drop attack methodology |
| Attacker mindset | Simulated adversarial thinking |
| AutoPlay/AutoRun | Identified as technical vulnerability |
| Device control | Recommended USB allowlisting |
| Data Loss Prevention (DLP) | Suggested for USB transfer control |
| Encryption | Recommended for lost device protection |
| Social engineering | Analyzed psychological exploitation |

<br><br>

## 12. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| **USB baiting** | Attack where malicious USB drives are intentionally left for victims to find |
| **USB drop attack** | Same as USB baiting – attacker "drops" USB in target area |
| **AutoPlay/AutoRun** | Windows feature that automatically executes programs on inserted media |
| **Device control** | Security feature restricting which USB devices can be used |
| **Baiting** | Social engineering tactic using physical item to lure victims |
| **Data co-mingling** | Mixing personal and work data on same device |
| **PII** | Personally Identifiable Information |
| **Keylogger** | Malware that records keystrokes |
| **Ransomware** | Malware that encrypts files and demands payment |

<br><br>

## 13. USB Security Quick Reference

### Red Flags – Suspicious USB

| Red Flag | What to Do |
|----------|------------|
| Found in parking lot/restroom | Do NOT insert |
| No label or markings | Report to security |
| Appears tampered with | Do NOT insert |
| From unknown source | Destroy or return to IT |

### Green Flags – Safe USB Handling

| Green Flag | Practice |
|------------|----------|
| Company-issued encrypted USB | Acceptable for work use |
| Scanned by IT before use | Best practice |
| Personal USB with only personal data | Acceptable on personal devices only |
| Reported lost USB | Proper procedure |

### Protection Checklist
- Disable AutoPlay on all company devices
- Implement USB device allowlisting
- Encrypt all company-issued USBs
- Employee security awareness training (including USB risks)
- Clear policy on personal USB use
- Lost & found procedure for found devices
- Regular antivirus scans
- Monitor USB usage logs


<br><br>

## 14. Attack Scenario – Complete Chain
### USB Baiting Attack Chain

#### Phase 1: Preparation
Attacker creates a malicious USB containing:
- AutoRun malware
- Keylogger
- Fake file (e.g., "employee_salaries.xlsx") as a lure

#### Phase 2: Deployment
Attacker places USB devices in:
- Hospital parking lot
- Employee break room

#### Phase 3: Discovery
Employee finds USB:
> "Someone lost this, maybe I can find owner info"

#### Phase 4: Insertion
Employee plugs USB into work PC → AutoPlay executes malware

#### Phase 5: Compromise
- Keylogger captures credentials
- Backdoor establishes attacker connection
- Malware spreads across the network

#### Phase 6: Impact
- Patient records stolen
- Ransomware deployed
- Hospital operations disrupted


**Attack Type:** Social Engineering (Physical)  
**MITRE ATT&CK Techniques:**
- Initial Access: Removable Media
- Credential Access: Keylogging
- Lateral Movement: Network propagation













<br><br><br><br>

---

<br><br><br><br>









# Lab 13: Incident Investigation and Response

**Focus Area:** Incident Response | Threat Intelligence | Malware Analysis | Phishing Investigation  
**Frameworks Applied:** NIST Incident Response Lifecycle | MITRE ATT&CK | Pyramid of Pain  
**Tools Used:** VirusTotal  
**Skills:** Malware Analysis | IoC Identification | Phishing Playbook Application | Incident Escalation | Security Reporting | Post-Incident Review  

<br><br>

## Objective

Develop practical skills in incident investigation, threat intelligence analysis, and incident response using industry-relevant tools and frameworks. This lab simulates real-world Security Operations Center (SOC) workflows including malware analysis, phishing investigation, and post-incident reporting.

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Key Tools/Frameworks | Security Relevance |
|----------|-------|---------------------|-------------------|
| 1 | Malicious file hash investigation | VirusTotal, Pyramid of Pain, IoC classification | Threat intelligence analysis |
| 2 | Phishing incident response | Phishing playbook, 5 W's framework | Standardized incident handling |
| 3 | Incident report review | NIST Incident Response Lifecycle | Post-incident improvement |

<br><br>

## 2. Tools and Frameworks Used

| Tool/Framework | Purpose |
|----------------|---------|
| **VirusTotal** | Threat intelligence platform for file/URL analysis |
| **Pyramid of Pain** | IoC classification model (hash → IP → domain → TTP) |
| **Phishing Playbook** | Standardized response procedure for phishing alerts |
| **NIST Incident Response Lifecycle** | 4-phase framework (Prepare → Detect → Respond → Recover) |
| **MITRE ATT&CK** | Knowledge base of adversary tactics and techniques |

<br><br>

## 3. Activity 1: Investigate a Suspicious File Hash

**Objective:** Analyze a suspicious file hash using VirusTotal to determine maliciousness and identify Indicators of Compromise (IoCs).

### Scenario

A suspicious file downloaded via an email attachment was submitted for analysis. The SHA256 hash was used to determine whether the file was malicious and to uncover related IoCs.

### VirusTotal Findings

| Finding | Result |
|---------|--------|
| **Malicious verdict** | Confirmed malicious – multiple vendor detections |
| **Detection rate** | High across antivirus engines |
| **Community score** | Negative (consensus of malicious behavior) |
| **Behavior** | Harmful behavior upon execution |
| **System impact** | Unauthorized system changes triggered security alerts |

### Observed Malicious Behavior

| Behavior | Description |
|----------|-------------|
| **Process execution** | Executes unauthorized processes on host system |
| **Network communication** | Establishes outbound connections to external IP addresses |
| **HTTP requests** | Sends HTTP requests to malicious domain |
| **Input capture** | May perform keylogging/credential harvesting |

### Indicators of Compromise (IoCs)

| IoC Type | Value |
|----------|-------|
| **SHA256** | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` |
| **MD5** | `287d612e29b71c90aa54947313810a25` |
| **IP Address** | `207.148.109.242` |
| **Domain** | `org.misecure.com` |
| **Network Artifact** | HTTP requests to malicious domain |
| **Tool** | Input capture (credential/data harvesting) |
| **TTP** | Command and Control (C2 communication) |

### Pyramid of Pain – IoC Classification

The Pyramid of Pain categorizes IoCs by how difficult they are for attackers to change when defenders discover them.

| Pyramid Level      | Example IoC              | Attacker Difficulty | Defender Value |
|-------------------|--------------------------|---------------------|----------------|
| TTPs              | Command & Control (C2) | Very Hard (change attack methodology) | Very High      |
| Tools             | Input capture software (keylogger) | Hard (develop new tool) | High           |
| Network Artifacts | HTTP communication       | Moderate (change protocol slightly) | Medium         |
| Domain Names      | org.misecure.com         | Moderate (register new domain) | Medium         |
| IP Addresses      | 207.148.109.242          | Easy (use different C2 server) | Low–Medium     |
| Hash Values       | SHA256, MD5              | Trivial (recompile malware) | Low            |


**Key Concept:**
The higher you detect in the pyramid, the more costly it is for attackers to adapt.
- Bottom (Hash/IP) → Easy for attacker to evade  
- Top (TTPs) → Forces attacker to change behavior 🔥


### MITRE ATT&CK Mapping

| Technique | MITRE ID | Description |
|-----------|----------|-------------|
| Command and Control | T1071 | Application Layer Protocol (HTTP) |
| Input Capture | T1056 | Credential harvesting via keylogging |
| Unauthorized Process Execution | T1204 | User Execution |

<br><br>

## 4. Activity 2: Phishing Incident Response

**Objective:** Investigate a phishing alert using an organizational playbook and apply structured response procedures.

### Scenario

A phishing alert was triggered when an employee downloaded and opened a malicious attachment (`bfsvc.exe`). The attachment had already been verified as malicious.

### Email Analysis – Phishing Indicators

| Indicator | Finding | Why Malicious |
|-----------|---------|----------------|
| **Sender address** | `76tguyhh6tgftrt7tg.su` | Suspicious domain (.su - Soviet Union) |
| **Display name** | "Def Communications" | Mismatch with actual sender address |
| **Sender IP** | `114.114.114.114` | Known suspicious IP |
| **Subject/body** | Grammatical errors | Unprofessional, common phishing trait |
| **Attachment** | `bfsvc.exe` (password-protected) | Evasion technique for AV scanning |
| **File disguise** | Disguised as resume | Social engineering |

### The 5 W's of the Incident

| W | Answer |
|---|--------|
| **Who** | Unknown external attacker sending phishing emails |
| **What** | Employee downloaded and opened malicious file attachment |
| **When** | Wednesday, July 20, 2022, 09:30 AM (email received) |
| **Where** | HR department employee workstation |
| **Why** | Attempt to deliver malware and compromise sensitive systems |

### Incident Response Playbook Steps

## Incident Response Playbook Steps

| Step | Phase | Actions | Objective | 
|------|-------|---------|-----------|
| 1 | Triage | Verify alert legitimacy | Validate alert | 
| 2 | Analysis | Extract headers, analyze attachments, check hash (VirusTotal), identify phishing indicators | Investigate threat |
| 3 | Containment | Isolate workstation, block malicious domain/IP | Limit damage | 
| 4 | Escalation | Document findings, escalate to Level 2 SOC | Engage higher support | 
| 5 | Post-Incident | User awareness training, update playbook | Improve security posture |


**Tools Used:**
- Email header analyzer
- VirusTotal (hash verification)
- SIEM / SOC monitoring tools

**Attack Type:** Phishing → Malware Delivery  
**Response Goal:** Detect, contain, and prevent lateral movement


### Response Actions Taken

| Action | Purpose |
|--------|---------|
| Verified malicious file hash (VirusTotal) | Confirmed threat |
| Identified phishing characteristics | Documented indicators |
| Followed playbook escalation procedures | Standardized response |
| Isolated affected workstation (implied) | Containment |
| Escalated to Level 2 SOC analyst | Further investigation |

### Justification for Escalation

| Evidence | Implication |
|----------|-------------|
| Confirmed malicious attachment (SHA256) | File is definitely malware |
| User downloaded AND opened the file | Malware likely executed |
| Password-protected attachment | Evasion technique - deliberate |
| Alert severity: Medium | Potential organizational impact |

### Escalation Summary

Based on investigation and evidence, the ticket was escalated to a Level 2 SOC analyst for further investigation, following the organization's phishing playbook. This ensures prompt containment and reduces risk of malware spreading across the network.

**Final Decision:**  Escalated

<br><br>

## 5. Activity 3: Review of Incident Final Report

**Objective:** Analyze a post-incident report to extract key insights, root cause, and recommendations.

### Incident Summary

| Aspect | Details |
|--------|---------|
| **Incident Type** | Data breach involving unauthorized access to customer PII and financial data |
| **Root Cause** | Vulnerability in e-commerce web application |
| **Attack Method** | Forced browsing attack (URL parameter manipulation) |
| **Impact** | Customer data exposed |

### Incident Timeline

| Date | Event |
|------|-------|
| Dec 22, 2022 | Initial extortion email received and ignored |
| Dec 28, 2022 | Second email received with proof of data breach |
| Dec 28, 2022 | Incident reported to security team |
| Dec 28–31, 2022 | Investigation conducted; vulnerability identified |

**Key Observation:**
- Delay between first and second email allowed attacker persistence
- Late response increased impact

**Risk Level:** High


### Attack Method – Forced Browsing Explained
#### Normal Access:
- User → /order?id=12345 → Only sees own order

#### Forced Browsing Attack (Sequential ID enumeration):
- Attacker → /order?id=12346 → Sees another user's order
- Attacker → /order?id=12347 → Sees another user's order
- Attacker → /order?id=12348 → Sees another user's order




### Response Actions Taken

| Action | Purpose |
|--------|---------|
| Analyzed web server logs | Identify abnormal access patterns |
| Investigated sequential customer order access | Determine data exfiltration scope |
| Coordinated with public relations | Customer notification |
| Provided identity protection services | Mitigate customer impact |

### NIST Incident Response Lifecycle Mapping

| Phase | Activity | What Happened | Gap Identified | Improvement | Description |
|-------|----------|---------------|----------------|-------------|-------------|
| Prepare | Vulnerability scanning | No preventive controls | Missing access control testing | Implement secure coding & audits | Preventive security measures         |
| Detect | Forced browsing detected | Attack discovered late | Lack of monitoring | Deploy logging & alerting (SIEM) | Identify security incident (Dec 28) |
| Respond | Log analysis, web app patching | Investigation + patching | Reactive response | Faster incident handling | Investigate and contain (Dec 28–31) |
| Recover | Customer notification, identity protection | Customer notification | Reputational impact | Improve incident communication | Restore trust and operations |


### Recommendations

| Recommendation | Implementation | Purpose |
|----------------|----------------|---------|
| **Routine vulnerability scans** | Weekly automated scans | Detect vulnerabilities before attackers |
| **Penetration testing** | Quarterly or bi-annually | Validate security controls |
| **URL allowlisting** | Restrict access to authorized pages only | Prevent forced browsing |
| **Authentication enforcement** | Require auth for all sensitive data access | Ensure only verified users access data |

### Lessons Learned

| Lesson | Application |
|--------|-------------|
| Prompt response to extortion emails is critical | Ignoring initial warning signs delayed response |
| Strong access control prevents unauthorized access | URL allowlisting + authentication required |
| Post-incident documentation improves security posture | Learn from incidents to prevent recurrence |

<br><br>

## 6. NIST Incident Response Lifecycle – Quick Reference

| Phase | Activities | Lab Application |
|-------|------------|-----------------|
| **Prepare** | Training, tools, playbooks | Phishing playbook ready |
| **Detect & Analyze** | Alert triage, investigation | VirusTotal analysis, email review |
| **Contain & Eradicate** | Isolate, remove threat | Workstation isolation (implied) |
| **Recover** | Restore, monitor | Customer notifications, identity protection |
| **Post-Incident** | Lessons learned, improve | Recommendations documented |

<br><br>

## 7. Pyramid of Pain – Quick Reference

| Level | IoC Type | Attacker Difficulty | Defender Value |
|-------|----------|---------------------|----------------|
| 1 | Hash Values | Trivial | Low |
| 2 | IP Address | Easy | Low-Medium |
| 3 | Domain Names | Moderate | Medium |
| 4 | Network/Host Artifacts | Moderate | Medium |
| 5 | Tools | Hard | High |
| 6 | TTPs | Very Hard | Very High |

**Key Insight:** Detecting TTPs (Tactics, Techniques, Procedures) forces attackers to change their entire methodology – the most valuable detection.

<br><br>

## 8. MITRE ATT&CK Framework Mapping

| Tactic | Technique | ID | Lab Example |
|--------|-----------|-----|-------------|
| Initial Access | Phishing | T1566 | Malicious email attachment |
| Execution | User Execution | T1204 | User opened `bfsvc.exe` |
| Persistence | Create Account | T1136 | (Not observed) |
| Defense Evasion | Obfuscated Files | T1027 | Password-protected ZIP |
| Credential Access | Input Capture | T1056 | Keylogging behavior |
| Command & Control | Application Layer Protocol | T1071 | HTTP to malicious domain |
| Exfiltration | Exfiltration Over C2 Channel | T1041 | Data sent to attacker |

<br><br>

## 9. Skills Demonstrated

| Skill | Application in Lab |
|-------|-------------------|
| Threat intelligence analysis | Used VirusTotal to analyze malicious file hash |
| IoC identification | Extracted hash, IP, domain, network artifacts |
| Pyramid of Pain classification | Categorized IoCs by difficulty/value |
| Phishing playbook application | Followed structured response procedure |
| 5 W's framework | Documented incident details |
| Incident escalation | Justified escalation to Level 2 |
| Post-incident review | Analyzed final report for root cause |
| Recommendation development | Proposed vulnerability scanning, access controls |

<br><br>

## 10. Reflection

This lab provided hands-on experience in analyzing real-world security incidents using structured methodologies.

**Activity 1 takeaways:**
- VirusTotal is essential for rapid malware triage
- Pyramid of Pain shows why TTP detection is most valuable (hardest for attackers)
- Multiple IoC types (hash, IP, domain) provide defense in depth

**Activity 2 takeaways:**
- Standardized playbooks ensure consistent response
- Password-protected attachments are evasion techniques
- The 5 W's framework structures incident documentation

**Activity 3 takeaways:**
- Forced browsing attacks exploit missing access controls
- Ignoring initial extortion emails delays response
- Post-incident recommendations must be actionable

**Demonstrates:** Incident investigation methodology, threat intelligence application, and professional SOC documentation.

<br><br>

## 11. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| **IoC** | Indicator of Compromise – evidence of potential intrusion |
| **Pyramid of Pain** | Model ranking IoCs by attacker difficulty to change |
| **TTP** | Tactics, Techniques, and Procedures – attacker behavior patterns |
| **MITRE ATT&CK** | Knowledge base of adversary tactics and techniques |
| **VirusTotal** | Online threat intelligence platform |
| **SHA256** | Cryptographic hash function (256-bit output) |
| **Playbook** | Standardized incident response procedure |
| **Forced browsing** | Attack enumerating URLs to access unauthorized data |
| **C2 (C&C)** | Command and Control – attacker communication channel |
| **SOC** | Security Operations Center |

<br><br>

## 12. Incident Response Quick Reference

### Phishing Email Checklist
| Check | Criteria | 
|-------|----------|
| () | Check sender email address (domain mismatch?) |
| () | Verify display name vs. actual sender |
| () | Examine subject line (urgency, grammar errors?) |
| () | Hover over links (do they match displayed text?) |
| () | Check attachments (unexpected .exe, .zip, .js?) |
| () | Look for urgency/pressure tactics |
| () | Verify with sender via out-of-band communication |



### Pyramid of Pain (Difficulty for Attacker)
Hash (Easiest to Change) < IP < Domain < Artifact < Tool < TTP (Hardest to Change)


### NIST IR Lifecycle (4 Phases)
Prepare → Detect & Analyze → Contain & Eradicate → Recover → (Post-Incident)












<br><br><br><br>

---

<br><br><br><br>















# Lab 14: Network Monitoring and Analysis

**Focus Area:** Network Traffic Analysis | Packet Capture | Protocol Analysis  
**Tools Used:** Wireshark | tcpdump 
**Skills:** Packet Inspection | Filter Application | Live Traffic Capture | Protocol Layering | Tool Comparison  

<br><br>

## Objective

Analyze and monitor network traffic using industry-standard tools (Wireshark and tcpdump). This lab demonstrates packet analysis, packet capture, and tool comparison through three main activities.

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Tool | Key Skills |
|----------|-------|------|------------|
| 1 | Analyze existing packet capture | Wireshark | Packet inspection, filtering, protocol identification |
| 2 | Capture live network traffic | tcpdump | Live capture, interface selection, file saving |
| 3 | Compare network analyzers | Research | Tool evaluation, use case identification |

<br><br>

## 2. Activity 1: Analyze Your First Packet (Wireshark)

**Objective:** Use Wireshark to open and analyze a packet capture (.pcap) file, understanding packet structure, protocol layers, and applying filters.

### Packet Structure – OSI Model Layers
## Packet Analysis – Wireshark (Security View)

| Layer | Example Data | Description | What to Look For in Wireshark | Security Insight |
|-------|--------------|-------------|-------------------------------|------------------|
| Application | HTTP, DNS, HTTPS request | User-level data | URLs, headers, payload | Detect phishing, data leaks |
| Transport | TCP/UDP segments | Ports, sequencing, reliability | Ports, flags (SYN, ACK) | Identify scanning or floods |
| Network | IP packets (IPv4, IPv6) | Source/destination IP addressing | Source/destination IP | Trace attacker origin |
| Data Link | Ethernet frames | MAC addresses and frames | MAC addresses| Detect ARP spoofing |
| Physical | Bits | Raw bits transmitted over medium | Raw capture data | Low-level transmission layer |



### Wireshark Filters Used

| Filter | Purpose | Example Use Case |
|--------|---------|------------------|
| `ip.addr == 142.250.1.139` | Traffic to/from specific IP | Investigate suspicious IP |
| `ip.src == 142.250.1.139` | Traffic from specific IP | Identify source of traffic |
| `ip.dst == 142.250.1.139` | Traffic to specific IP | Track destination |
| `eth.addr == 42:01:ac:15:e0:02` | Traffic by MAC address | Physical device tracking |
| `udp.port == 53` | DNS traffic | Domain resolution analysis |
| `tcp.port == 80` | HTTP traffic | Web traffic analysis |
| `tcp contains "curl"` | TCP payload contains text | Application signature detection |

### Sample Packet Evidence

#### 1. DNS Query (Domain Resolution)

| Field | Value |
|-------|-------|
| **Source IP** | 172.21.224.2 |
| **Destination IP** | DNS Server |
| **Protocol** | UDP |
| **Destination Port** | 53 |
| **Query** | opensource.google.com |

**Purpose:** System resolving domain name to IP address

#### 2. TCP Communication (Web Traffic)

| Field | Value |
|-------|-------|
| **Source IP** | 172.21.224.2 |
| **Destination IP** | 142.250.1.139 |
| **Protocol** | TCP |
| **Destination Port** | 80 (HTTP) |

**Purpose:** Web communication between local system and external server

#### 3. ICMP Packet (Connectivity Check)

| Field | Value |
|-------|-------|
| **Source IP** | 172.21.224.2 |
| **Destination IP** | 142.250.1.139 |
| **Protocol** | ICMP |
| **Type** | Echo Request/Reply |

**Purpose:** Basic network connectivity testing

### Packet Layer Analysis (TCP Packet Example)

| Layer | Information Captured |
|-------|---------------------|
| **Frame** | Overall packet size, capture timestamp |
| **Ethernet II** | Source MAC, Destination MAC |
| **IPv4** | Source IP (172.21.224.2), Destination IP (142.250.1.139) |
| **TCP** | Source Port (49652), Destination Port (80), Flags (SYN, ACK, etc.) |

### Traffic Interpretation

| Observation | Interpretation |
|-------------|----------------|
| DNS queries to opensource.google.com | Normal domain resolution |
| TCP connections over port 80 | HTTP web traffic |
| ICMP echo requests/replies | Connectivity checks (ping) |
| No malicious indicators | Normal web browsing behavior |

### Security Relevance

| Skill | Application |
|-------|-------------|
| Detect abnormal traffic patterns | Identify C2 communication, data exfiltration |
| Identify potential intrusions | Detect scanning, exploitation attempts |
| Investigate incidents | Forensic analysis of captured traffic |

<br><br>

## 3. Activity 2: Capture Your First Packet (tcpdump)

**Objective:** Capture live network traffic using tcpdump in a Linux environment, save captures, and analyze results.

### Network Interface Identification

```bash
# List available interfaces
ifconfig

# List interfaces suitable for capture
sudo tcpdump -D
Selected interface: eth0 (primary Ethernet interface)
```

### tcpdump Command Reference
| Command | Purpose |
|---------|---------|
| `sudo tcpdump -i eth0 -v -c5` | Capture 5 packets from eth0 with verbose output |
| `sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &` | Capture 9 HTTP packets, save to file, run in background |
| `sudo tcpdump -nn -r capture.pcap -v` | Read saved capture with verbose output |
| `sudo tcpdump -nn -r capture.pcap -X` | Read saved capture with hex and ASCII output |

### tcpdump Options Explained
| Option | Meaning | Security Relevance |
|--------|---------|-------------------|
| `-i eth0` | Capture on interface eth0 | Target specific network segment |
| `-v` | Verbose output | More packet details |
| `-c5` | Capture 5 packets then exit | Limit capture size |
| `-nn` | No name resolution | Prevents DNS leaks during capture |
| `port 80` | Filter HTTP traffic | Focus on web traffic |
| `-w capture.pcap` | Write to file | Save for later analysis |
| `-r capture.pcap` | Read from file | Analyze saved capture |
| `-X` | Hex and ASCII output | Deep packet inspection |
| `&` | Run in background | Simultaneous traffic generation |


### Capture Process
| Step | Action | Command |
|------|--------|---------|
| 1 | Start tcpdump in background | sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap & | 
| 2 | Generate traffic while tcpdump runs | curl opensource.google.com | 
| 3 | tcpdump captures 9 packets and exits | - |
| 4 | Verify capture file | ls -l capture.pcap | 
| 5 | Analyze captured packets | sudo tcpdump -nn -r capture.pcap -v, sudo tcpdump -nn -r capture.pcap -X|
        

### Key Findings
| Finding | Implication |
|---------|-------------|
| Successfully captured HTTP traffic (port 80) | Web traffic monitoring possible |
| Observed TCP handshake (SYN, SYN-ACK, ACK) | Connection establishment visible |
| Identified packet metadata (TTL, flags, sequence numbers) | Deep packet inspection possible |
| `-nn` option prevented name resolution | Secure capture (no DNS leaks) |


### TCP Handshake Observed


| Step | Stage | Client Action | Server Response | Description | Security Relevance |
|------|-------|---------------|-----------------|-------------|--------------------|
| 1 | SYN | SYN (Seq = x) | — | Connection request | Can be used in SYN flood attacks |
| 2 | SYN-ACK | — | SYN-ACK (Seq = y, Ack = x+1) | Acknowledge request | Confirms open port |
| 3 | ACK | ACK (Ack = y+1) | — | Connection established | Session begins |
| 4 | HTTP GET | HTTP GET request | — | Client requests resource | May expose sensitive endpoints |
| 5 | HTTP 200 OK | — | HTTP 200 OK | Server returns requested data    | Data returned to client |


**Key Insight:**
- TCP handshake establishes reliable communication before data transfer.
- Attackers may abuse SYN packets for DoS attacks (SYN flood).



## 4. Activity 3: Research Network Protocol Analyzers
Objective: Compare Wireshark and tcpdump to understand differences, similarities, and appropriate use cases.

### Comparison Matrix
| Feature | Wireshark | tcpdump |
|---------|-----------|---------|
| Interface | Graphical (GUI) | Command-line (CLI) |
| Ease of learning | Easier for beginners | Steeper learning curve |
| Filtering | Advanced (visual filter builder) | Basic (command-line expressions) |
| Visualization | Color-coded, graphs, streams | Text-only output |
| Resource usage | High (memory, CPU) | Low (lightweight) |
| Remote capture | Limited (requires GUI access) | Excellent (SSH + tcpdump) |
| Scriptable | Limited | Fully scriptable |
| Output formats | Multiple (pcap, JSON, CSV, etc.) | pcap primarily |
| Real-time analysis | Yes (with GUI) | Yes (text-based) |
| Cost | Free (open source) | Free (open source) |

### Similarities
| Similarity | Description |
|------------|-------------|
| Packet capture | Both capture live network traffic |
| Filtering capability | Both support BPF (Berkeley Packet Filter) syntax |
| Protocol analysis | Both analyze common protocols (TCP, UDP, HTTP, DNS) |
| Open source | Both are free and community-supported |
| pcap support | Both read/write .pcap files |

### Limitations
| Tool | Limitation |
|------|-------------|
| Wireshark | Requires GUI (X11 forwarding or local desktop); higher resource usage |
| tcpdump | CLI-only; requires proficiency with command-line filters; no visual output |

### Use Cases
| Scenario | Recommended Tool | Justification |
|----------|-----------------|---------------|
| Deep protocol analysis | Wireshark | Visual packet dissection, follow TCP streams |
| Quick capture on server | tcpdump | Lightweight, no GUI needed |
| Automated capture script | tcpdump | Scriptable, can run in cron jobs |
| Training/learning | Wireshark | Visual feedback helps understanding |
| Remote forensic capture | tcpdump | SSH + tcpdump, transfer pcap for analysis |
| Large capture analysis | Wireshark | Better navigation, filtering, search |
| Low-bandwidth environment | tcpdump | Minimal overhead |


### Workflow Integration - SOC Pipeline

Remote Server (tcpdump capture)
- Secure transfer (SCP / SFTP)
- Analyst Workstation (Wireshark analysis)

**Principle:** Capture on server, analyze locally


| Stage              | Tool        | Purpose                          |
|--------------------|------------|----------------------------------|
| Packet Capture     | tcpdump     | Collect network traffic          |
| Secure Transfer    | SCP / SFTP  | Move data safely                 |
| Traffic Analysis   | Wireshark   | Inspect packets visually         |
| Investigation      | Analyst     | Identify anomalies or threats    |


## Security Insight
- Capturing on the server reduces risk of data loss
- Local analysis prevents performance impact on production systems
- This workflow is commonly used in SOC Level 1–2 investigations



## 5. Filter Pattern Library
### Common Wireshark/tcpdump Filters
| Filter | Protocol/Field | Use Case |
|--------|---------------|----------|
| `tcp.port == 80` | HTTP | Web traffic analysis |
| `udp.port == 53` | DNS | Domain resolution investigation |
| `icmp` | ICMP | Ping flood detection |
| `tcp.flags.syn == 1` | SYN packets | Port scanning detection |
| `tcp.analysis.flags` | TCP analysis | Retransmissions, out-of-order |
| `http.request` | HTTP requests | Web browsing analysis |
| `dns.qry.name contains "google"` | DNS queries | Domain pattern matching |
| `ip.addr == 192.168.1.1` | IP address | Single host traffic |
| `tcp contains "password"` | Payload | Credential detection |
| `frame.len > 1500` | Frame size | Jumbo frame detection |


### tcpdump BPF Filters
| Filter | Meaning |
|--------|---------|
| `host 192.168.1.1` | Traffic to/from IP |
| `src host 192.168.1.1` | Traffic from IP |
| `dst host 192.168.1.1` | Traffic to IP |
| `port 80` | Traffic on port 80 |
| `tcp port 80` | TCP port 80 only |
| `udp port 53` | UDP port 53 only |
| `net 192.168.1.0/24` | Entire subnet |
| `tcp[tcpflags] & tcp-syn != 0` | SYN packets only |


## 6. Wireshark vs tcpdump – Quick Decision Guide
- Need GUI? → Wireshark  
- Remote server? → tcpdump  
- Learning/network visualization? → Wireshark  
- General use? → Either tool works


## 7. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| Packet inspection | Analyzed DNS, TCP, ICMP packets in Wireshark |
| Protocol layering understanding | Identified Frame, Ethernet, IP, TCP layers |
| Filter application | Used IP, port, protocol, and payload filters |
| Live traffic capture | Used tcpdump to capture HTTP traffic |
| Interface management | Identified and selected eth0 for capture |
| Capture file management | Saved, verified, and analyzed .pcap files |
| Tool evaluation | Compared Wireshark vs tcpdump features |
| Security best practices | Used `-nn` to disable name resolution |


## 8. Tools and Concepts Used
| Tool/Concept | Application |
|--------------|-------------|
| Wireshark | Graphical packet analysis |
| tcpdump | Command-line packet capture |
| BPF filters | Berkeley Packet Filter syntax |
| .pcap format | Standard packet capture format |
| TCP handshake | Observed SYN, SYN-ACK, ACK sequence |
| Protocol layering | Analyzed encapsulation |
| HTTP (port 80) | Captured web traffic |
| DNS (port 53) | Observed domain resolution |
| ICMP | Observed connectivity checks |


## 9. Reflection
This lab significantly improved my understanding of how network traffic operates and how security analysts investigate it.

### Activity 1 takeaways:
- Packet analysis was initially overwhelming due to protocol complexity
- Wireshark filters make traffic analysis manageable
- Protocol layering (Ethernet → IP → TCP/UDP → Application) is consistent across packets

### Activity 2 takeaways:
- tcpdump is lightweight and ideal for remote/server captures
- The -nn option is critical for secure captures (prevents DNS leaks)
- Saving captures to .pcap enables later analysis in Wireshark

### Activity 3 takeaways:
- Wireshark and tcpdump complement each other
- Master both: tcpdump for capture, Wireshark for analysis
- Use case determines the right tool

Demonstrates: Network traffic analysis proficiency, tool familiarity, and investigative methodology.

## 10. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Packet capture | Recording network traffic for analysis |
| .pcap | Standard file format for captured packets |
| BPF | Berkeley Packet Filter – syntax for filtering packets |
| Encapsulation | Wrapping data with protocol headers at each layer |
| TCP handshake | SYN, SYN-ACK, ACK – connection establishment |
| TTL | Time To Live – hop limit for packets |
| Sequence number | TCP field for packet ordering |
| Name resolution | Converting IP addresses to hostnames (can leak in captures) |

## 11. Command Quick Reference
### tcpdump Common Commands
```bash
# List interfaces
sudo tcpdump -D

# Capture 10 packets on eth0
sudo tcpdump -i eth0 -c10

# Capture HTTP traffic to file (no name resolution)
sudo tcpdump -i eth0 -nn port 80 -w capture.pcap

# Read capture file with verbose output
sudo tcpdump -nn -r capture.pcap -v

# Read capture with hex and ASCII
sudo tcpdump -nn -r capture.pcap -X

# Capture all traffic from specific IP
sudo tcpdump -i eth0 src host 192.168.1.1

# Capture traffic to specific port
sudo tcpdump -i eth0 dst port 443
Wireshark Display Filters
ip.addr == 192.168.1.1          # Traffic to/from IP
tcp.port == 443                 # HTTPS traffic
http.request                    # HTTP GET/POST requests
dns.qry.name contains "example" # DNS queries for domain
tcp.flags.syn == 1              # SYN packets only
frame.len > 1500                # Large frames
tcp.analysis.retransmission     # Retransmitted packets
```

## 12. Security Best Practices for Packet Capture
| Practice | Why It Matters |
|----------|----------------|
| Use `-nn` in tcpdump | Prevents DNS lookups that could leak information |
| Capture to file, analyze later | Minimizes time spent capturing live |
| Use filters to limit capture | Reduces storage and focuses on relevant traffic |
| Secure .pcap files | May contain sensitive data (passwords, PII) |
| Run with least privilege | Use sudo only when necessary |
| Document capture context | Timestamps, interfaces, filters used |













<br><br><br><br>

---

<br><br><br><br>
















# Lab 15: Network Traffic and Logs using IDS and SIEM Tools

**Focus Area:** Intrusion Detection | SIEM | Log Analysis | Threat Detection  
**Tools Used:** Suricata | Splunk | Wazuh | Google Chronicle | jq  
**Skills:** IDS Rule Writing | PCAP Analysis | SPL Queries | Log Correlation | Cloud SIEM | JSON Parsing  

<br><br>

## Objective

Monitor, analyze, and query network traffic and logs using IDS (Suricata) and SIEM tools (Splunk, Wazuh, and Google Chronicle). Understand how security analysts detect, investigate, and correlate security events using different log sources and detection systems.

<br><br>

## 1. Lab Activities Summary

| Activity | Tool | Focus | Key Skills |
|----------|------|-------|------------|
| 1 | Suricata (IDS) | Custom rules, PCAP analysis, alert generation | Rule writing, jq parsing |
| 2 | Splunk Cloud (SIEM) | Log upload, SPL queries, authentication monitoring | SPL, log filtering |
| 3 | Wazuh (SIEM) | SSH brute-force investigation | Field filtering, anomaly detection |
| 4 | Google Chronicle (Cloud SIEM) | Structured security searches | Cloud SIEM, query language |

<br><br>

## 2. Tools Overview

| Tool | Type | Purpose | Key Feature |
|------|------|---------|-------------|
| **Suricata** | IDS/IPS | Network traffic inspection | Rule-based detection, high performance |
| **Splunk** | SIEM | Centralized log analysis | SPL query language, dashboards |
| **Wazuh** | SIEM | Security monitoring | Open source, integrated with Elastic |
| **Chronicle** | Cloud SIEM | Enterprise threat detection | Google-scale, cloud-native |
| **jq** | CLI tool | JSON parsing | Lightweight, scriptable |

---

## 3. Activity 1: Explore Signatures and Logs with Suricata

**Objective:** Use Suricata as an IDS to create custom rules, analyze network traffic, and generate alerts from a packet capture file.

### Suricata Rule Structure
Action → Protocol → Source IP → Source Port → Destination IP → Destination Port → Options

#### Example:
alert icmp any any → any any (msg:"ICMP traffic detected")

| Field | Description | Example |
|-------|-------------|---------|
| Action | What to do | alert |
| Protocol | Network protocol | icmp |
| Source IP | Origin of traffic | any |
| Source Port | Source port | any |
| Destination IP | Target system | any |
| Destination Port | Target port | any |
| Options | Rule metadata / message | msg:"alert" |


### Security Insight
- Suricata is an IDS/IPS engine used for network threat detection
- Rules define what traffic should trigger alerts
- "any any → any any" is commonly used for broad detection testing


### Custom Rules Created

| Action | Protocol | Source | Destination | Message | SID |
|--------|----------|--------|-------------|---------|-----|
| alert | icmp | any any | any any | "ICMP Ping Detected" | 1000001 |
| alert | http | any any | any 80 | "HTTP GET Request Detected" | 1000002 |
| alert | tcp | any any | any 22 | "SSH Connection Attempt" | 1000003 |

### Rule Components Explained

| Component | Example | Purpose |
|-----------|---------|---------|
| **Action** | `alert` | What to do when rule matches (alert, drop, reject, pass) |
| **Protocol** | `icmp`, `http`, `tcp` | Which protocol to inspect |
| **Source** | `any any` | Source IP and port (any = wildcard) |
| **Direction** | `->` | Traffic direction (-> = to, <> = both ways) |
| **Destination** | `any any` | Destination IP and port |
| **Message** | `msg:"..."` | Alert text displayed |
| **SID** | `sid:1000001` | Unique rule identifier |
| **Revision** | `rev:1` | Rule version number |

### Lab Files Used

| File | Purpose |
|------|---------|
| `custom.rules` | Suricata detection rules |
| `sample.pcap` | Network traffic capture (Wireshark sample) |
| `fast.log` | Suricata alert log (quick summary) |
| `eve.json` | Structured Suricata event logs (JSON format) |

### Suricata Workflow

| Stage | Input/Output | Description | Example | 
|-------|--------------|-------------|---------|
| Rule Definition | custom.rules | Defines detection logic | (rules file) | 
| Traffic Input | sample.pcap | Packet capture for analysis | (traffic) | 
| Processing | Suricata Engine | Matches traffic against rules | Engine | 
| Alert Output | fast.log | Human-readable alerts | "ICMP Ping Detected" |
| Structured Logs | eve.json | Machine-readable event data (JSON) | {"timestamp":"...", "src_ip":"...", "alert":{...}} |


## Security Insight
- `fast.log` is used for quick alert visibility
- `eve.json` is used for SIEM integration (Splunk, ELK)
- Suricata acts as both IDS and IPS depending on configuration


### Sample eve.json Output
```json
{
  "timestamp": "2026-04-21T10:15:01",
  "src_ip": "192.168.1.10",
  "dest_ip": "8.8.8.8",
  "proto": "ICMP",
  "alert": {
    "signature": "ICMP Ping Detected"
  },
  "flow_id": 1111
}
```


### jq Parsing Commands
```bash
# Extract all alerts
jq '.alert' eve.json

# Extract specific fields
jq '{timestamp, src_ip, dest_ip, proto, alert_signature: .alert.signature}' eve.json

# Filter by protocol
jq 'select(.proto == "ICMP")' eve.json

# Count alerts by signature
jq -r '.alert.signature' eve.json | sort | uniq -c
```


### Skills Developed – Activity 1
| Skill | Application |
|-------|-------------|
| IDS rule creation | Wrote custom rules for ICMP, HTTP, SSH |
| Rule interpretation | Understood action, header, options structure |
| Network traffic analysis | Applied rules to sample.pcap |
| JSON log parsing | Used jq to extract fields from eve.json |
| Event correlation | Used flow_id to track related events |


### Security Relevance
Suricata helps detect malicious or suspicious traffic in real time by applying rule-based inspection on network packets. Benefits include:
- Real-time detection of known attack patterns
- Custom rule creation for organization-specific threats
- Structured logging (eve.json) for SIEM integration

### Reflection – Activity 1
This activity improved my understanding of how IDS tools inspect network traffic and generate alerts. I learned how to create rules, analyze structured logs, and use jq to extract specific fields for investigation.


## 4. Activity 2: Perform a Query with Splunk
Objective: Use Splunk Cloud to upload log data and perform searches using SPL (Search Processing Language).

### Sample Log Data
```
2026-04-21 10:20:05 user=root action=ssh_login status=failure src_ip=192.168.1.15
2026-04-21 10:20:10 user=guest action=login status=success src_ip=192.168.1.20
2026-04-21 10:20:15 user=admin action=ssh_login status=failure src_ip=203.0.113.50
2026-04-21 10:20:20 user=admin action=ssh_login status=failure src_ip=203.0.113.50
2026-04-21 10:20:25 user=admin action=ssh_login status=success src_ip=203.0.113.50
```

### SPL Query Examples
| Query | Purpose |
|-------|---------|
| `status=failure` | All failed authentication events |
| `status=failure AND user=root` | Failed logins for root user |
| `user=admin status=failure` | Failed logins for admin user |
| `src_ip=192.168.1.15` | Activity from specific IP |
| `action=ssh_login status=failure` | Failed SSH logins only |


### Splunk Workflow
## Splunk Log Analysis Workflow

| Stage | Action | Purpose |
|-------|--------|---------|
| Data Ingestion | Upload log file | Import raw event data |
| Query Execution | SPL search | Extract relevant events |
| Filtering | Refine results | Remove noise, focus on anomalies |
| Analysis | Identify suspicious activity | Detect threats or anomalies |


### Skills Developed – Activity 2
| Skill | Application |
|-------|-------------|
| SPL query construction | Built searches using field-value pairs |
| Log filtering | Isolated authentication failures |
| Dashboard navigation | Explored Splunk Cloud interface |


### Security Relevance
Splunk enables centralized log analysis to detect authentication failures and abnormal user behavior across enterprise systems.

### Reflection – Activity 2
This activity helped me understand how SIEM tools like Splunk can quickly filter large datasets to identify security-relevant events. The field-value pair syntax makes searching intuitive once you understand the log structure.



## 5. Activity 3: Perform a Query with Wazuh
Objective: Use Wazuh SIEM to investigate SSH brute-force attempts on a mail server.

### Sample Wazuh Logs
```
Apr 21 10:30:01 mailsv sshd: Failed password for root from 192.168.1.10
Apr 21 10:30:05 mailsv sshd: Failed password for root from 192.168.1.11
Apr 21 10:30:09 mailsv sshd: Failed password for root from 192.168.1.12
Apr 21 10:30:13 mailsv sshd: Failed password for root from 192.168.1.10
Apr 21 10:30:17 mailsv sshd: Failed password for root from 192.168.1.11
```

### Query Used
```
host.keyword: mailsv AND (fail* OR failed) AND root
```

#### Query Breakdown
| Component | Meaning | Purpose |
|-----------|---------|---------|
| `host.keyword: mailsv` | Filter by hostname | Focus on mail server |
| `fail*` | Wildcard match | Catches "fail", "failed", "failure" |
| `OR failed` | Alternative term | Ensures coverage |
| `AND root` | Combine conditions | Target root user specifically |


### Findings
| Finding | Value |
|---------|-------|
| Total failed root SSH login attempts | 376 |
| Multiple IP addresses involved | Yes (distributed brute-force) |
| Sensitive data identified | vendor_sales logs in mail server |
| Attack pattern | Credential brute-force |


### Wazuh Investigation Workflow

| Stage | Action | Result |
|-------|--------|--------|
| Detection | Identify suspicious host | mailsv flagged |
| Query Execution | host:mailsv AND fail* | Log filtering applied |
| Analysis | Review logs | Failed login patterns found |
| Count Events | Aggregate failures | 376 attempts detected |
| Source Analysis | Identify IPs | Multiple source IPs involved |


### Skills Developed – Activity 3
| Skill | Application |
|-------|-------------|
| SIEM threat investigation | Identified brute-force pattern |
| Field-based filtering | Used `host.keyword` for precise filtering |
| Log correlation | Linked multiple failed attempts |
| Anomaly detection | Recognized 376 failures as abnormal |


### Security Relevance
Wazuh helps detect brute-force attacks and unauthorized access attempts in real time. The open-source nature allows customization for specific organizational needs.


### Reflection – Activity 3
This activity demonstrated how SIEM systems help security analysts investigate attack patterns such as brute-force login attempts. The ability to count and correlate failed attempts across multiple source IPs is essential for identifying distributed attacks.



## 6. Activity 4: Perform a Query with Chronicle
Objective: Use Google Chronicle as a cloud-based SIEM platform to perform structured security searches on ingested logs.

### Chronicle Query Language
| Query Type | Syntax | Purpose |
|------------|--------|---------|
| Event type filter | `metadata.event_type = "NETWORK_CONNECTION"` | Focus on network events |
| Port filter | `target.port = 22` | SSH traffic only |
| Action filter | `security_result.action = "FAIL"` | Failed actions only |
| Combined | `target.port = 22 AND security_result.action = "FAIL"` | Failed SSH attempts |

### Example Queries
```
-- All network connections
metadata.event_type = "NETWORK_CONNECTION"

-- SSH connection attempts
target.port = 22

-- Failed SSH attempts
target.port = 22 AND security_result.action = "FAIL"

-- Failed attempts from specific IP
target.port = 22 AND security_result.action = "FAIL" AND principal.ip = "192.168.1.10"
```


### Chronicle vs Traditional SIEM
| Feature | Chronicle (Cloud) | Traditional SIEM |
|---------|-------------------|------------------|
| Scalability | Google-scale (unlimited) | Hardware-limited |
| Query speed | Sub-second on petabytes | Minutes to hours |
| Maintenance | Zero (cloud-managed) | Significant |
| Cost model | Consumption-based | Hardware + licensing |
| Retention | Extended (years) | Limited (months) |


### Skills Developed – Activity 4
| Skill | Application |
|-------|-------------|
| Cloud SIEM navigation | Explored Chronicle interface |
| Structured query language | Used field-based queries |
| Security event investigation | Correlated network events |


### Security Relevance
Chronicle provides scalable cloud-based log analysis for enterprise-level threat detection, enabling rapid investigation across massive datasets.

### Reflection – Activity 4
This activity introduced cloud-based security monitoring and showed how large-scale log analysis is performed in modern SOC environments. The structured query language is intuitive once you understand the data schema.




## 7. IDS vs SIEM – Comparison
| Feature | IDS (Suricata) | SIEM (Splunk/Wazuh/Chronicle) |
|---------|----------------|-------------------------------|
| Data source | Network traffic | Logs (multiple sources) |
| Scope | Network layer | Enterprise-wide |
| Detection | Rule-based signatures | Correlation, analytics |
| Alert type | Packet-level | Event-level |
| Primary use | Real-time threat detection | Investigation, compliance |
| Typical deployment | Network perimeter | Centralized logging |


### How They Work Together

| Step | Tool | Type | Function | Output | Workflow Role |
|------|------|------|----------|--------|---------------|
| 1 | Suricata | IDS | Detects network threats/intrusions | eve.json alerts | Initial detection of suspicious activity |
| 2 | Splunk | SIEM | Log aggregation & correlation | Search results, dashboards | Correlates events across data sources |
| 3 | Chronicle | Cloud SIEM | Large-scale threat analysis | Cloud analytics | Deep analysis and threat investigation |
| 4 | SOC Analyst | Human | Investigates and responds | Incident reports, actions taken  | Final review, response, and decision-making |


## 8. SOC Analyst Workflow – Complete Picture

| Stage | Process | Output / Action |
|-------|---------|-----------------|
| Detection | Suricata IDS | ICMP scan detected |
| Alerting | eve.json logs | Structured alert generated |
| Ingestion | SIEM (Splunk/Wazuh) | Centralized log storage |
| Investigation| Query & analysis | Identify related activity (Same source IP?, Other failed attempts?, Timeline of activity?) |
| Correlation | Cross-log analysis | Multi-stage attack linked (Link IDS alerts with authentication logs, ICMP scan followed by SSH brute-force)|
| Response | SOC containment | IP blocked, host isolated |



## 9. Multi-SIEM Comparison
| Feature | Splunk | Wazuh | Chronicle |
|---------|--------|-------|-----------|
| Deployment | Cloud or on-prem | On-prem (open source) | Cloud-only |
| Query language | SPL | Lucene/KQL | YARA-L (custom) |
| Learning curve | Moderate | Moderate | Low (structured) |
| Cost | Commercial ($$$) | Free (open source) | Consumption-based |
| Best for | Enterprise SOC | Budget-conscious teams | Google ecosystem |
| Integration | Extensive | Elastic stack | Google Cloud |


### When to Use Each
| Scenario | Recommended Tool |
|----------|------------------|
| Deep packet inspection | Suricata (IDS) |
| Enterprise log aggregation | Splunk |
| Budget-conscious SOC | Wazuh |
| Google Cloud environment | Chronicle |
| Automated parsing | jq |


## 10. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| IDS rule writing | Created custom Suricata rules for ICMP, HTTP, SSH |
| PCAP analysis | Applied rules to sample.pcap traffic capture |
| JSON parsing | Used jq to extract fields from eve.json |
| SPL queries | Searched Splunk for authentication failures |
| SIEM investigation | Used Wazuh to identify SSH brute-force (376 attempts) |
| Cloud SIEM | Queried Chronicle for network connections |
| Log correlation | Linked events across multiple tools |
| Tool comparison | Evaluated IDS vs SIEM, Splunk vs Wazuh vs Chronicle |


## 11. Tool-Specific Query Reference
### Suricata (jq)
```bash
# Extract all alerts
jq '.alert' eve.json

# Filter by protocol
jq 'select(.proto == "ICMP")' eve.json

# Show timestamp and signature only
jq '{time: .timestamp, alert: .alert.signature}' eve.json
```

### Splunk (SPL)
```spl
# Basic search
status=failure

# Field-specific
user=root status=failure

# Time-based
earliest=-24h status=failure

# Statistical
status=failure | stats count by user
```


### Wazuh (KQL)
```kql
host.keyword: mailsv AND (fail* OR failed) AND root
Chronicle (YARA-L)
yara
metadata.event_type = "NETWORK_CONNECTION"
target.port = 22
security_result.action = "FAIL"
```


## 12. Overall Reflection
This lab provided hands-on experience with IDS and SIEM tools used in real-world cybersecurity operations.

Key takeaways by activity:

| Activity | Key Insight |
|----------|--------------|
| Suricata | IDS provides packet-level visibility; custom rules enable organization-specific detection |
| Splunk | SPL makes log analysis efficient; field-value pairs are intuitive |
| Wazuh | Open-source SIEM is powerful; 376 failed attempts clearly indicates brute-force |
| Chronicle | Cloud SIEM scales infinitely; structured queries enable rapid investigation |


### Complete workflow understanding:
- Suricata provides low-level network visibility (packets)
- SIEM tools enable high-level event correlation (logs)
- Together, they form the core of SOC monitoring

Demonstrates: Practical proficiency with industry-standard IDS and SIEM tools, essential for SOC analyst roles.

## 13. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| IDS | Intrusion Detection System – monitors network traffic for threats |
| IPS | Intrusion Prevention System – IDS that can block traffic |
| SIEM | Security Information and Event Management – centralized logging |
| SPL | Search Processing Language – Splunk's query language |
| PCAP | Packet Capture – recorded network traffic |
| eve.json | Suricata's structured JSON log format |
| jq | Command-line JSON processor |
| SID | Signature ID – unique rule identifier |
| Brute-force | Repeated login attempts to guess credentials |
| Flow ID | Unique identifier for a network flow (connection) |


## 14. Quick Reference – Tool Commands
### Suricata
```bash
# Run Suricata on PCAP
suricata -r sample.pcap -S custom.rules

# Read fast.log
cat fast.log

# Parse eve.json with jq
jq '.' eve.json
```


### Splunk
```spl
# Search syntax
field=value
field=value AND field2=value2
```


### Wazuh
```kql
field.keyword: value AND (term1 OR term2)
```


### Chronicle
```yara
metadata.event_type = "TYPE"
field = "value"
field = "value" AND other_field = "value"
```










<br><br><br><br>

---

<br><br><br><br>












# Lab 16: Automate Cybersecurity Tasks with Python

**Focus Area:** Security Automation | Scripting | Log Analysis | File Processing  
**Tools Used:** Python 3  
**Skills:** Functions | Conditional Logic | Loops | File Operations | Regular Expressions | Data Parsing  

<br><br>

## Objective

Demonstrate understanding and practical application of Python concepts for cybersecurity, including automation, data parsing, conditional logic, iterative statements, and file operations – essential skills for log analysis, threat detection, and system monitoring.

<br><br>

## 1. Module Structure

| Section | Concepts Covered | Cybersecurity Application |
|---------|-----------------|--------------------------|
| 1 | Comments, functions, conditionals, loops | Login attempt validation, access control |
| 2 | User-defined functions, built-in functions, imports | Reusable security tools, data analysis |
| 3 | String/list methods, regex, concatenation | Log parsing, pattern matching |
| 4 | File operations, parsing | Allow list updates, log processing |

<br><br>

## 2. Section 1: Python Fundamentals

**Concepts:** Comments, Functions, Conditional Statements, Iterative Statements

### Comments

```python
# Single-line comment - explains code purpose
"""
Multi-line comment / Docstring
Used for function documentation
"""
```

### Conditional Statements (if, elif, else)
| Keyword | Purpose | Cybersecurity Use Case |
|---------|---------|----------------------|
| `if` | Execute if condition true | Check if login attempts exceeded limit |
| `elif` | Else-if chain | Multi-condition user role checks |
| `else` | Execute if no conditions true | Default deny access |
| `and` | Both conditions true | Username AND IP match |
| `or` | At least one condition true | Admin OR manager access |
| `not` | Negate condition | NOT on blocklist |

```python
# Login validation example
if username == "bmoreno" and login_attempts < 5:
    print("Access granted")
elif status == 500:
    print("Server error - log this incident")
else:
    print("Access denied - unauthorized user")
```


### Iterative Statements (for, while)
| Loop Type | Use Case | Example |
|-----------|----------|---------|
| `for` | Iterate through known sequence | Process list of users |
| `while` | Loop until condition changes | Retry login attempts |
| `break` | Exit loop early | Stop after finding threat |
| `continue` | Skip to next iteration | Skip whitelisted IPs |

```python
# Iterate through user list
for user in ["bmoreno", "tshah", "elarson"]:
    print(f"Checking logs for: {user}")

# Track login attempts
while login_attempts < 5:
    login_attempts += 1
    print(f"Attempt {login_attempts} of 5")
```

### User-Defined Functions
```python
def calculate_fails(total_attempts, failed_attempts):
    """Calculate failure percentage for security metrics"""
    fail_percentage = failed_attempts / total_attempts
    return fail_percentage

# Function call
failure_rate = calculate_fails(50, 5)
print(f"Failure rate: {failure_rate * 100}%")
```


### Built-in Functions
| Function | Purpose | Example | Output |
|----------|---------|---------|--------|
| `print()` | Display output | `print("Alert!")` | Alert! |
| `type()` | Get data type | `type(True)` | `<class 'bool'>` |
| `range()` | Generate sequence | `range(1, 10)` | 1-9 |
| `max()` | Find maximum | `max(10, 15, 5)` | 15 |
| `min()` | Find minimum | `min(10, 15, 5)` | 5 |
| `sorted()` | Sort sequence | `sorted([10, 15, 5])` | [5, 10, 15] |

### Importing Modules
```python
# Import entire module
import statistics

# Import specific functions
from statistics import mean, median

# Usage
data = [10, 20, 30, 40, 50]
print(mean(data))    # 30
print(median(data))  # 30
```


## 3. Section 2: Functions and Modules
Concepts: User-defined Functions, Built-in Functions, Importing Modules

### Function Design Pattern
```python
def function_name(parameters):
    """Docstring describing function"""
    # Function body
    return output_value
```


### Cybersecurity Function Examples
```python
# Validate login credentials
def validate_login(username, password_hash, attempts):
    if attempts >= 5:
        return "Account locked"
    elif username in allowed_users and verify_hash(password_hash):
        return "Access granted"
    else:
        return "Access denied"

# Calculate threat score
def calculate_threat_score(failed_logins, suspicious_ports, anomaly_score):
    return (failed_logins * 2) + (suspicious_ports * 3) + (anomaly_score * 5)
```


## 4. Section 3: Strings, Lists, and Regular Expressions
Concepts: String Methods, List Methods, Regular Expressions, Advanced Syntax

### String Methods
| Method | Purpose | Example | Output |
|--------|---------|---------|--------|
| `.upper()` | Convert to uppercase | `"security".upper()` | `"SECURITY"` |
| `.lower()` | Convert to lowercase | `"SECURITY".lower()` | `"security"` |
| `.index()` | Find position | `"security".index("c")` | 2 |

### List Methods
| Method | Purpose | Example |
|--------|---------|---------|
| `.append()` | Add to end | `username_list.append("btang")` |
| `.insert()` | Insert at index | `username_list.insert(2, "wjaffrey")` |
| `.remove()` | Remove first match | `username_list.remove("elarson")` |
| `.index()` | Find position | `username_list.index("tshah")` |


```python
# User list management (access control)
username_list = ["elarson", "fgarcia", "tshah"]
username_list.insert(2, "wjaffrey")  # Add new hire
username_list.remove("elarson")      # Remove departed employee
username_list.append("btang")        # Add contractor
print(username_list.index("tshah"))  # Find user position
```

### String and List Operations
| Operation | Syntax | Example | Result |
|-----------|--------|---------|--------|
| Concatenation | `+` | `"IT" + "nwp12"` | `"ITnwp12"` |
| Bracket notation | `[]` | `users[2]` | Third element |
| Slicing | `[start:end]` | `"security"[0:4]` | `"secu"` |


### Regular Expressions (re module)
| Pattern | Meaning | Example Match |
|---------|---------|---------------|
| `\w` | Word character (a-z, A-Z, 0-9, _) | a, Z, 9, _ |
| `\d` | Digit (0-9) | 0, 1, 2 |
| `.` | Any character (except newline) | a, , ! |
| `\s` | Whitespace | space, tab, newline |
| `+` | One or more | `\w+` = one or more word chars |
| `*` | Zero or more | `\d*` = zero or more digits |
| `{}` | Exact count | `\d{3}` = exactly 3 digits |


```python
import re

# Extract words from log entry
words = re.findall(r"\w+", "a53-32c .E")
print(words)  # ['a53', '32c', 'E']

# Extract all digits from IP address log
digits = re.findall(r"\d", "a53-32c .E")
print(digits)  # ['5', '3', '3', '2']

# Extract IP addresses from log
log_line = "Failed login from 192.168.1.100"
ip_addresses = re.findall(r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", log_line)
print(ip_addresses)  # ['192.168.1.100']
```


## 5. Section 4: File Operations and Parsing
Concepts: File Operations, Parsing (.split(), .join())

| Mode | Description | Use Case |
|------|-------------|----------|
| `"r"` | Read (default) | Read log files |
| `"w"` | Write (overwrites) | Create allow list |
| `"a"` | Append (adds to end) | Add to audit log |
| `"x"` | Exclusive creation | Create new file |


```python
# Reading a file
with open("login_attempts.txt", "r") as file:
    file_text = file.read()
    print(file_text)

# Appending to a log file
with open("access_log.txt", "a") as file:
    file.write("jrafael - login success - 2024-01-15\n")

# Writing a new allow list
with open("allow_list.txt", "w") as file:
    file.write("elarson,bmoreno,tshah")
```


### Parsing with .split() and .join()
| Method | Purpose | Example |
|--------|---------|---------|
| `.split()` | String → List | `"a,b,c".split(",")` → `['a','b','c']` |
| `.join()` | List → String | `",".join(['a','b','c'])` → `"a,b,c"` |


```python
# Parse comma-separated allow list
approved_users = "elarson,bmoreno,tshah".split(",")
print(approved_users)  # ['elarson', 'bmoreno', 'tshah']

# Parse space-separated removed users
removed_users = "wjaffrey jsoto abernard".split()
print(removed_users)  # ['wjaffrey', 'jsoto', 'abernard']

# Rebuild allow list as string
approved_users_string = ",".join(["elarson", "bmoreno", "tshah"])
print(approved_users_string)  # "elarson,bmoreno,tshah"
```


## 6. Cybersecurity Script Examples
Example 1: Update Allow List
```python
# Remove IP addresses from allow list
def update_allow_list(allow_list_file, remove_list_file):
    # Read current allow list
    with open(allow_list_file, "r") as file:
        allow_list = file.read().split()
    
    # Read IPs to remove
    with open(remove_list_file, "r") as file:
        remove_list = file.read().split()
    
    # Remove matching IPs
    for ip in remove_list:
        if ip in allow_list:
            allow_list.remove(ip)
    
    # Write updated allow list
    with open(allow_list_file, "w") as file:
        file.write("\n".join(allow_list))
    
    return allow_list

# Usage
updated_list = update_allow_list("allow_list.txt", "remove_list.txt")
```


### Example 2: Analyze Login Attempts
```python
# Analyze failed login attempts from log file
def analyze_failed_logins(log_file, threshold=5):
    failed_attempts = {}
    
    with open(log_file, "r") as file:
        for line in file:
            if "Failed password" in line:
                # Extract username using regex
                import re
                match = re.search(r"for user (\w+)", line)
                if match:
                    username = match.group(1)
                    failed_attempts[username] = failed_attempts.get(username, 0) + 1
    
    # Flag accounts exceeding threshold
    suspicious = {user: count for user, count in failed_attempts.items() 
                  if count >= threshold}
    
    return suspicious

# Usage
suspicious_accounts = analyze_failed_logins("auth.log", threshold=5)
print(f"Suspicious accounts: {suspicious_accounts}")
```


### Example 3: Parse HTTP Log
```python
# Extract IP addresses and status codes from web log
def parse_web_log(log_file):
    import re
    ip_pattern = r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"
    status_pattern = r'" (\d{3}) '
    
    requests = []
    
    with open(log_file, "r") as file:
        for line in file:
            ip = re.findall(ip_pattern, line)
            status = re.findall(status_pattern, line)
            
            if ip and status:
                requests.append({
                    "ip": ip[0],
                    "status": int(status[0])
                })
    
    # Count errors (4xx, 5xx)
    errors = [r for r in requests if r["status"] >= 400]
    
    return {
        "total_requests": len(requests),
        "error_count": len(errors),
        "error_rate": len(errors) / len(requests) if requests else 0
    }

# Usage
stats = parse_web_log("access.log")
print(f"Error rate: {stats['error_rate'] * 100}%")
```


## 7. Python-Cybersecurity Mapping
| Python Concept | Cybersecurity Application |
|----------------|--------------------------|
| Conditional statements | Access control decisions, alert thresholds |
| Loops (for, while) | Processing log files, iterating through user lists |
| Functions | Reusable threat detection modules |
| File operations | Reading/writing allow lists, audit logs |
| Regular expressions | Extracting IPs, usernames, timestamps from logs |
| String methods | Normalizing log entries (`.upper()`, `.lower()`) |
| List methods | Managing user/IP allow/block lists |
| `.split()` / `.join()` | Parsing CSV logs, formatting output |


## 8. Skills Demonstrated
| Skill | Application |
|-------|-------------|
| Conditional logic | Login validation, access control decisions |
| Iterative processing | Looping through user lists, log entries |
| Function creation | Reusable security analysis tools |
| File I/O | Reading/writing allow lists, audit logs |
| Regular expressions | Pattern matching in log files |
| Data parsing | Splitting/joining strings for data extraction |
| Module imports | Using statistics, re modules |


## 9. How to Run Python Scripts
### Prerequisites
- Python 3 installed (python --version to verify)
- Script files in same directory as input files

### Execution Commands
```bash
# Basic execution
python filename.py

# With input redirection
python parse_logs.py < access.log

# With arguments (advanced)
python analyze_threats.py --threshold 5 --input auth.log
Example Workflow
bash
# Navigate to project folder
cd /home/analyst/python_scripts

# Run allow list update script
python update_allow_list.py

# Run log analysis script
python analyze_failed_logins.py
```


## 10. Python Quick Reference Card
### Conditionals
```python
if condition:
    action
elif other_condition:
    other_action
else:
    default_action
```


### Loops
```python
for item in sequence:
    process(item)

while condition:
    action
    update_condition
```


### Functions
```python
def function_name(param1, param2):
    result = param1 + param2
    return result
```


### File Operations
```python
with open("file.txt", "r") as f:
    content = f.read()

with open("file.txt", "w") as f:
    f.write("data")
```


### Regex Patterns
```python
import re
re.findall(r"\d+", text)     # All digits
re.findall(r"\w+", text)     # All words
re.findall(r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", text)  # IP addresses
```


### String/List Operations
```python
text.upper()                 # Uppercase
text.lower()                 # Lowercase
text.split(",")              # Split by comma
",".join(list)               # Join with comma
list.append(item)            # Add to end
list.remove(item)            # Remove item
```


## 11. Reflection
This module helped consolidate fundamental Python concepts while applying them to cybersecurity-related scenarios.

### Key takeaways:

| Concept | Insight |
|---------|---------|
| Conditional logic | Essential for access control and alert thresholds |
| Loops | Enable processing of large log files efficiently |
| Functions | Promote code reuse for security tools |
| File operations | Critical for updating allow lists and audit logs |
| Regular expressions | Most powerful tool for log parsing |
| String/list methods | Simplify data normalization and management |


### Confidence gained:
- Automating routine security tasks
- Building scripts for incident response
- Parsing logs to extract Indicators of Compromise (IoCs)

Demonstrates: Python proficiency for security automation, log analysis, and operational efficiency.

## 12. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Syntax | Rules governing code structure |
| Function | Reusable block of code |
| Parameter | Input passed to function |
| Return value | Output from function |
| Conditional | Code that executes based on conditions (if/else) |
| Iteration | Repeating code (loops) |
| List | Ordered, mutable collection |
| String | Sequence of characters |
| Regex | Pattern matching language |
| Parse | Extract information from data |
| File I/O | Reading from/writing to files |


## 13. Next Steps for Python in Cybersecurity
| Skill Area | Learning Path |
|------------|---------------|
| Log analysis | Parse syslog, auth.log, web server logs |
| Network automation | Use socket library for port scanning |
| API integration | Query VirusTotal, Shodan via REST APIs |
| Forensics | Parse PCAP files with scapy |
| Incident response | Build automated triage scripts |
| Threat hunting | Process large datasets with pandas |


















<br><br><br><br>

---

<br><br><br><br>













# Lab 17: Put It to Work – Prepare for Cybersecurity Jobs

**Focus Area:** Professional Development | Log Analysis | Threat Detection | Generative AI  
**Tools Used:** SIEM Concepts | TCREI Prompting Framework   
**Skills:** Log Analysis | Risk Assessment | Professional Networking | AI Prompt Engineering | Security Awareness Training  

<br><br>

## Objective

Simulate real-world responsibilities of a junior cybersecurity analyst, including log analysis, professional development through security organizations, and leveraging generative AI for security awareness.

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Key Skills |
|----------|-------|------------|
| 1 | Analyze event logs | Threat identification, risk assessment |
| 2 | Explore cybersecurity organizations | Career planning, professional development |
| 3 | Use generative AI for security awareness | Prompt engineering, content creation |

<br><br>

## 2. Activity 1: Analyze Event Logs

**Objective:** Analyze a system log file to identify abnormal behavior, potential security threats, and policy violations – simulating real-world SOC monitoring.

### Log Sample

| Timestamp | User | Source IP | Event Type |
|-----------|------|-----------|------------|
| 2025-07-30 08:15:00 | guest | 10.0.0.100 | Login_Failed |
| 2025-07-30 08:20:20 | John.Doe | 192.168.1.5 | File_Access |
| 2025-07-30 08:30:40 | admin | 203.0.113.25 | Login_Success |

### Suspicious Events Identified

| Event | Risk Level | Indicator | Potential Threat |
|-------|------------|-----------|------------------|
| Multiple failed login attempts | 🟠 Medium | Repeated failures from single IP | Brute-force attack |
| Sensitive file exposure | 🔴 High | Financial file copied to public location | Data exfiltration / insider threat |
| Unusual admin login | 🔴 High | Admin login from external IP | Account compromise |

### Risk Assessment Matrix

| Event | Likelihood | Impact | Risk Score | Priority |
|-------|------------|--------|------------|----------|
| External admin login | Medium (2) | Critical (3) | **6** | High |
| Sensitive file exposure | Medium (2) | High (3) | **6** | High |
| Repeated failed logins | High (3) | Medium (2) | **6** | High |

### Recommended Actions

| Priority | Action | Responsible |
|----------|--------|-------------|
| **Immediate** | Investigate external admin login legitimacy | SOC Analyst |
| **Immediate** | Reset admin credentials if compromise suspected | IT Security |
| **High** | Restrict access to sensitive directories | Security Engineer |
| **High** | Block suspicious IP address (203.0.113.25) | Network Admin |
| **Medium** | Implement alerting for repeated login failures | SIEM Engineer |

### SOC Investigation Workflow

| Stage | Objective | Key Activities / Actions |
|-------|-----------|--------------------------|
| Log Entry Received | Detect event | Event detected in system logs |
| Initial Triage | Identify suspicious logs | Identify abnormal patterns, classify event type |
| Risk Assessment | Determine severity | Evaluate impact and likelihood, assign priority level |
| Investigation | Confirm incident details | Correlate logs, analyze behavior, timeline analysis, check historical activity |
| Response | Mitigate threat | Execute containment, block IoCs |
| Documentation | Record findings | Document incident, report, escalate if needed |


<br><br>

## 3. Activity 2: Explore Cybersecurity Organizations

**Objective:** Research professional security organizations aligned with career interests.

### Part 1: Security Interests

| Interest Area | Description | Relevant Roles |
|---------------|-------------|----------------|
| Incident response | Detecting and responding to security breaches | SOC Analyst, Incident Responder |
| Threat detection | Identifying malicious activity through monitoring | Threat Hunter, SOC Analyst |
| Data protection | Safeguarding sensitive information | DLP Analyst, Security Engineer |
| SIEM tools | Log aggregation and alerting | SIEM Administrator, SOC Analyst |

### Part 2: Professional Organizations

| Organization | Focus Area | Certifications | Resources |
|--------------|------------|----------------|-----------|
| **ISACA** | IT governance, risk management, cybersecurity | CISA, CISM, CRISC | Frameworks, publications, conferences |
| **(ISC)²** | Information security certifications and standards | CISSP, CCSP, SSCP | Best practices, continuing education |
| **SANS Institute** | Hands-on cybersecurity training and research | GIAC certifications | Research papers, training courses |

### Organization Comparison

| Criteria | ISACA | (ISC)² | SANS |
|----------|-------|--------|------|
| **Primary focus** | Governance & audit | Broad security | Technical training |
| **Best for** | Risk/compliance roles | Management roles | Technical/ops roles |
| **Entry point** | CISA certification | SSCP certification | GIAC certifications |
| **Learning style** | Framework-based | Knowledge-based | Hands-on/practical |
| **Cost** | Moderate | Moderate | High |

### Career Pathway Mapping

#### SOC Track
SOC Analyst → Incident Responder → IR Manager  
- SOC Analyst: (ISC)² SSCP, SANS SEC401  
- Incident Responder: GIAC, ISACA CISA  
- IR Manager: (ISC)² CISSP, ISACA CISM  

#### Security Engineering Track
Security Analyst → Security Engineer → Security Architect  
- Security Analyst: CompTIA Security+, ISACA CSX  
- Security Engineer: SANS/GIAC, ISACA CRISC  
- Security Architect: (ISC)² CISSP, SANS MGT


<br><br>

## 4. Activity 3: Use Generative AI for Security Awareness

**Objective:** Use generative AI with the TCREI prompting framework to create a phishing and malware awareness guide.

### TCREI Framework Explained

| Component | Meaning | Application |
|-----------|---------|-------------|
| **T**ask | Define what you want the AI to do | "Create a phishing awareness guide" |
| **C**ontext | Provide background and constraints | "For non-technical employees" |
| **E**valuate | Assess output quality | Check clarity, completeness, accuracy |
| **R**efine | Iterate on prompt | Adjust wording, add specificity |
| **I**terate | Repeat process | Multiple rounds of improvement |

### Prompt Evolution

| Iteration | Prompt | Issue | Refinement |
|-----------|--------|-------|------------|
| 1 | "Create a phishing guide" | Too vague, generic output | Added target audience |
| 2 | "Create phishing guide for employees" | Missing structure | Added format requirements |
| 3 | "Create phishing guide for non-technical employees with bullet points" | Lacked examples | Added real-world examples |
| **Final** | See below | Comprehensive, actionable | N/A |

### Final Prompt

> *"As a cybersecurity analyst, create a clear and comprehensive reference guide on identifying phishing emails and malware threats for non-technical employees. Include common phishing indicators, malware warning signs, real-world examples, and best practices for detection and prevention. Format the guide using bullet points and ensure the tone is simple and easy to understand."*

### Generated Output Structure
#### PHISHING & MALWARE AWARENESS GUIDE

| Section | Key Points |
|---------|------------|
| Phishing Indicators | Suspicious sender addresses, Urgent or threatening language, Mismatched URLs, Unexpected attachments | 
| Malware Warning Signs | Slow system performance, Unexpected pop-ups, Unusual network activity, File changes or encryption |
| Real-World Examples | Fake invoice scam, CEO fraud (whaling), Credential harvesting |
| Prevention Techniques | Verify before clicking, Use MFA available, Report suspicious emails, Keep software updated |


### AI Prompt Engineering Best Practices

| Practice | Example |
|----------|---------|
| **Assign a role** | "As a cybersecurity analyst..." |
| **Define audience** | "For non-technical employees" |
| **Specify format** | "Using bullet points" |
| **Request examples** | "Include real-world examples" |
| **Set tone** | "Simple and easy to understand" |

<br><br>

## 5. Skills Demonstrated

| Skill | Application in Lab |
|-------|-------------------|
| Log analysis | Identified failed logins, file access anomalies, external admin access |
| Threat identification | Recognized brute-force, data exfiltration, account compromise |
| Risk assessment | Prioritized events by likelihood and impact |
| Professional development | Researched ISACA, (ISC)², SANS for career alignment |
| AI prompt engineering | Applied TCREI framework for iterative improvement |
| Content creation | Generated security awareness guide for non-technical audience |

<br><br>

## 6. Junior SOC Analyst – Role Breakdown

### Typical Responsibilities

| Responsibility | Description | Lab Alignment |
|----------------|-------------|---------------|
| **Log monitoring** | Review system logs for anomalies | Activity 1 log analysis |
| **Alert triage** | Prioritize and investigate alerts | Risk assessment |
| **Incident documentation** | Record findings and actions | Recommendations documented |
| **Threat research** | Stay current on attack trends | Organization research |
| **Security awareness** | Help train employees | Activity 3 guide |

### Required Skills

| Skill Category | Specific Skills | Lab Demonstrated |
|----------------|-----------------|------------------|
| **Technical** | Log analysis, SIEM tools, networking | Activity 1 |
| **Analytical** | Pattern recognition, risk assessment | Risk matrix |
| **Communication** | Documentation, training content | Activity 3 guide |
| **Professional** | Continuous learning, certifications | Organization research |

<br><br>

## 7. Security Certification Pathway

### Entry Level

| Certification | Provider | Focus | Lab Relevance |
|---------------|----------|-------|---------------|
| CompTIA Security+ | CompTIA | Broad security fundamentals | All activities |
| GSEC | SANS/GIAC | Security essentials | Network analysis |
| SSCP | (ISC)² | Security operations | Log analysis |

### Mid Level

| Certification | Provider | Focus | Career Path |
|---------------|----------|-------|-------------|
| CySA+ | CompTIA | Threat detection, analysis | SOC Analyst |
| GCIH | SANS/GIAC | Incident handling | Incident Responder |
| CISA | ISACA | Audit, risk | Compliance Analyst |

### Advanced

| Certification | Provider | Focus | Career Path |
|---------------|----------|-------|-------------|
| CISSP | (ISC)² | Security management | Security Manager |
| CISM | ISACA | Information security management | GRC Manager |
| GPEN | SANS/GIAC | Penetration testing | Pen Tester |

<br><br>

## 8. TCREI Framework – Quick Reference
### TCREI Prompting Framework (Unified Guide)

| Component | Step | Purpose | Meaning / Key Question | Example |
|-----------|------|---------|------------------------|---------|
| T – Task | Task | Define objective | What should the AI do? | "Explain phishing attacks" |
| C – Context | Context | Provide background | What does the AI need to know? | "For beginners in cybersecurity" |
| R – Role | Role | Assign persona | Who should the AI act as? | "Act as a SOC analyst" |
| E – Evaluate | Evaluate | Assess output | Is it accurate, clear, and useful? | Check accuracy, clarity, completeness |
| I – Iterate | Iterate | Improve prompt | How can it be refined? | Add details, adjust tone, re-run prompt |

#### Example Prompt Using TCREI

**T:** Explain phishing attacks  
**C:** For non-technical employees  
**R:** Act as a cybersecurity trainer  
**E:** Ensure clarity and real-world examples  
**I:** Simplify language and add examples if needed


<br><br>


## 9. Reflection

This lab strengthened my ability to perform core cybersecurity tasks and prepare for professional roles.

**Activity 1 takeaways:**
- Log analysis requires pattern recognition and contextual understanding
- Risk assessment helps prioritize response actions
- External admin access is a critical red flag

**Activity 2 takeaways:**
- Professional organizations provide career pathways and certifications
- Different organizations serve different career tracks (governance vs. technical)
- Continuous learning is essential in cybersecurity

**Activity 3 takeaways:**
- TCREI framework improves AI output quality
- Iteration is key to effective prompt engineering
- Generative AI can accelerate security awareness content creation

**Demonstrates:** SOC analysis skills, professional development awareness, and modern AI tool application.

<br><br>

## 10. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| **SOC** | Security Operations Center – centralized security monitoring team |
| **SIEM** | Security Information and Event Management – log aggregation platform |
| **TCREI** | Task, Context, Role, Evaluate, Iterate – AI prompting framework |
| **ISACA** | Information Systems Audit and Control Association |
| **(ISC)²** | International Information System Security Certification Consortium |
| **SANS** | System Administration, Networking, and Security Institute |
| **CISA** | Certified Information Systems Auditor |
| **CISM** | Certified Information Security Manager |
| **CISSP** | Certified Information Systems Security Professional |
| **Brute-force** | Repeated login attempts to guess credentials |

<br><br>

## 11. Professional Development Plan Template

```
## My Cybersecurity Career Plan

**Target Role:** SOC Analyst / Cybersecurity Analyst

**Short-term (0-6 months):**
- [ ] Complete CompTIA Security+ certification
- [ ] Build portfolio with 10+ labs (completed: 16)
- [ ] Network with local cybersecurity groups

**Medium-term (6-12 months):**
- [ ] Earn CySA+ or SSCP certification
- [ ] Apply for entry-level SOC positions
- [ ] Join ISACA or (ISC)² as student member

**Long-term (1-3 years):**
- [ ] Earn CISSP or CISM
- [ ] Specialize in incident response or threat hunting
- [ ] Mentor junior analysts
```

<br><br>

## 12. Quick Reference – Security Organizations
| Organization | Website | Best For | Entry Certification |
|--------------|---------|----------|---------------------|
| ISACA | isaca.org | Governance, risk, audit | CISA |
| (ISC)² | isc2.org | Broad security knowledge | SSCP |
| SANS | sans.org | Hands-on technical skills | GIAC (GSEC) |
| CompTIA | comptia.org | Foundational IT security | Security+ |
| EC-Council | eccouncil.org | Ethical hacking | CEH |

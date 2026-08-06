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


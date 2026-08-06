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


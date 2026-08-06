# Project 4: Documenting a Security Incident - Ransomware Attack Response

## Project Overview
**Role Context:** SOC Analyst / Incident Handler  
**Objective:** Document a ransomware security incident using professional incident documentation practices, including the 5 W's framework (Who, What, When, Where, Why), and demonstrate proficiency with security analysis tools.  
**Techniques Used:** Incident documentation (NIST SP 800-61), Wireshark packet analysis, tcpdump network capture, VirusTotal hash analysis, root cause analysis.

<br><br><br>

## Scenario
A small U.S. health care clinic experienced a ransomware attack that encrypted critical patient and operational files. As an incident handler, I am responsible for documenting the incident from detection through containment, analyzing the attack vector, and recommending preventive measures. Additionally, I practiced using industry-standard tools (Wireshark, tcpdump, VirusTotal) to build hands-on investigation skills.

<br><br><br>

## Incident Handler's Journal

### Journal Entry #1: Ransomware Incident Initial Documentation

| Field | Details |
| :--- | :--- |
| **Date** | July 23, 2024 |
| **Incident ID** | INC-2024-001 |
| **Description** | Ransomware security incident causing system-wide file encryption at a healthcare company |
| **Severity** | 🔴 Critical |
| **Tool(s) Used** | None (initial documentation only) |

<br><br>

### Ransomware Attack Timeline (Visual)
```
timeline
    title Ransomware Incident Timeline
    section July 23, 2024 - 9:00 AM
        Initial Detection
        : Employees report encrypted files
        : Ransom note discovered
    section July 23, 2024 - 9:30 AM
        Containment
        : Affected systems isolated
        : Network segmentation activated
    section July 23, 2024 - 11:00 AM
        Analysis
        : Phishing email identified
        : Malicious attachment traced
    section July 23, 2024 - 2:00 PM
        Eradication
        : Malware removed
        : Patches applied
    section July 24, 2024+
        Recovery
        : Data restored from backups
        : Security awareness training scheduled
```

<br><br>

#### The 5 W's Analysis

| Element | Details |
| :--- | :--- |
| **Who** | An organized group of unethical hackers (threat actor) |
| **What** | Ransomware security incident causing system-wide file encryption |
| **When** | Tuesday at 9:00 a.m. (business hours - maximum disruption) |
| **Where** | Small U.S. health care clinic |
| **Why** | Attackers gained initial access via a phishing email with a malicious attachment. Once executed, the ransomware deployed and encrypted critical files. A ransom demand was issued for decryption keys. |

<br><br>

#### Root Cause Analysis
Phishing Email → Malicious Attachment → User Execution → Ransomware Deployment → File Encryption → Ransom Demand

<br><br>

#### Critical Questions for Response

| Question | Initial Analysis |
| :--- | :--- |
| **How could the healthcare company prevent this type of incident in the future?** | Security awareness training, email filtering, application allow-listing, regular offline backups |
| **Should the company pay the ransom?** | Generally NOT recommended. Paying funds criminal activity and does not guarantee data recovery. Restore from backups instead. |

<br><br><br>

### Journal Entry #2: Network Traffic Analysis with Wireshark

| Field | Details |
| :--- | :--- |
| **Date** | July 25, 2024 |
| **Description** | Analyzing a packet capture (pcap) file to identify malicious network activity |
| **Tool(s) Used** | Wireshark |
| **Purpose** | Learn to capture and analyze network traffic for signs of compromise |

<br><br>

#### Activity Summary

| Activity | Outcome |
| :--- | :--- |
| **Task** | Open and analyze a pcap file using Wireshark |
| **Challenge** | Interface initially overwhelming with many columns and filters |
| **Learning** | Wireshark displays source/destination IPs, protocols, packet payloads, and timestamps |

<br><br>

#### Key Takeaways

```
- Wireshark enables real-time network traffic inspection
- Filters (e.g., `http`, `tcp.port==443`, `ip.src==192.168.1.1`) help isolate relevant traffic
- Packet-level analysis can reveal command-and-control (C2) communication
- Unusual outbound connections may indicate data exfiltration
```

<br><br>

#### Security Impact
Network traffic analysis is critical for detection:
- Identifying malware beaconing behavior
- Detecting unauthorized data transfers
- Finding anomalous protocols or ports

<br><br><br>

### Journal Entry #3: Command-Line Packet Capture with tcpdump
| Field | Details |
|-------|---------|
| Date | July 25, 2024 |
| Description | Capturing the first packet using tcpdump command-line tool |
| Tool(s) Used | tcpdump |
| Environment | Linux command line |

<br><br>

#### Activity Summary
| Activity | Outcome |
|----------|---------|
| Task | Use tcpdump to capture live network traffic |
| Challenge | Unfamiliar command-line syntax and flags |
| Resolution | Carefully reviewed instructions and repeated steps until successful |

<br><br>

#### Commands Practiced
```bash
# List available network interfaces
sudo tcpdump -D

# Capture packets on specific interface
sudo tcpdump -i eth0

# Capture limited number of packets
sudo tcpdump -c 10 -i eth0

# Write capture to file for later analysis
sudo tcpdump -i eth0 -w capture.pcap

# Read capture file
sudo tcpdump -r capture.pcap
```

<br><br>

#### Key Takeaways
| Concept | Insight |
|---------|---------|
| Command-line proficiency | Essential for security analysts working on headless servers |
| tcpdump vs Wireshark | tcpdump for capture (lightweight); Wireshark for analysis (GUI) |
| Use cases | Live incident response, forensic acquisition, network troubleshooting |


<br><br><br>

### Journal Entry #4: Malicious File Hash Investigation with VirusTotal
| Field | Details |
|-------|---------|
| Date | July 27, 2024 |
| Description | Investigating a suspicious file hash from an email attachment |
| Tool(s) Used | VirusTotal |
| Alert Time | 1:20 p.m. |
| Affected Asset | Employee's computer at a financial services company |

<br><br>

#### The 5 W's Analysis
| Element | Details |
|---------|---------|
| Who | Unknown malicious actor |
| What | Email containing a malicious file attachment |
| When | Alert received at 1:20 p.m. |
| Where | Employee's computer at a financial services company |
| Why | Employee downloaded and executed the malicious attachment |

<br><br>

#### Technical Details
| Attribute | Value |
|-----------|-------|
| File Hash (SHA-256) | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` |
| Detection Method | VirusTotal scan against 60+ antivirus engines |
| Finding | Hash confirmed malicious (number of detections varies by vendor) |


<br><br>

#### VirusTotal Investigation Steps
```
1. Copy the suspicious SHA-256 hash
2. Navigate to virustotal.com
3. Paste hash into search bar
4. Review detection ratio (e.g., 35/65 engines detect as malicious)
5. Examine:
   - File type and size
   - First seen date
   - Associated filenames
   - Behavior analysis (if available)
   - Community comments
```

<br><br>

#### Indicators of Compromise (IOCs)

Based on the investigation, the following IOCs were identified:

| Type | Value | Source |
| :--- | :--- | :--- |
| **SHA-256** | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` | VirusTotal (Entry #4) |
| **Email Sender** | `billing@fake-healthcare[.]com` | User report |
| **Attachment Name** | `INVOICE_07232024.exe` | Email log |
| **C2 Domain** | `malicious-c2[.]xyz` (example) | Wireshark analysis |

> **Note:** IOCs are critical for threat hunting and can be shared with security vendors or added to blocklists.

<br><br>

#### Prevention Recommendations
| Control | Implementation |
|---------|----------------|
| Security Awareness Training | Teach employees to verify unexpected attachments before opening |
| Email Filtering | Block known malicious attachments at gateway |
| Endpoint Detection (EDR) | Alert and block execution of known malicious hashes |
| Application Allow-listing | Only permit approved executables to run |

<br><br>

#### Skills Summary Table
| Skill | How Demonstrated |
|-------|------------------|
| Incident Documentation | 5 W's framework applied to ransomware incident (Entry #1) |
| Network Traffic Analysis | Wireshark packet capture analysis (Entry #2) |
| Command-Line Investigation | tcpdump packet capture on Linux (Entry #3) |
| Threat Intelligence | VirusTotal hash lookup for malicious file (Entry #4) |
| Root Cause Analysis | Traced ransomware to phishing email vector |
| Prevention Planning | Recommended security controls for each finding |

<br><br><br>

## Reflection: Challenges and Growth
### Most Challenging Activity
| Activity | Challenge | How Overcome |
|----------|-----------|---------------|
| tcpdump command-line usage | Unfamiliar syntax and flags | Repeated steps, careful instruction reading, practice |

<br><br>

### Understanding Growth
| Before This Project | After This Project |
|---------------------|-------------------|
| Incidents are just "something bad happened" | Incidents have a lifecycle: detection → analysis → containment → eradication → recovery |
| Tools are optional | Tools are essential: Wireshark, tcpdump, VirusTotal each serve specific purposes |
| Documentation is administrative | Documentation is critical for legal, operational, and improvement purposes |

<br><br>

### Favorite Tools / Concepts
| Tool/Concept | Why Interesting |
|--------------|-----------------|
| Wireshark | Visualizing network traffic makes abstract concepts tangible |
| tcpdump | Command-line power for live incident response |
| Network Traffic Analysis | Like solving a puzzle - finding malicious needles in legitimate haystacks |

<br><br><br>

## Conclusion
This project demonstrates my ability to professionally document security incidents using structured frameworks (5 W's) and industry-standard tools.

<br><br><br>

## Portfolio-Ready Evidence
| Competency | Evidence |
|------------|----------|
| Incident Documentation | Complete journal entry for ransomware attack |
| Network Analysis | Wireshark and tcpdump practice documentation |
| Threat Hunting | VirusTotal hash investigation |
| Root Cause Analysis | Phishing → Ransomware chain identified |
| Preventive Security | Actionable recommendations for each finding |

<br><br><br>

## Key Takeaway
"I can document a security incident from detection through analysis, using both GUI tools (Wireshark, VirusTotal) and command-line tools (tcpdump), while maintaining professional documentation standards required for legal and operational review."


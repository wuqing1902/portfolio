# Project Summary – 5 Cybersecurity Projects
 
**Total Projects:** 5  
**Primary Focus:** Security Automation, Incident Response, Vulnerability Assessment, Linux Security, SQL Investigation

<br><br><br>

## How to Use This Document

This summary provides a high-level overview of each project for quick reference. For detailed project reports, including code, queries, and complete analysis, navigate to `project.md` within this folder.

<br><br><br>

## Project 1: Applying Filters to SQL Queries for Security Incident Investigation

**Role Context:** SOC Analyst / Security Investigator  
**Tools:** MariaDB SQL  
**Framework:** NIST SP 800-61 (Incident Handling)

### Scenario

A series of suspicious events were reported. I used SQL to investigate unauthorized access attempts, filter geographic anomalies, and segment employee departments for targeted security patches.

### Key Queries and Findings

| Task | Query Logic | Result |
|------|-------------|--------|
| After-hours failed logins | `login_time > '18:00' AND success = 0` | 19 failed attempts between 6 PM and 2 AM |
| Incident date timeline | `login_date = '2022-05-09' OR login_date = '2022-05-08'` | 87 logins; 60% failure rate on May 8 |
| Non-Mexico logins | `country NOT LIKE 'MEX%'` | 42 logins from USA, Canada, UK (40 successful) |
| Marketing in East building | `department = 'Marketing' AND office LIKE 'East%'` | 11 employees identified |
| Finance or Sales departments | `department = 'Finance' OR department = 'Sales'` | 208 employees |
| All except IT | `department != 'Information Technology'` | 447 employees (IT excluded) |

### Skills Demonstrated

| Skill | Application |
|-------|-------------|
| Basic Filtering | `WHERE login_time > '18:00:00'` |
| Multiple Conditions (AND) | After-hours AND failed logins |
| Multiple Conditions (OR) | Multiple date ranges |
| Pattern Matching (LIKE + %) | `country NOT LIKE 'MEX%'`, `office LIKE 'East%'` |
| Exclusion (NOT / !=) | Excluding Mexico and IT department |

### Security Impact

- Provided actionable IP lists for blocking
- Traced attacker dwell time back 24 hours
- Triggered credential reset for affected accounts
- Enabled zero-false-positive software updates

<br><br><br>

## Project 2: File Permissions in Linux

**Role Context:** Security Analyst / Linux System Administrator  
**Tools:** Bash, chmod, ls -la  
**Framework:** Principle of Least Privilege (NIST SP 800-53 AC-6)

### Scenario

A research team requested a security review of their Linux environment. I reviewed existing file and directory permissions, identified violations, and applied appropriate restrictions.

### Investigation and Actions

| Step | Command | Purpose | Result |
|------|---------|---------|--------|
| 1 | `ls -la` | List all files with permissions | Identified overly permissive files |
| 2 | `chmod o-w project_k.txt` | Remove others' write access | `-rw-rw-rw-` → `-rw-rw-r--` |
| 3 | `chmod ug+r,u-w,g-w,o-rwx .project_x.txt` | Secure hidden file | `-rw--w----` → `-r--r-----` |
| 4 | `chmod 700 drafts` | Restrict directory to owner only | `drwx--x---` → `drwx------` |

### Permission String Interpretation

| Example | User | Group | Others | Security Implication |
|---------|------|-------|--------|----------------------|
| `-rw-rw-rw-` | read/write | read/write | read/write | Critical violation |
| `-rw-rw-r--` | read/write | read/write | read | Acceptable for collaboration |
| `-r--r-----` | read | read | none | Properly restricted |
| `drwx------` | read/write/execute | none | none | Owner-only access |

### Skills Demonstrated

| Skill | How Demonstrated |
|-------|------------------|
| Listing with Details | `ls -la` to view all files including hidden |
| Reading Permission Strings | Interpreted 10-character permission strings |
| Removing Permissions (Symbolic) | `chmod o-w` syntax |
| Multiple Changes at Once | `chmod ug+r,u-w,g-w,o-rwx` |
| Octal Notation | `chmod 700` for directory restriction |
| Hidden File Handling | Identified and secured `.project_x.txt` |

<br><br><br>

## Project 3: Vulnerability Assessment for a Small Business Database Server

**Role Context:** Vulnerability Analyst / Security Assessor  
**Framework:** NIST SP 800-30 Rev. 1  
**Risk Formula:** Likelihood × Severity

### Scenario

A small business operates a publicly accessible database server storing sensitive customer data, campaign information, and analytic data. I conducted a formal vulnerability assessment to identify security gaps and provide prioritized recommendations.

### Risk Assessment Matrix

| Threat Source | Threat Event | Likelihood | Severity | Risk Score | Priority |
|---------------|--------------|------------|----------|------------|----------|
| Hacker | Data exfiltration | 3 | 3 | **9** | Critical |
| Employee | Operational disruption | 2 | 3 | **6** | High |
| Customer | Data manipulation | 1 | 3 | **3** | Medium |

### Remediation Strategy

| Priority | Control | Implementation Timeline |
|----------|---------|------------------------|
| Critical | IP allow-listing, strong authentication, encryption at rest | Immediate |
| High | Least privilege, MFA, audit logging | Within 30 days |
| Medium | Input validation, RBAC | Within 90 days |

### Skills Demonstrated

- Applied NIST SP 800-30 Rev. 1 risk assessment framework
- Created risk matrix with qualitative scoring
- Prioritized remediation based on calculated risk scores
- Recommended specific, actionable security controls
- Documented findings in professional report format

<br><br><br>

## Project 4: Documenting a Security Incident - Ransomware Attack Response

**Role Context:** SOC Analyst / Incident Handler  
**Tools:** Wireshark, tcpdump, VirusTotal  
**Framework:** NIST SP 800-61, 5 W's

### Scenario

A small U.S. health care clinic experienced a ransomware attack that encrypted critical patient and operational files. I documented the incident from detection through containment and recommended preventive measures.

### The 5 W's Analysis

| Element | Details |
|---------|---------|
| Who | Organized group of unethical hackers |
| What | Ransomware causing system-wide file encryption |
| When | Tuesday at 9:00 a.m. (business hours) |
| Where | Small U.S. health care clinic |
| Why | Phishing email with malicious attachment |

### Root Cause Chain
Phishing Email → Malicious Attachment → User Execution →
Ransomware Deployment → File Encryption → Ransom Demand


### Tools Practiced

| Tool | Purpose | Key Command |
|------|---------|-------------|
| Wireshark | Packet analysis | Filters: `http`, `tcp.port==443` |
| tcpdump | Live capture | `sudo tcpdump -i eth0 -w capture.pcap` |
| VirusTotal | Hash investigation | SHA-256: `54e6ea47eb04634d3e87fd7787e2136...` |

### Skills Demonstrated

- Incident documentation using 5 W's framework
- Network traffic analysis with Wireshark
- Command-line packet capture with tcpdump
- Malicious file hash investigation with VirusTotal
- Root cause analysis (phishing → ransomware)
- Prevention planning with actionable recommendations

<br><br><br>

## Project 5: Update a File Through a Python Algorithm

**Role Context:** Security Automation Engineer / SOC Analyst  
**Tools:** Python 3  
**Techniques:** File I/O, list operations, string manipulation, error handling

### Scenario

Access to restricted content is controlled by an allow list of IP addresses. A separate remove list identifies IPs that should no longer have access. I created a Python algorithm to automate this process.

### Solution Architecture

1. Read `allow_list.txt` and `remove_list.txt`
2. Convert file contents into strings
3. Split both into IP lists
4. Remove matching IPs from allow list
5. Join updated list using newline `\n`
6. Write updated data back to `allow_list.txt`


### Solution Explaination

| Step | Operation | Python Technique |
|------|-----------|------------------|
| 1 | Read allow list | `with open(file, "r")` + `.read()` |
| 2 | Read remove list | `with open(file, "r")` + `.read()` |
| 3 | Convert to lists | `.split()` |
| 4 | Remove unauthorized IPs | List comprehension with `if not in` |
| 5 | Write updated list | `"\n".join()` + `with open(file, "w")` |
| 6 | Create backup | Timestamped file copy before modification |


### Execution Results

| Metric | Before | After |
|--------|--------|-------|
| IP count | 4 | 2 |
| Removed IPs | - | 192.168.1.10, 10.0.0.5 |
| Remaining IPs | - | 192.168.1.1, 172.16.0.1 |

### Skills Demonstrated

| Skill | Application |
|-------|-------------|
| File I/O | `with open()` for safe file handling |
| String manipulation | `.split()`, `.strip()`, `"\n".join()` |
| List operations | Iteration, membership (`in`), removal |
| Error handling | Try-except for missing files |
| Defensive programming | Backup before modification |
| Code organization | Functions, main guard, docstrings |

### Security Impact

- Reduced manual effort from hours to milliseconds
- Eliminated human error in allow list management
- Created audit trail through backup files
- Provided reproducible workflow for security team

<br><br><br>

## Skills Matrix Summary

| Skill Area | Project 1 | Project 2 | Project 3 | Project 4 | Project 5 |
|------------|-----------|-----------|-----------|-----------|-----------|
| SQL Querying | ✓ | | | | |
| Linux Permissions | | ✓ | | | |
| Risk Assessment | | | ✓ | | |
| Incident Response | | | | ✓ | |
| Python Automation | | | | | ✓ |
| Network Analysis | | | | ✓ | |
| Threat Intelligence | | | | ✓ | |
| Documentation | ✓ | ✓ | ✓ | ✓ | ✓ |

<br><br><br>

## Tools and Technologies Summary

| Category | Tools Used |
|----------|-------------|
| Database | MariaDB (SQL) |
| Operating System | Linux (Bash) |
| Network Analysis | Wireshark, tcpdump |
| Threat Intelligence | VirusTotal |
| Programming | Python 3 |
| Frameworks | NIST SP 800-30, NIST SP 800-61, NIST SP 800-53 |

<br><br><br>

## Portfolio-Ready Evidence Checklist

| Project | Deliverable |
|---------|-------------|
| Project 1 | SQL queries with before/after analysis |
| Project 2 | Permission changes with command documentation |
| Project 3 | Risk matrix with remediation plan |
| Project 4 | Incident journal + tool practice evidence |
| Project 5 | Production-ready Python script with error handling |

<br><br><br>

## Key Takeaways
**Project 1:** I can translate natural language incident reports into precise SQL queries and deliver actionable intelligence to response teams.

**Project 2:** I can audit Linux permissions, interpret 10-character strings, and apply least privilege using both symbolic and octal syntax.

**Project 3:** I can conduct formal vulnerability assessments using NIST methodology and prioritize remediation based on calculated risk scores.

**Project 4:** I can document security incidents professionally, analyze network traffic with Wireshark and tcpdump, and investigate malicious hashes with VirusTotal.

**Project 5:** I can write Python scripts that solve real security problems - automating allow list management, handling edge cases gracefully, and producing auditable output.

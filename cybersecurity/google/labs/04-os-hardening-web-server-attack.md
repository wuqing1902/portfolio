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


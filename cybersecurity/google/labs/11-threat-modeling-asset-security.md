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


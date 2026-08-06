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

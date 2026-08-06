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

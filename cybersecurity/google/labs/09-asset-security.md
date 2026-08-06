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

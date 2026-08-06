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


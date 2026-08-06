# Lab 1: Internal IT Audit Documentation – Botium Toys 

**Framework aligned:** NIST Cybersecurity Framework (CSF)  
**Skills:** Risk Scoring | Gap Analysis | Compliance Mapping | Control Assessment  

<br><br>

## Objective

Conduct an internal IT audit for Botium Toys to evaluate security posture, identify risks, assess controls, check compliance with regulatory standards, and provide actionable recommendations.

<br><br>

## 1. Scope & Goals

| Area | Description |
|------|-------------|
| **Scope** | Entire security program; all assets, systems, internal processes, controls; compliance with regulatory standards |
| **Goals** | Assess assets & controls → Identify gaps → Recommend fixes → Align with NIST CSF |

<br><br>

## 2. Risk Assessment

### Assets Inventory (Summary)
- Employee endpoints (desktops, laptops, smartphones, remote workstations)
- Internal network (customer, vendor, internal data)
- Storefront systems (on‑site & online inventory)
- Business systems (accounting, DB, telecom, ecommerce, inventory mgmt)
- Internet access, legacy systems, data storage

### Risk Summary
- No asset classification  
- Missing key controls (technical, admin, physical)  
- Unrestricted PII/SPII & cardholder access  
- No encryption, no disaster recovery plan, no intrusion detection system  

### Control Best Practices Considered
- Asset identification & classification  
- Controls to reduce breach likelihood  
- Business impact analysis  
- GDPR, PCI DSS, SOC alignment  

**Risk Score:** 8/10 (High) – High risk of data loss or regulatory penalties without corrective action.

<br><br>

## 3. Control Categories

| Category | Examples | Purpose |
|----------|----------|---------|
| Administrative | Password policy, least privilege, separation of duties | Define responsibilities & policies |
| Technical | Firewall, IDS/IPS, encryption, backups | Prevent/detect/correct incidents |
| Physical | Locks, CCTV, alarms, safes | Limit unauthorized physical access |

**Control Types:** Preventative | Detective | Corrective | Deterrent

<br><br>

## 4. Controls Assessment Checklist

| Status | Control | Explanation |
|--------|---------|-------------|
| Missing | Least Privilege | All employees have excessive access |
| Missing | Disaster Recovery Plans | No continuity plan |
| Missing | Strong Password Policies | Minimal requirements |
| Missing | Separation of Duties | CEO overlaps critical roles |
| Implemented | Firewall | Rules actively enforced |
| Missing | Intrusion Detection System (IDS) | Not deployed |
| Missing | Backups | Critical data not backed up |
| Implemented | Antivirus | Installed & monitored |
| Partial | Manual Monitoring & Legacy Maintenance | Exists but unscheduled |
| Missing | Encryption | No encryption for sensitive data |
| Missing | Password Management System | Not used |
| Implemented | Physical Locks | Offices, storefront, warehouse |
| Implemented | CCTV | Installed & working |
| Implemented | Fire Detection/Prevention | Alarms & sprinklers functional |

<br><br>

## 5. Compliance Checklist

| Standard | Status | Requirement | Gap |
|----------|--------|-------------|-----|
| PCI DSS | Fail | Restrict cardholder data access | All employees have access |
| PCI DSS | Fail | Secure data processing & transmission | No encryption |
| PCI DSS | Fail | Encrypt transactions | Not implemented |
| PCI DSS | Fail | Secure password management | Weak policies + no mgmt system |
| GDPR | Pass | 72‑hour breach notification | Plan exists |
| GDPR | Fail | EU customer data privacy | No encryption |
| GDPR | Fail | Data classification & inventory | Assets listed but unclassified |
| GDPR | Pass | Privacy policies enforced | Enforced among staff |
| SOC 1/2 | Fail | User access policies | No least privilege or separation of duties |
| SOC 1/2 | Fail | Data confidentiality | No encryption |
| SOC 1/2 | Pass | Data integrity | Measures in place |
| SOC 1/2 | Fail | Authorized access only | Unrestricted internal access |

<br><br>

## 6. Recommendations (Prioritized)

### High Priority (Immediate)
- Implement **Least Privilege** & **Separation of Duties**
- Deploy **encryption** for data at rest and in transit
- Create **Disaster Recovery Plan**

### Medium Priority
- Install **IDS** and **Password Management System**
- Enforce **strong password policies**
- Schedule **legacy system monitoring**

### Ongoing
- Maintain physical controls (locks, CCTV, fire safety)
- Classify assets and enforce GDPR/PCI/SOC access rules

> Addressing these gaps will reduce risk, protect sensitive data, and improve security posture.

<br><br>

## 7. Reflection

This audit reinforced a **holistic cybersecurity approach** (administrative + technical + physical). Key learnings:

- Asset identification, risk scoring, and gap analysis  
- Applying compliance frameworks (GDPR, PCI DSS, SOC)  
- Translating findings into actionable recommendations  

**Demonstrates:** Cybersecurity principles, analytical thinking, and business continuity planning.

<br><br>

## 8. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| PII | Personally Identifiable Information |
| SPII | Sensitive PII |
| DRP | Disaster Recovery Plan |
| IDS | Intrusion Detection System |
| NIST CSF | National Institute of Standards and Technology Cybersecurity Framework |

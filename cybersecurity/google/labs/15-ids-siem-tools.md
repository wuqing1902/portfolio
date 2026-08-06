# Lab 15: Network Traffic and Logs using IDS and SIEM Tools

**Focus Area:** Intrusion Detection | SIEM | Log Analysis | Threat Detection  
**Tools Used:** Suricata | Splunk | Wazuh | Google Chronicle | jq  
**Skills:** IDS Rule Writing | PCAP Analysis | SPL Queries | Log Correlation | Cloud SIEM | JSON Parsing  

<br><br>

## Objective

Monitor, analyze, and query network traffic and logs using IDS (Suricata) and SIEM tools (Splunk, Wazuh, and Google Chronicle). Understand how security analysts detect, investigate, and correlate security events using different log sources and detection systems.

<br><br>

## 1. Lab Activities Summary

| Activity | Tool | Focus | Key Skills |
|----------|------|-------|------------|
| 1 | Suricata (IDS) | Custom rules, PCAP analysis, alert generation | Rule writing, jq parsing |
| 2 | Splunk Cloud (SIEM) | Log upload, SPL queries, authentication monitoring | SPL, log filtering |
| 3 | Wazuh (SIEM) | SSH brute-force investigation | Field filtering, anomaly detection |
| 4 | Google Chronicle (Cloud SIEM) | Structured security searches | Cloud SIEM, query language |

<br><br>

## 2. Tools Overview

| Tool | Type | Purpose | Key Feature |
|------|------|---------|-------------|
| **Suricata** | IDS/IPS | Network traffic inspection | Rule-based detection, high performance |
| **Splunk** | SIEM | Centralized log analysis | SPL query language, dashboards |
| **Wazuh** | SIEM | Security monitoring | Open source, integrated with Elastic |
| **Chronicle** | Cloud SIEM | Enterprise threat detection | Google-scale, cloud-native |
| **jq** | CLI tool | JSON parsing | Lightweight, scriptable |

---

## 3. Activity 1: Explore Signatures and Logs with Suricata

**Objective:** Use Suricata as an IDS to create custom rules, analyze network traffic, and generate alerts from a packet capture file.

### Suricata Rule Structure
Action → Protocol → Source IP → Source Port → Destination IP → Destination Port → Options

#### Example:
alert icmp any any → any any (msg:"ICMP traffic detected")

| Field | Description | Example |
|-------|-------------|---------|
| Action | What to do | alert |
| Protocol | Network protocol | icmp |
| Source IP | Origin of traffic | any |
| Source Port | Source port | any |
| Destination IP | Target system | any |
| Destination Port | Target port | any |
| Options | Rule metadata / message | msg:"alert" |


### Security Insight
- Suricata is an IDS/IPS engine used for network threat detection
- Rules define what traffic should trigger alerts
- "any any → any any" is commonly used for broad detection testing


### Custom Rules Created

| Action | Protocol | Source | Destination | Message | SID |
|--------|----------|--------|-------------|---------|-----|
| alert | icmp | any any | any any | "ICMP Ping Detected" | 1000001 |
| alert | http | any any | any 80 | "HTTP GET Request Detected" | 1000002 |
| alert | tcp | any any | any 22 | "SSH Connection Attempt" | 1000003 |

### Rule Components Explained

| Component | Example | Purpose |
|-----------|---------|---------|
| **Action** | `alert` | What to do when rule matches (alert, drop, reject, pass) |
| **Protocol** | `icmp`, `http`, `tcp` | Which protocol to inspect |
| **Source** | `any any` | Source IP and port (any = wildcard) |
| **Direction** | `->` | Traffic direction (-> = to, <> = both ways) |
| **Destination** | `any any` | Destination IP and port |
| **Message** | `msg:"..."` | Alert text displayed |
| **SID** | `sid:1000001` | Unique rule identifier |
| **Revision** | `rev:1` | Rule version number |

### Lab Files Used

| File | Purpose |
|------|---------|
| `custom.rules` | Suricata detection rules |
| `sample.pcap` | Network traffic capture (Wireshark sample) |
| `fast.log` | Suricata alert log (quick summary) |
| `eve.json` | Structured Suricata event logs (JSON format) |

### Suricata Workflow

| Stage | Input/Output | Description | Example | 
|-------|--------------|-------------|---------|
| Rule Definition | custom.rules | Defines detection logic | (rules file) | 
| Traffic Input | sample.pcap | Packet capture for analysis | (traffic) | 
| Processing | Suricata Engine | Matches traffic against rules | Engine | 
| Alert Output | fast.log | Human-readable alerts | "ICMP Ping Detected" |
| Structured Logs | eve.json | Machine-readable event data (JSON) | {"timestamp":"...", "src_ip":"...", "alert":{...}} |


## Security Insight
- `fast.log` is used for quick alert visibility
- `eve.json` is used for SIEM integration (Splunk, ELK)
- Suricata acts as both IDS and IPS depending on configuration


### Sample eve.json Output
```json
{
  "timestamp": "2026-04-21T10:15:01",
  "src_ip": "192.168.1.10",
  "dest_ip": "8.8.8.8",
  "proto": "ICMP",
  "alert": {
    "signature": "ICMP Ping Detected"
  },
  "flow_id": 1111
}
```


### jq Parsing Commands
```bash
# Extract all alerts
jq '.alert' eve.json

# Extract specific fields
jq '{timestamp, src_ip, dest_ip, proto, alert_signature: .alert.signature}' eve.json

# Filter by protocol
jq 'select(.proto == "ICMP")' eve.json

# Count alerts by signature
jq -r '.alert.signature' eve.json | sort | uniq -c
```


### Skills Developed – Activity 1
| Skill | Application |
|-------|-------------|
| IDS rule creation | Wrote custom rules for ICMP, HTTP, SSH |
| Rule interpretation | Understood action, header, options structure |
| Network traffic analysis | Applied rules to sample.pcap |
| JSON log parsing | Used jq to extract fields from eve.json |
| Event correlation | Used flow_id to track related events |


### Security Relevance
Suricata helps detect malicious or suspicious traffic in real time by applying rule-based inspection on network packets. Benefits include:
- Real-time detection of known attack patterns
- Custom rule creation for organization-specific threats
- Structured logging (eve.json) for SIEM integration

### Reflection – Activity 1
This activity improved my understanding of how IDS tools inspect network traffic and generate alerts. I learned how to create rules, analyze structured logs, and use jq to extract specific fields for investigation.


## 4. Activity 2: Perform a Query with Splunk
Objective: Use Splunk Cloud to upload log data and perform searches using SPL (Search Processing Language).

### Sample Log Data
```
2026-04-21 10:20:05 user=root action=ssh_login status=failure src_ip=192.168.1.15
2026-04-21 10:20:10 user=guest action=login status=success src_ip=192.168.1.20
2026-04-21 10:20:15 user=admin action=ssh_login status=failure src_ip=203.0.113.50
2026-04-21 10:20:20 user=admin action=ssh_login status=failure src_ip=203.0.113.50
2026-04-21 10:20:25 user=admin action=ssh_login status=success src_ip=203.0.113.50
```

### SPL Query Examples
| Query | Purpose |
|-------|---------|
| `status=failure` | All failed authentication events |
| `status=failure AND user=root` | Failed logins for root user |
| `user=admin status=failure` | Failed logins for admin user |
| `src_ip=192.168.1.15` | Activity from specific IP |
| `action=ssh_login status=failure` | Failed SSH logins only |


### Splunk Workflow
## Splunk Log Analysis Workflow

| Stage | Action | Purpose |
|-------|--------|---------|
| Data Ingestion | Upload log file | Import raw event data |
| Query Execution | SPL search | Extract relevant events |
| Filtering | Refine results | Remove noise, focus on anomalies |
| Analysis | Identify suspicious activity | Detect threats or anomalies |


### Skills Developed – Activity 2
| Skill | Application |
|-------|-------------|
| SPL query construction | Built searches using field-value pairs |
| Log filtering | Isolated authentication failures |
| Dashboard navigation | Explored Splunk Cloud interface |


### Security Relevance
Splunk enables centralized log analysis to detect authentication failures and abnormal user behavior across enterprise systems.

### Reflection – Activity 2
This activity helped me understand how SIEM tools like Splunk can quickly filter large datasets to identify security-relevant events. The field-value pair syntax makes searching intuitive once you understand the log structure.



## 5. Activity 3: Perform a Query with Wazuh
Objective: Use Wazuh SIEM to investigate SSH brute-force attempts on a mail server.

### Sample Wazuh Logs
```
Apr 21 10:30:01 mailsv sshd: Failed password for root from 192.168.1.10
Apr 21 10:30:05 mailsv sshd: Failed password for root from 192.168.1.11
Apr 21 10:30:09 mailsv sshd: Failed password for root from 192.168.1.12
Apr 21 10:30:13 mailsv sshd: Failed password for root from 192.168.1.10
Apr 21 10:30:17 mailsv sshd: Failed password for root from 192.168.1.11
```

### Query Used
```
host.keyword: mailsv AND (fail* OR failed) AND root
```

#### Query Breakdown
| Component | Meaning | Purpose |
|-----------|---------|---------|
| `host.keyword: mailsv` | Filter by hostname | Focus on mail server |
| `fail*` | Wildcard match | Catches "fail", "failed", "failure" |
| `OR failed` | Alternative term | Ensures coverage |
| `AND root` | Combine conditions | Target root user specifically |


### Findings
| Finding | Value |
|---------|-------|
| Total failed root SSH login attempts | 376 |
| Multiple IP addresses involved | Yes (distributed brute-force) |
| Sensitive data identified | vendor_sales logs in mail server |
| Attack pattern | Credential brute-force |


### Wazuh Investigation Workflow

| Stage | Action | Result |
|-------|--------|--------|
| Detection | Identify suspicious host | mailsv flagged |
| Query Execution | host:mailsv AND fail* | Log filtering applied |
| Analysis | Review logs | Failed login patterns found |
| Count Events | Aggregate failures | 376 attempts detected |
| Source Analysis | Identify IPs | Multiple source IPs involved |


### Skills Developed – Activity 3
| Skill | Application |
|-------|-------------|
| SIEM threat investigation | Identified brute-force pattern |
| Field-based filtering | Used `host.keyword` for precise filtering |
| Log correlation | Linked multiple failed attempts |
| Anomaly detection | Recognized 376 failures as abnormal |


### Security Relevance
Wazuh helps detect brute-force attacks and unauthorized access attempts in real time. The open-source nature allows customization for specific organizational needs.


### Reflection – Activity 3
This activity demonstrated how SIEM systems help security analysts investigate attack patterns such as brute-force login attempts. The ability to count and correlate failed attempts across multiple source IPs is essential for identifying distributed attacks.



## 6. Activity 4: Perform a Query with Chronicle
Objective: Use Google Chronicle as a cloud-based SIEM platform to perform structured security searches on ingested logs.

### Chronicle Query Language
| Query Type | Syntax | Purpose |
|------------|--------|---------|
| Event type filter | `metadata.event_type = "NETWORK_CONNECTION"` | Focus on network events |
| Port filter | `target.port = 22` | SSH traffic only |
| Action filter | `security_result.action = "FAIL"` | Failed actions only |
| Combined | `target.port = 22 AND security_result.action = "FAIL"` | Failed SSH attempts |

### Example Queries
```
-- All network connections
metadata.event_type = "NETWORK_CONNECTION"

-- SSH connection attempts
target.port = 22

-- Failed SSH attempts
target.port = 22 AND security_result.action = "FAIL"

-- Failed attempts from specific IP
target.port = 22 AND security_result.action = "FAIL" AND principal.ip = "192.168.1.10"
```


### Chronicle vs Traditional SIEM
| Feature | Chronicle (Cloud) | Traditional SIEM |
|---------|-------------------|------------------|
| Scalability | Google-scale (unlimited) | Hardware-limited |
| Query speed | Sub-second on petabytes | Minutes to hours |
| Maintenance | Zero (cloud-managed) | Significant |
| Cost model | Consumption-based | Hardware + licensing |
| Retention | Extended (years) | Limited (months) |


### Skills Developed – Activity 4
| Skill | Application |
|-------|-------------|
| Cloud SIEM navigation | Explored Chronicle interface |
| Structured query language | Used field-based queries |
| Security event investigation | Correlated network events |


### Security Relevance
Chronicle provides scalable cloud-based log analysis for enterprise-level threat detection, enabling rapid investigation across massive datasets.

### Reflection – Activity 4
This activity introduced cloud-based security monitoring and showed how large-scale log analysis is performed in modern SOC environments. The structured query language is intuitive once you understand the data schema.




## 7. IDS vs SIEM – Comparison
| Feature | IDS (Suricata) | SIEM (Splunk/Wazuh/Chronicle) |
|---------|----------------|-------------------------------|
| Data source | Network traffic | Logs (multiple sources) |
| Scope | Network layer | Enterprise-wide |
| Detection | Rule-based signatures | Correlation, analytics |
| Alert type | Packet-level | Event-level |
| Primary use | Real-time threat detection | Investigation, compliance |
| Typical deployment | Network perimeter | Centralized logging |


### How They Work Together

| Step | Tool | Type | Function | Output | Workflow Role |
|------|------|------|----------|--------|---------------|
| 1 | Suricata | IDS | Detects network threats/intrusions | eve.json alerts | Initial detection of suspicious activity |
| 2 | Splunk | SIEM | Log aggregation & correlation | Search results, dashboards | Correlates events across data sources |
| 3 | Chronicle | Cloud SIEM | Large-scale threat analysis | Cloud analytics | Deep analysis and threat investigation |
| 4 | SOC Analyst | Human | Investigates and responds | Incident reports, actions taken  | Final review, response, and decision-making |


## 8. SOC Analyst Workflow – Complete Picture

| Stage | Process | Output / Action |
|-------|---------|-----------------|
| Detection | Suricata IDS | ICMP scan detected |
| Alerting | eve.json logs | Structured alert generated |
| Ingestion | SIEM (Splunk/Wazuh) | Centralized log storage |
| Investigation| Query & analysis | Identify related activity (Same source IP?, Other failed attempts?, Timeline of activity?) |
| Correlation | Cross-log analysis | Multi-stage attack linked (Link IDS alerts with authentication logs, ICMP scan followed by SSH brute-force)|
| Response | SOC containment | IP blocked, host isolated |



## 9. Multi-SIEM Comparison
| Feature | Splunk | Wazuh | Chronicle |
|---------|--------|-------|-----------|
| Deployment | Cloud or on-prem | On-prem (open source) | Cloud-only |
| Query language | SPL | Lucene/KQL | YARA-L (custom) |
| Learning curve | Moderate | Moderate | Low (structured) |
| Cost | Commercial ($$$) | Free (open source) | Consumption-based |
| Best for | Enterprise SOC | Budget-conscious teams | Google ecosystem |
| Integration | Extensive | Elastic stack | Google Cloud |


### When to Use Each
| Scenario | Recommended Tool |
|----------|------------------|
| Deep packet inspection | Suricata (IDS) |
| Enterprise log aggregation | Splunk |
| Budget-conscious SOC | Wazuh |
| Google Cloud environment | Chronicle |
| Automated parsing | jq |


## 10. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| IDS rule writing | Created custom Suricata rules for ICMP, HTTP, SSH |
| PCAP analysis | Applied rules to sample.pcap traffic capture |
| JSON parsing | Used jq to extract fields from eve.json |
| SPL queries | Searched Splunk for authentication failures |
| SIEM investigation | Used Wazuh to identify SSH brute-force (376 attempts) |
| Cloud SIEM | Queried Chronicle for network connections |
| Log correlation | Linked events across multiple tools |
| Tool comparison | Evaluated IDS vs SIEM, Splunk vs Wazuh vs Chronicle |


## 11. Tool-Specific Query Reference
### Suricata (jq)
```bash
# Extract all alerts
jq '.alert' eve.json

# Filter by protocol
jq 'select(.proto == "ICMP")' eve.json

# Show timestamp and signature only
jq '{time: .timestamp, alert: .alert.signature}' eve.json
```

### Splunk (SPL)
```spl
# Basic search
status=failure

# Field-specific
user=root status=failure

# Time-based
earliest=-24h status=failure

# Statistical
status=failure | stats count by user
```


### Wazuh (KQL)
```kql
host.keyword: mailsv AND (fail* OR failed) AND root
Chronicle (YARA-L)
yara
metadata.event_type = "NETWORK_CONNECTION"
target.port = 22
security_result.action = "FAIL"
```


## 12. Overall Reflection
This lab provided hands-on experience with IDS and SIEM tools used in real-world cybersecurity operations.

Key takeaways by activity:

| Activity | Key Insight |
|----------|--------------|
| Suricata | IDS provides packet-level visibility; custom rules enable organization-specific detection |
| Splunk | SPL makes log analysis efficient; field-value pairs are intuitive |
| Wazuh | Open-source SIEM is powerful; 376 failed attempts clearly indicates brute-force |
| Chronicle | Cloud SIEM scales infinitely; structured queries enable rapid investigation |


### Complete workflow understanding:
- Suricata provides low-level network visibility (packets)
- SIEM tools enable high-level event correlation (logs)
- Together, they form the core of SOC monitoring

Demonstrates: Practical proficiency with industry-standard IDS and SIEM tools, essential for SOC analyst roles.

## 13. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| IDS | Intrusion Detection System – monitors network traffic for threats |
| IPS | Intrusion Prevention System – IDS that can block traffic |
| SIEM | Security Information and Event Management – centralized logging |
| SPL | Search Processing Language – Splunk's query language |
| PCAP | Packet Capture – recorded network traffic |
| eve.json | Suricata's structured JSON log format |
| jq | Command-line JSON processor |
| SID | Signature ID – unique rule identifier |
| Brute-force | Repeated login attempts to guess credentials |
| Flow ID | Unique identifier for a network flow (connection) |


## 14. Quick Reference – Tool Commands
### Suricata
```bash
# Run Suricata on PCAP
suricata -r sample.pcap -S custom.rules

# Read fast.log
cat fast.log

# Parse eve.json with jq
jq '.' eve.json
```


### Splunk
```spl
# Search syntax
field=value
field=value AND field2=value2
```


### Wazuh
```kql
field.keyword: value AND (term1 OR term2)
```


### Chronicle
```yara
metadata.event_type = "TYPE"
field = "value"
field = "value" AND other_field = "value"
```


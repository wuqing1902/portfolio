# Lab 3: Network Attack Analysis (Wireshark – SYN Flood)

**Tools Used:** Wireshark  
**Attack Type Analyzed:** SYN Flood (Denial of Service)  
**Skills:** Packet Analysis | Attack Pattern Recognition | TCP Handshake | Incident Response | Mitigation Strategies  

<br><br>

## Objective

Analyze a cybersecurity incident involving a travel agency's website that experienced connection timeouts. Using Wireshark logs, identify the type of network attack, examine its impact, and explain how it disrupted the web server's functionality.

<br><br>

## 1. Scenario Overview

A travel agency's website experienced connection timeouts, preventing employees and customers from accessing its sales pages. Automated alerts indicated a problem with the web server. A packet sniffer captured network traffic revealing a large number of TCP SYN requests from an unfamiliar IP address, overwhelming the web server.

<br><br>

## 2. Wireshark Log Analysis (TCP/HTTP)

| No. | Time | Source | Destination | Protocol | Info | Status |
|-----|------|--------|-------------|----------|------|--------|
| 47 | 3.144521 | 198.51.100.23 | 192.0.2.1 | TCP | 42584->443 [SYN] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 48 | 3.195755 | 192.0.2.1 | 198.51.100.23 | TCP | 443->42584 [SYN, ACK] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 49 | 3.246989 | 198.51.100.23 | 192.0.2.1 | TCP | 42584->443 [ACK] Seq=1 Win=5792 Len=120 | 🟢 Normal |
| 50 | 3.298223 | 198.51.100.23 | 192.0.2.1 | HTTP | GET /sales.html HTTP/1.1 | 🟢 Normal |
| 51 | 3.349457 | 192.0.2.1 | 198.51.100.23 | HTTP | HTTP/1.1 200 OK (text/html) | 🟢 Normal |
| 52 | 3.390692 | 203.0.113.0 | 192.0.2.1 | TCP | 54770->443 [SYN] Seq=0 Win=5792 Len=0 | 🔴 Attack |
| 53 | 3.441926 | 192.0.2.1 | 203.0.113.0 | TCP | 443->54770 [SYN, ACK] Seq=0 Win=5792 Len=120 | 🔴 Attack |
| 54 | 3.493160 | 203.0.113.0 | 192.0.2.1 | TCP | 54770->443 [ACK] Seq=1 Win=5792 Len=0 | 🔴 Attack |
| 55 | 3.544394 | 198.51.100.14 | 192.0.2.1 | TCP | 14785->443 [SYN] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 56 | 3.599628 | 192.0.2.1 | 198.51.100.14 | TCP | 443->14785 [SYN, ACK] Seq=0 Win=5792 Len=120 | 🟢 Normal |
| 77 | 7.330577 | 192.0.2.1 | 198.51.100.5 | HTTP | HTTP/1.1 504 Gateway Time-out (text/html) | 🟡 Timeout/Error |

**Status Legend:** 🟢 Normal | 🔴 Attack Traffic | 🟡 Error/Timeout

<br><br>

## 3. Normal vs. Attack Traffic Analysis

### Normal TCP/HTTP Communication

A normal connection between a legitimate user and the web server follows the **TCP three-way handshake**:

| Step | Direction | Packet Type | Purpose |
|------|-----------|-------------|---------|
| 1 | Client → Server | SYN | Requests connection |
| 2 | Server → Client | SYN-ACK | Acknowledges and reserves resources |
| 3 | Client → Server | ACK | Confirms connection established |

After handshake completion, HTTP traffic flows normally:
- **GET request** from client for specific webpage
- **200 OK response** from server with requested content

### Indicators of the Attack

The Wireshark log reveals several abnormal patterns:

| Indicator | Evidence from Logs |
|-----------|---------------------|
| Repeated SYN packets | Multiple SYN entries from attacker IP `203.0.113.0` |
| Single attacking source | Only one unfamiliar IP address generating SYN traffic |
| Resource exhaustion | Legitimate traffic (e.g., `198.51.100.14`) initially processed but later fails |
| Timeout errors | HTTP `504 Gateway Time-out` appears after attack intensifies |

<br><br>

## 4. Attack Identification

### Attack Type: **SYN Flood (Denial of Service - DoS)**

**Classification:** Layer 4 (Transport Layer) Denial of Service Attack

### Evidence Supporting Identification:

| Evidence | Explanation |
|----------|-------------|
| Single attacking IP | `203.0.113.0` sending repeated SYN packets |
| Incomplete handshakes | Attacker never completes the three-way handshake properly |
| Resource exhaustion | Server becomes unable to respond to legitimate SYN requests |
| Timeout errors | Employees receive `504 Gateway Time-out` instead of web content |

<br><br>

## 5. Attack Mechanism Explained

### How SYN Flood Works:

| Step | Action |
|------|--------|
| Step 1: | Attacker sends massive volume of SYN packets (spoofed or real) |
| Step 2: | Server responds with SYN-ACK and reserves resources for each connection |
| Step 3: | Attacker never sends final ACK, leaving connections "half-open" |
| Step 4: | Server's connection queue fills up |
| Step 5: | Legitimate SYN requests are dropped or timeout |

### Impact on the Travel Agency Website:

| Impact | Description |
|--------|-------------|
| Service unavailability | Employees cannot access sales webpage |
| Connection timeouts | Browsers display timeout errors |
| Resource exhaustion | Web server CPU/memory consumed by half-open connections |
| Business disruption | No online vacation package sales during attack |

<br><br>

## 6. Incident Timeline

| Time | Event |
|------|-------|
| Afternoon | Automated alerts trigger |
| T+0 min | Employees report connection timeouts |
| T+5 min | Packet capture initiated |
| T+10 min | SYN flood pattern identified |
| T+15 min | Attack confirmed as DoS (SYN Flood) |
| Post-incident | Mitigation strategies recommended |

<br><br>

## 7. Consequences of the Attack

| Category | Consequence |
|----------|-------------|
| **Business** | Disrupted operations – website inaccessible |
| **Customer** | Negative user experience – cannot book vacations |
| **Financial** | Potential revenue loss during downtime |
| **Reputational** | Customers may lose trust in travel agency |
| **Technical** | Web server resources exhausted |

<br><br>

## 8. Mitigation Strategies

### Immediate Response (During Attack)

| Action | Purpose |
|--------|---------|
| Block attacking IP (`203.0.113.0`) at firewall | Stop malicious traffic source |
| Enable SYN cookies | Handle TCP handshake without exhausting resources |
| Increase backlog queue size | Allow more pending connections |

### Long-term Prevention

| Strategy | Implementation |
|----------|----------------|
| **Rate limiting** | Limit SYN packets per second from single IP |
| **Firewall rules** | Detect and block anomalous SYN patterns |
| **SYN cookies** | Permanently enable on web servers |
| **DDoS protection** | Deploy cloud-based DDoS mitigation service |
| **Monitoring** | Set alerts for sudden SYN traffic spikes |

<br><br>

## 9. Comparison: Normal vs. Attack Traffic

| Characteristic | Normal Traffic | SYN Flood Attack |
|----------------|----------------|------------------|
| SYN packet frequency | Low, sporadic | High, continuous |
| Source IP diversity | Many legitimate users | Single or few IPs |
| Handshake completion | 100% complete | Incomplete (no final ACK) |
| Server response | 200 OK | 504 Timeout |
| Connection queue | Manageable | Exhausted |

<br><br>

## 10. Skills Demonstrated

- Network traffic analysis using Wireshark
- TCP handshake and protocol behavior understanding
- Attack pattern recognition (SYN flood)
- Incident investigation and root cause analysis
- Mitigation strategy development
- Technical documentation for security incidents

<br><br>

## 11. Reflection

This lab provided hands-on experience analyzing a real-world DoS attack scenario. Key takeaways:

- How SYN flood attacks exploit the TCP three-way handshake
- Recognizing attack patterns in packet capture logs
- The cascading impact of resource exhaustion on legitimate users
- Practical mitigation techniques (SYN cookies, rate limiting, IP blocking)

**Demonstrates:** Network security analysis, attack identification, and defensive strategy formulation.

<br><br>

## 12. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| SYN | Synchronize packet – initiates TCP connection |
| SYN-ACK | Synchronize-Acknowledge packet – server response |
| ACK | Acknowledge packet – completes handshake |
| SYN Flood | DoS attack exhausting server connection queue |
| Half-open connection | Connection awaiting final ACK |
| 504 Gateway Time-out | Server upstream timeout error |
| SYN cookies | Technique to handle SYN flood without resource exhaustion |
| DoS | Denial of Service – attack disrupting availability |


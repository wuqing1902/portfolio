# Lab 14: Network Monitoring and Analysis

**Focus Area:** Network Traffic Analysis | Packet Capture | Protocol Analysis  
**Tools Used:** Wireshark | tcpdump 
**Skills:** Packet Inspection | Filter Application | Live Traffic Capture | Protocol Layering | Tool Comparison  

<br><br>

## Objective

Analyze and monitor network traffic using industry-standard tools (Wireshark and tcpdump). This lab demonstrates packet analysis, packet capture, and tool comparison through three main activities.

<br><br>

## 1. Lab Activities Summary

| Activity | Focus | Tool | Key Skills |
|----------|-------|------|------------|
| 1 | Analyze existing packet capture | Wireshark | Packet inspection, filtering, protocol identification |
| 2 | Capture live network traffic | tcpdump | Live capture, interface selection, file saving |
| 3 | Compare network analyzers | Research | Tool evaluation, use case identification |

<br><br>

## 2. Activity 1: Analyze Your First Packet (Wireshark)

**Objective:** Use Wireshark to open and analyze a packet capture (.pcap) file, understanding packet structure, protocol layers, and applying filters.

### Packet Structure – OSI Model Layers
## Packet Analysis – Wireshark (Security View)

| Layer | Example Data | Description | What to Look For in Wireshark | Security Insight |
|-------|--------------|-------------|-------------------------------|------------------|
| Application | HTTP, DNS, HTTPS request | User-level data | URLs, headers, payload | Detect phishing, data leaks |
| Transport | TCP/UDP segments | Ports, sequencing, reliability | Ports, flags (SYN, ACK) | Identify scanning or floods |
| Network | IP packets (IPv4, IPv6) | Source/destination IP addressing | Source/destination IP | Trace attacker origin |
| Data Link | Ethernet frames | MAC addresses and frames | MAC addresses| Detect ARP spoofing |
| Physical | Bits | Raw bits transmitted over medium | Raw capture data | Low-level transmission layer |



### Wireshark Filters Used

| Filter | Purpose | Example Use Case |
|--------|---------|------------------|
| `ip.addr == 142.250.1.139` | Traffic to/from specific IP | Investigate suspicious IP |
| `ip.src == 142.250.1.139` | Traffic from specific IP | Identify source of traffic |
| `ip.dst == 142.250.1.139` | Traffic to specific IP | Track destination |
| `eth.addr == 42:01:ac:15:e0:02` | Traffic by MAC address | Physical device tracking |
| `udp.port == 53` | DNS traffic | Domain resolution analysis |
| `tcp.port == 80` | HTTP traffic | Web traffic analysis |
| `tcp contains "curl"` | TCP payload contains text | Application signature detection |

### Sample Packet Evidence

#### 1. DNS Query (Domain Resolution)

| Field | Value |
|-------|-------|
| **Source IP** | 172.21.224.2 |
| **Destination IP** | DNS Server |
| **Protocol** | UDP |
| **Destination Port** | 53 |
| **Query** | opensource.google.com |

**Purpose:** System resolving domain name to IP address

#### 2. TCP Communication (Web Traffic)

| Field | Value |
|-------|-------|
| **Source IP** | 172.21.224.2 |
| **Destination IP** | 142.250.1.139 |
| **Protocol** | TCP |
| **Destination Port** | 80 (HTTP) |

**Purpose:** Web communication between local system and external server

#### 3. ICMP Packet (Connectivity Check)

| Field | Value |
|-------|-------|
| **Source IP** | 172.21.224.2 |
| **Destination IP** | 142.250.1.139 |
| **Protocol** | ICMP |
| **Type** | Echo Request/Reply |

**Purpose:** Basic network connectivity testing

### Packet Layer Analysis (TCP Packet Example)

| Layer | Information Captured |
|-------|---------------------|
| **Frame** | Overall packet size, capture timestamp |
| **Ethernet II** | Source MAC, Destination MAC |
| **IPv4** | Source IP (172.21.224.2), Destination IP (142.250.1.139) |
| **TCP** | Source Port (49652), Destination Port (80), Flags (SYN, ACK, etc.) |

### Traffic Interpretation

| Observation | Interpretation |
|-------------|----------------|
| DNS queries to opensource.google.com | Normal domain resolution |
| TCP connections over port 80 | HTTP web traffic |
| ICMP echo requests/replies | Connectivity checks (ping) |
| No malicious indicators | Normal web browsing behavior |

### Security Relevance

| Skill | Application |
|-------|-------------|
| Detect abnormal traffic patterns | Identify C2 communication, data exfiltration |
| Identify potential intrusions | Detect scanning, exploitation attempts |
| Investigate incidents | Forensic analysis of captured traffic |

<br><br>

## 3. Activity 2: Capture Your First Packet (tcpdump)

**Objective:** Capture live network traffic using tcpdump in a Linux environment, save captures, and analyze results.

### Network Interface Identification

```bash
# List available interfaces
ifconfig

# List interfaces suitable for capture
sudo tcpdump -D
Selected interface: eth0 (primary Ethernet interface)
```

### tcpdump Command Reference
| Command | Purpose |
|---------|---------|
| `sudo tcpdump -i eth0 -v -c5` | Capture 5 packets from eth0 with verbose output |
| `sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &` | Capture 9 HTTP packets, save to file, run in background |
| `sudo tcpdump -nn -r capture.pcap -v` | Read saved capture with verbose output |
| `sudo tcpdump -nn -r capture.pcap -X` | Read saved capture with hex and ASCII output |

### tcpdump Options Explained
| Option | Meaning | Security Relevance |
|--------|---------|-------------------|
| `-i eth0` | Capture on interface eth0 | Target specific network segment |
| `-v` | Verbose output | More packet details |
| `-c5` | Capture 5 packets then exit | Limit capture size |
| `-nn` | No name resolution | Prevents DNS leaks during capture |
| `port 80` | Filter HTTP traffic | Focus on web traffic |
| `-w capture.pcap` | Write to file | Save for later analysis |
| `-r capture.pcap` | Read from file | Analyze saved capture |
| `-X` | Hex and ASCII output | Deep packet inspection |
| `&` | Run in background | Simultaneous traffic generation |


### Capture Process
| Step | Action | Command |
|------|--------|---------|
| 1 | Start tcpdump in background | sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap & | 
| 2 | Generate traffic while tcpdump runs | curl opensource.google.com | 
| 3 | tcpdump captures 9 packets and exits | - |
| 4 | Verify capture file | ls -l capture.pcap | 
| 5 | Analyze captured packets | sudo tcpdump -nn -r capture.pcap -v, sudo tcpdump -nn -r capture.pcap -X|
        

### Key Findings
| Finding | Implication |
|---------|-------------|
| Successfully captured HTTP traffic (port 80) | Web traffic monitoring possible |
| Observed TCP handshake (SYN, SYN-ACK, ACK) | Connection establishment visible |
| Identified packet metadata (TTL, flags, sequence numbers) | Deep packet inspection possible |
| `-nn` option prevented name resolution | Secure capture (no DNS leaks) |


### TCP Handshake Observed


| Step | Stage | Client Action | Server Response | Description | Security Relevance |
|------|-------|---------------|-----------------|-------------|--------------------|
| 1 | SYN | SYN (Seq = x) | — | Connection request | Can be used in SYN flood attacks |
| 2 | SYN-ACK | — | SYN-ACK (Seq = y, Ack = x+1) | Acknowledge request | Confirms open port |
| 3 | ACK | ACK (Ack = y+1) | — | Connection established | Session begins |
| 4 | HTTP GET | HTTP GET request | — | Client requests resource | May expose sensitive endpoints |
| 5 | HTTP 200 OK | — | HTTP 200 OK | Server returns requested data    | Data returned to client |


**Key Insight:**
- TCP handshake establishes reliable communication before data transfer.
- Attackers may abuse SYN packets for DoS attacks (SYN flood).



## 4. Activity 3: Research Network Protocol Analyzers
Objective: Compare Wireshark and tcpdump to understand differences, similarities, and appropriate use cases.

### Comparison Matrix
| Feature | Wireshark | tcpdump |
|---------|-----------|---------|
| Interface | Graphical (GUI) | Command-line (CLI) |
| Ease of learning | Easier for beginners | Steeper learning curve |
| Filtering | Advanced (visual filter builder) | Basic (command-line expressions) |
| Visualization | Color-coded, graphs, streams | Text-only output |
| Resource usage | High (memory, CPU) | Low (lightweight) |
| Remote capture | Limited (requires GUI access) | Excellent (SSH + tcpdump) |
| Scriptable | Limited | Fully scriptable |
| Output formats | Multiple (pcap, JSON, CSV, etc.) | pcap primarily |
| Real-time analysis | Yes (with GUI) | Yes (text-based) |
| Cost | Free (open source) | Free (open source) |

### Similarities
| Similarity | Description |
|------------|-------------|
| Packet capture | Both capture live network traffic |
| Filtering capability | Both support BPF (Berkeley Packet Filter) syntax |
| Protocol analysis | Both analyze common protocols (TCP, UDP, HTTP, DNS) |
| Open source | Both are free and community-supported |
| pcap support | Both read/write .pcap files |

### Limitations
| Tool | Limitation |
|------|-------------|
| Wireshark | Requires GUI (X11 forwarding or local desktop); higher resource usage |
| tcpdump | CLI-only; requires proficiency with command-line filters; no visual output |

### Use Cases
| Scenario | Recommended Tool | Justification |
|----------|-----------------|---------------|
| Deep protocol analysis | Wireshark | Visual packet dissection, follow TCP streams |
| Quick capture on server | tcpdump | Lightweight, no GUI needed |
| Automated capture script | tcpdump | Scriptable, can run in cron jobs |
| Training/learning | Wireshark | Visual feedback helps understanding |
| Remote forensic capture | tcpdump | SSH + tcpdump, transfer pcap for analysis |
| Large capture analysis | Wireshark | Better navigation, filtering, search |
| Low-bandwidth environment | tcpdump | Minimal overhead |


### Workflow Integration - SOC Pipeline

Remote Server (tcpdump capture)
- Secure transfer (SCP / SFTP)
- Analyst Workstation (Wireshark analysis)

**Principle:** Capture on server, analyze locally


| Stage              | Tool        | Purpose                          |
|--------------------|------------|----------------------------------|
| Packet Capture     | tcpdump     | Collect network traffic          |
| Secure Transfer    | SCP / SFTP  | Move data safely                 |
| Traffic Analysis   | Wireshark   | Inspect packets visually         |
| Investigation      | Analyst     | Identify anomalies or threats    |


## Security Insight
- Capturing on the server reduces risk of data loss
- Local analysis prevents performance impact on production systems
- This workflow is commonly used in SOC Level 1–2 investigations



## 5. Filter Pattern Library
### Common Wireshark/tcpdump Filters
| Filter | Protocol/Field | Use Case |
|--------|---------------|----------|
| `tcp.port == 80` | HTTP | Web traffic analysis |
| `udp.port == 53` | DNS | Domain resolution investigation |
| `icmp` | ICMP | Ping flood detection |
| `tcp.flags.syn == 1` | SYN packets | Port scanning detection |
| `tcp.analysis.flags` | TCP analysis | Retransmissions, out-of-order |
| `http.request` | HTTP requests | Web browsing analysis |
| `dns.qry.name contains "google"` | DNS queries | Domain pattern matching |
| `ip.addr == 192.168.1.1` | IP address | Single host traffic |
| `tcp contains "password"` | Payload | Credential detection |
| `frame.len > 1500` | Frame size | Jumbo frame detection |


### tcpdump BPF Filters
| Filter | Meaning |
|--------|---------|
| `host 192.168.1.1` | Traffic to/from IP |
| `src host 192.168.1.1` | Traffic from IP |
| `dst host 192.168.1.1` | Traffic to IP |
| `port 80` | Traffic on port 80 |
| `tcp port 80` | TCP port 80 only |
| `udp port 53` | UDP port 53 only |
| `net 192.168.1.0/24` | Entire subnet |
| `tcp[tcpflags] & tcp-syn != 0` | SYN packets only |


## 6. Wireshark vs tcpdump – Quick Decision Guide
- Need GUI? → Wireshark  
- Remote server? → tcpdump  
- Learning/network visualization? → Wireshark  
- General use? → Either tool works


## 7. Skills Demonstrated
| Skill | Application in Lab |
|-------|-------------------|
| Packet inspection | Analyzed DNS, TCP, ICMP packets in Wireshark |
| Protocol layering understanding | Identified Frame, Ethernet, IP, TCP layers |
| Filter application | Used IP, port, protocol, and payload filters |
| Live traffic capture | Used tcpdump to capture HTTP traffic |
| Interface management | Identified and selected eth0 for capture |
| Capture file management | Saved, verified, and analyzed .pcap files |
| Tool evaluation | Compared Wireshark vs tcpdump features |
| Security best practices | Used `-nn` to disable name resolution |


## 8. Tools and Concepts Used
| Tool/Concept | Application |
|--------------|-------------|
| Wireshark | Graphical packet analysis |
| tcpdump | Command-line packet capture |
| BPF filters | Berkeley Packet Filter syntax |
| .pcap format | Standard packet capture format |
| TCP handshake | Observed SYN, SYN-ACK, ACK sequence |
| Protocol layering | Analyzed encapsulation |
| HTTP (port 80) | Captured web traffic |
| DNS (port 53) | Observed domain resolution |
| ICMP | Observed connectivity checks |


## 9. Reflection
This lab significantly improved my understanding of how network traffic operates and how security analysts investigate it.

### Activity 1 takeaways:
- Packet analysis was initially overwhelming due to protocol complexity
- Wireshark filters make traffic analysis manageable
- Protocol layering (Ethernet → IP → TCP/UDP → Application) is consistent across packets

### Activity 2 takeaways:
- tcpdump is lightweight and ideal for remote/server captures
- The -nn option is critical for secure captures (prevents DNS leaks)
- Saving captures to .pcap enables later analysis in Wireshark

### Activity 3 takeaways:
- Wireshark and tcpdump complement each other
- Master both: tcpdump for capture, Wireshark for analysis
- Use case determines the right tool

Demonstrates: Network traffic analysis proficiency, tool familiarity, and investigative methodology.

## 10. Appendix: Key Terminology
| Term | Meaning |
|------|---------|
| Packet capture | Recording network traffic for analysis |
| .pcap | Standard file format for captured packets |
| BPF | Berkeley Packet Filter – syntax for filtering packets |
| Encapsulation | Wrapping data with protocol headers at each layer |
| TCP handshake | SYN, SYN-ACK, ACK – connection establishment |
| TTL | Time To Live – hop limit for packets |
| Sequence number | TCP field for packet ordering |
| Name resolution | Converting IP addresses to hostnames (can leak in captures) |

## 11. Command Quick Reference
### tcpdump Common Commands
```bash
# List interfaces
sudo tcpdump -D

# Capture 10 packets on eth0
sudo tcpdump -i eth0 -c10

# Capture HTTP traffic to file (no name resolution)
sudo tcpdump -i eth0 -nn port 80 -w capture.pcap

# Read capture file with verbose output
sudo tcpdump -nn -r capture.pcap -v

# Read capture with hex and ASCII
sudo tcpdump -nn -r capture.pcap -X

# Capture all traffic from specific IP
sudo tcpdump -i eth0 src host 192.168.1.1

# Capture traffic to specific port
sudo tcpdump -i eth0 dst port 443
Wireshark Display Filters
ip.addr == 192.168.1.1          # Traffic to/from IP
tcp.port == 443                 # HTTPS traffic
http.request                    # HTTP GET/POST requests
dns.qry.name contains "example" # DNS queries for domain
tcp.flags.syn == 1              # SYN packets only
frame.len > 1500                # Large frames
tcp.analysis.retransmission     # Retransmitted packets
```

## 12. Security Best Practices for Packet Capture
| Practice | Why It Matters |
|----------|----------------|
| Use `-nn` in tcpdump | Prevents DNS lookups that could leak information |
| Capture to file, analyze later | Minimizes time spent capturing live |
| Use filters to limit capture | Reduces storage and focuses on relevant traffic |
| Secure .pcap files | May contain sensitive data (passwords, PII) |
| Run with least privilege | Use sudo only when necessary |
| Document capture context | Timestamps, interfaces, filters used |


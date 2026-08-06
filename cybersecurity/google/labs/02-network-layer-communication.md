# Lab 2: Analyze Network Layer Communication 

**Tools Used:** tcpdump  
**Protocols Analyzed:** DNS, ICMP  
**Skills:** Packet Analysis | Protocol Identification | Root Cause Analysis | Incident Investigation  

<br><br>

## Objective

Analyze network traffic using `tcpdump` to identify why users receive a **“destination port unreachable”** error when accessing a website, and determine the root cause of the DNS communication failure.

<br><br>

## 1. Scenario Overview

Users reported inability to access **yummyrecipesforme.com**, receiving the error message **“destination port unreachable.”**

As a cybersecurity analyst, I used `tcpdump` to capture and analyze network traffic while attempting to access the website, focusing on DNS and ICMP communication patterns.

<br><br>

## 2. Captured Traffic Summary

> **Note:** The following is a summarized representation of the captured `tcpdump` logs:

| Timestamp | Source | Destination | Protocol | Message Type |
|-----------|--------|-------------|----------|--------------|
| 13:24:32.192571 | 192.51.100.15:35084 | 203.0.113.2:53 | DNS (UDP) | A? yummyrecipesforme.com |
| 13:24:32.193400 | 203.0.113.2 | 192.51.100.15 | ICMP | UDP port 53 unreachable |
| 13:24:32.194100 | 192.51.100.15:35084 | 203.0.113.2:53 | DNS (UDP) | A? yummyrecipesforme.com (retry) |
| 13:24:32.194130 | 203.0.113.2 | 192.51.100.15 | ICMP | UDP port 53 unreachable |

**Pattern observed:** Each DNS query received an ICMP error instead of a valid DNS response.

<br><br>

## 3. Traffic Analysis Findings

### a. Protocols Identified

| Protocol | Role in Incident |
|----------|------------------|
| **UDP (DNS)** | Used by client to send domain resolution requests on port 53 |
| **ICMP** | Used by server to return error messages when DNS service is unavailable |

### b. Log Analysis Summary
- Client (**192.51.100.15**) sent DNS A‑record queries to DNS server (**203.0.113.2**) on **UDP port 53**
- Each request asked for the IP address of `yummyrecipesforme.com`
- Instead of a DNS reply, the server returned **ICMP “udp port 53 unreachable”** errors
- Multiple retries produced identical failures → issue is **persistent**

### c. Key Observations
- **Port 53** is the standard DNS port
- The DNS server is **responding with ICMP errors** instead of DNS replies
- This indicates the DNS service is **not reachable or not functioning properly**

<br><br>

## 4. Incident Timeline

| Event | Time |
|-------|------|
| Users report website access failure | ~13:20 |
| Traffic capture started | 13:24 |
| First DNS query + ICMP error observed | 13:24:32.192 |
| Repeated failures confirmed | 13:24:32.194 |
| Root cause identified | Post‑analysis |

<br><br>

## 5. Investigation Process

1. Reproduced the error by attempting to access the website
2. Captured live network traffic using `tcpdump`
3. Isolated DNS requests (UDP port 53)
4. Identified ICMP error responses
5. Verified repeated failure pattern
6. Concluded DNS service unavailability

<br><br>

## 6. Root Cause Analysis

### Most Likely Causes:
- **DNS server is down or not running** – Service failure on `203.0.113.2`
- **Firewall blocking port 53** – Network security rule misconfiguration
- **DNS service misconfiguration** – Incorrect listening port or binding

### Less Likely but Possible:
- **Denial of Service (DoS) attack** overwhelming the DNS server

<br><br>

## 7. Conclusion

The issue is caused by a **failure in DNS communication**. The client cannot retrieve the IP address of `yummyrecipesforme.com` because **UDP port 53 on the DNS server is unreachable**. This prevents domain resolution, resulting in users being unable to access the website.

<br><br>

## 8. Recommended Next Steps

| Priority | Action |
|----------|--------|
| Immediate | Verify DNS server service status on `203.0.113.2` |
| Immediate | Check firewall rules for port 53 blocking |
| Short‑term | Restart or reconfigure DNS service |
| Ongoing | Monitor for unusual traffic patterns (potential DoS) |

<br><br>

## 9. Skills Demonstrated

- Network traffic analysis using `tcpdump`
- Understanding of TCP/IP protocols (UDP, ICMP, DNS)
- Log interpretation and incident investigation
- Root cause analysis in cybersecurity incidents
- Technical documentation for troubleshooting

<br><br>

## 10. Reflection

This lab reinforced practical network troubleshooting skills. Key takeaways:

- How DNS resolution fails when port 53 is unreachable
- The role of ICMP in delivering network error messages
- Using packet analysis to isolate root cause without relying on application‑level logs

**Demonstrates:** Network analysis, protocol behavior understanding, and systematic incident investigation.

<br><br>

## 11. Appendix: Key Terminology

| Term | Meaning |
|------|---------|
| DNS | Domain Name System – translates domain names to IP addresses |
| ICMP | Internet Control Message Protocol – used for error reporting |
| UDP | User Datagram Protocol – connectionless transport protocol |
| A record | DNS record that maps a domain to an IPv4 address |
| Port 53 | Standard port for DNS traffic |
| tcpdump | Command‑line packet analyzer |

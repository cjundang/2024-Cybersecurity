---
marp: true
theme: default
paginate: true
footer: "CompTIA Security+ — Chapter 9: Perimeter & Firewall Security | © Walailak University"
title: "Chapter 9: Perimeter & Firewall Security"
---

# 🔥 Chapter 9: Perimeter & Firewall Security
### CompTIA Security+ Study Slides  
Walailak University — Assist. Prof. Dr. CJ  

---

## 🎯 Learning Objectives
- Understand **perimeter security architecture**  
- Describe **firewall types and filtering methods**  
- Explain **IDS and IPS** operation and deployment  
- Recognize **proxy servers, honeypots, and DLP** systems  
- Discuss **Unified Threat Management (UTM)** and **Next-Gen Firewalls (NGFW)**  

---

## 🧭 Overview
**Perimeter security** protects the boundary between internal trusted networks (LAN) and untrusted networks (WAN/Internet).

🎯 **Goal:**  
Control, inspect, and monitor traffic entering or leaving the organization’s network.

---

## 🧱 Layers of Network Defense
- **Perimeter Layer:** Firewalls, IDS/IPS, proxies  
- **Internal Layer:** VLANs, NAC, endpoint firewalls  
- **Application Layer:** WAF, content filters, DLP  
- **Data Layer:** Encryption, backups, access control  

💡 *Defense in Depth ensures redundancy in protection.*

---

## 🔒 What is a Firewall?
A **firewall** is a device or software that filters network traffic between networks based on predefined rules.

**Functions:**
- Inspect inbound/outbound packets  
- Enforce security policies  
- Block unauthorized access  
- Log and audit connections  

💡 Firewalls operate mainly at **Layers 3–7** of the OSI model.

---

## 🧩 Types of Firewalls

| Type | Description | Example Use |
|-------|--------------|--------------|
| **Packet-Filtering Firewall** | Inspects headers (IP, port, protocol) | Basic filtering; low overhead |
| **Stateful Firewall** | Tracks connection states; allows return traffic | Enterprise border firewall |
| **Circuit-Level Gateway** | Monitors session setup (TCP handshake) | Proxy servers |
| **Application-Layer Gateway (Proxy)** | Deep inspection of specific applications | HTTP, SMTP, FTP filtering |
| **Next-Generation Firewall (NGFW)** | Combines firewall, IPS, and application control | Modern enterprise defense |

---

## ⚙️ Packet Filtering Example
**Stateless Filtering:**  
```

permit tcp any any eq 80
deny ip any any

```
- Evaluates each packet individually  
- Faster but less context-aware  
- Suitable for low-risk environments  

**Stateful Inspection:**  
- Tracks sessions (TCP SYN/ACK)  
- Only allows valid return traffic  
- Prevents spoofing and DoS attempts  

---

## 🧠 NAT Filtering
**Network Address Translation (NAT)** hides internal IP addresses by mapping them to public addresses.

**Advantages:**
- Adds layer of anonymity  
- Limits external attack surface  
- Supports private IP reuse  

**Types:**
- Static NAT, Dynamic NAT, PAT (Port Address Translation)

---

## 🔐 Firewall Rule Best Practices
1. Use **implicit deny** as the last rule.  
2. Document and review rules regularly.  
3. Apply **least privilege** — only open necessary ports.  
4. Separate inbound and outbound rule sets.  
5. Enable **logging and alerts**.  
6. Restrict administrative access (SSH, HTTPS only).  

💡 *A misconfigured firewall is as dangerous as no firewall at all.*

---

## 🧱 Application-Layer Gateways
Operate at **OSI Layer 7** (Application Layer).  
- Perform **deep packet inspection (DPI)**  
- Detect malicious payloads and web attacks  
- Filter content based on keywords or MIME types  

**Examples:** HTTP proxy, Email security gateway, Web Application Firewall (WAF)

---

## 🧰 Proxy Servers
**Definition:** intermediary between client and external network.  

**Functions:**
- Cache frequently accessed websites  
- Filter URLs and block categories  
- Hide internal IP addresses (anonymization)  
- Log user activity  

| Type | Description |
|------|--------------|
| **Forward Proxy** | Protects internal clients accessing Internet |
| **Reverse Proxy** | Protects servers from external clients |

---

## 🧩 Web Security Gateway
An advanced proxy that integrates:
- **Malware scanning**  
- **Content filtering**  
- **Data Loss Prevention (DLP)**  
- **URL categorization and SSL inspection**

Example products: Forcepoint, Cisco Umbrella, Zscaler

---

## 🚨 Intrusion Detection Systems (IDS)
**Purpose:** monitor traffic for suspicious patterns or policy violations.

| Type | Description |
|------|--------------|
| **HIDS (Host-based IDS)** | Installed on a host; monitors OS logs |
| **NIDS (Network-based IDS)** | Monitors network traffic using packet sniffing |

**Detection Techniques:**
- **Signature-based:** compares traffic to known patterns  
- **Anomaly-based:** detects deviation from normal behavior  

---

## 🛑 Intrusion Prevention Systems (IPS)
**Definition:**  
An inline security system that can **detect, block, or mitigate** attacks in real time.

- Can drop malicious packets or reset connections  
- Integrated with firewalls or deployed standalone  
- Defends against:
  - Brute-force attempts  
  - Buffer overflows  
  - DoS/DDoS attacks  

💡 IDS = passive monitoring; IPS = active prevention.

---

## 🧠 IDS/IPS Alerts
| Alert Type | Meaning |
|-------------|----------|
| **True Positive** | Legitimate attack detected correctly |
| **False Positive** | Normal activity misidentified as attack |
| **True Negative** | Normal activity correctly ignored |
| **False Negative** | Attack not detected |

🎯 **Objective:** Minimize false positives and negatives through tuning.

---

## 🧩 IDS/IPS Deployment Modes
- **Inline Mode:** directly intercepts packets (for IPS)  
- **Passive Mode:** copies and analyzes traffic (for IDS)  
- **Promiscuous Mode:** captures all packets on the segment  

**Placement:** between core switch and firewall or at DMZ ingress/egress.

---

## 🧲 Honeypots and Honeynets
**Honeypot:** a decoy system designed to attract attackers.  
**Honeynet:** a network of honeypots for research or detection.

**Purpose:**
- Study attacker behavior  
- Divert malicious traffic  
- Detect early-stage reconnaissance  

⚠️ Should be isolated from production systems.

---

## 📤 Data Loss Prevention (DLP)
**Definition:** systems that detect and prevent unauthorized data transmission.

**Types:**
- **Endpoint DLP** – monitors data on user devices  
- **Network DLP** – scans outbound traffic for sensitive data  
- **Storage DLP** – checks data at rest on servers or databases  

**Example Controls:**
- Block transfer of credit card numbers or confidential files  
- Enforce encryption for outbound email attachments  

---

## 🧱 Unified Threat Management (UTM)
**UTM appliances** combine multiple security features in one device.

| Component | Function |
|------------|-----------|
| **Firewall** | Filters traffic |
| **IDS/IPS** | Detects and blocks intrusions |
| **Anti-malware** | Scans inbound/outbound content |
| **VPN** | Provides secure remote access |
| **DLP/Content Filter** | Prevents data exfiltration |
| **Reporting/SIEM** | Centralized logging and analysis |

💡 Also known as **Next-Generation Firewalls (NGFW)**.

---

## ⚙️ UTM / NGFW Advantages
- Simplifies management with single console  
- Provides deeper inspection and correlation  
- Offers scalability for SMBs and enterprises  
- Reduces hardware and maintenance cost  

⚠️ Potential downsides:  
- Single point of failure  
- Performance impact under high throughput  

---

## 🧠 Designing the Perimeter Defense
1. Deploy **firewalls** at network boundaries.  
2. Place **IDS/IPS** between external and internal networks.  
3. Use **DMZ** for public-facing servers.  
4. Employ **proxy servers** for outbound control.  
5. Implement **DLP** and **logging/SIEM** for visibility.  
6. Regularly audit and test firewall rules.

---

## 🔁 Example Perimeter Architecture
```

[Internet]
|
[Edge Router]
|
[Firewall / NGFW]
|
[DMZ: Web, Mail, DNS]
|
[Internal Firewall]
|
[LAN + Servers + IDS + SIEM]

```

💡 Layered perimeter reduces risk of total compromise.

---

## ✅ Best Practices Summary
- Maintain **defense in depth** across network layers  
- Use **stateful or NGFW** for perimeter control  
- Tune IDS/IPS to reduce false alerts  
- Monitor and log all perimeter activities  
- Test configuration regularly with **vulnerability scans** and **pen tests**

---

# 🏁 End of Chapter 9  
### Next: **Chapter 10 — Cloud Security & Virtualized Infrastructure**
```


# Cybersecurity Lecture Series  
### Designed and Delivered by Assist. Prof. Dr. Chanankorn Jandaeng  
Walailak University | 📧 chatchanan.ja@mail.wu.ac.th  


## Course Overview

This repository contains a comprehensive ten-chapter lecture series on **Foundations and Practices in Cybersecurity**.  
Each lecture (01.md – 10.md) is designed for use with **Marp** to create professional slide decks that combine theoretical foundations, applied demonstrations, and research-driven insights.  

The curriculum emphasizes the connection between **network operations**, **threat behavior**, **monitoring systems**, and **security automation** — guiding learners from core concepts to advanced implementation with ML and real-time dashboards.



## Learning Outcomes

After completing the series, students will be able to:

1. Explain and apply the **CIA and DAD Triads** in designing secure systems.  
2. Recognize vulnerabilities and threats across different cybersecurity domains.  
3. Understand **network protocols** and their inherent weaknesses affecting security.  
4. Capture, dissect, and analyze network traffic using tools such as **Wireshark** and **tshark**.  
5. Identify, simulate, and mitigate common **attacks** (e.g., ARP spoofing, DoS).  
6. Configure and test **firewalls, ACLs, and LAN security controls**.  
7. Integrate **machine learning** techniques for malware and anomaly detection.  
8. Design and implement **log management** and **dashboard visualization** systems.  
9. Deploy **IDS/IPS (Snort, Suricata)** for active network defense.  
10. Build **automated, ML-integrated security pipelines** with **WebSocket real-time monitoring**.



## Chapter Summaries

### **01. Introduction to Cybersecurity**

Introduces fundamental principles of **information assurance**:  
- **CIA Triad** (Confidentiality, Integrity, Availability) and **DAD Triad** (Disclosure, Alteration, Denial).  
- Cybersecurity domains, including network security, cryptography, risk management, and incident response.  
- The concept that *“Security is Protective of Assets”* serves as the philosophical and practical anchor.  

Learners examine threats, vulnerabilities, and attack surfaces, establishing the mental model of defense and assurance.



### **02. Network and Protocol Fundamentals**

Provides the networking foundation essential for traffic monitoring and later analysis.  
Topics include:
- IP addressing, subnet masks, gateways, and DNS servers.  
- OSI and TCP/IP models.  
- Core protocols: **TCP/UDP, IP, ICMP, HTTP, HTTPS, ARP, DNS**.  
- Discussion of protocol weaknesses exploited in common attacks.  
- Overview of routers, switches, firewalls, IDS/IPS, and access points in layered defense.

This chapter concludes with an extended explanation of how device interconnections influence visibility in network monitoring and security architecture.


### **03. Traffic Analysis with Wireshark**

Students learn to observe network behavior under normal conditions before intrusion simulation.  
- Packet dissection using Wireshark and command-line **tshark**.  
- Creation of **display and capture filters**.  
- Understanding traffic flows, TCP handshakes, and protocol hierarchies.  
- Introduction to **PyShark** for programmatic traffic analysis and log conversion.

This prepares learners for anomaly detection using ML in the following modules.



### **04. Threats, Attacks, and Security Troubleshooting**

Examines attack types, techniques, and defensive troubleshooting:
- Malware behavior, Denial-of-Service (DoS), and Man-in-the-Middle (MITM) attacks.  
- Security misconfiguration and privilege escalation.  
- Demonstration of **ARP spoofing** and detection techniques.  
Students analyze how network protocols can be manipulated, leading to security failures.



### **05. Firewall Concepts and Configuration**

Focuses on packet filtering and perimeter defense:
- Packet vs. stateful inspection, NAT, port forwarding, and ACL design.  
- Understanding of security zones and policy hierarchies.  
- Step-by-step configuration using **Cisco IOS commands**.  
- Practical demonstration of firewall and ACL deployment in **Cisco Packet Tracer**.

Objective: build confidence in configuring access control and traffic inspection rules to mitigate unauthorized communication.



### **06. LAN Security**

Explores endpoint and access-layer protection:
- **Port security**, **VLAN segmentation**, **NAC (Network Access Control)**, **DHCP snooping**, and **Dynamic ARP Inspection (DAI)**.  
- Theoretical explanation of LAN attack surfaces, including MAC flooding and VLAN hopping.  
- Detection and prevention techniques demonstrated through Packet Tracer.  

Students learn to balance usability and isolation within switched environments.



### **07. Malware Detection with Machine Learning**

Integrates cybersecurity and AI disciplines:
- Malware taxonomy: virus, worm, trojan, ransomware, spyware, rootkit, botnet.  
- Techniques of detection — static vs. dynamic analysis.  
- **Feature extraction from PE files (static)** and **CFG-based DNA strings**.  
- Feature selection, dataset labeling, and ML model training (SVM, Random Forest, Isolation Forest).  
- Evaluation and visualization of model performance.

The chapter bridges traditional malware analysis with modern ML-based defense pipelines.


### **08. Traffic Anomaly Detection with Machine Learning**

Advances from packet capture to flow analysis:
- Flow data generation (NetFlow, IPFIX).  
- Feature engineering and normalization.  
- Implementation of **Isolation Forest** and clustering algorithms in Python using **pandas** and **scikit-learn**.  
- Differentiating normal vs. anomalous network behavior.  

Demonstrations emphasize how unsupervised learning supports proactive detection of emerging threats.

### **09. Log and Audit Log Management**

Covers the foundation and operationalization of event tracking systems:contentReference[oaicite:0]{index=0}:
- Definition, purpose, and structure of audit logs.  
- Log standards: **Syslog (RFC 5424)**, **CEF**, **LEEF**, **JSON/GELF**, and **Auditd**.  
- Log collection, normalization, indexing, and visualization layers (Fluentd, Logstash, Elasticsearch, Kibana).  
- Challenges: volume, variety, integrity, and retention.  
- Demonstration: building a **FastAPI service** that generates API logs and a **ReactJS dashboard** for visualization.  

Students understand how visibility and traceability strengthen accountability and compliance.


### **10. Network Monitoring Systems & Security Automation**

A synthesis of detection, analytics, and automation:contentReference[oaicite:1]{index=1}.  
Covers:
- IDS/IPS principles with **Snort** and **Suricata**.  
- Alert formats (EVE JSON), rule syntax, and tuning.  
- Handling of detection events and integration into SIEM pipelines.  
- Hands-on lab: simulate ping flood and brute-force attacks, observe alert generation.  
- Extension to **Security Automation and Integration**:
  - ML-enhanced IDS for adaptive classification.  
  - FastAPI backend streaming Suricata alerts via WebSocket.  
  - ReactJS frontend for real-time dashboards.

Outcome: learners can construct an intelligent IDS prototype capable of automated correlation and visualization.


## Course Integration Path

| Phase | Focus | Key Tools |
|-------|--------|-----------|
| 1 | Foundation & Network Basics | Wireshark, TCP/IP stack |
| 2 | Threats & Mitigation | ARP spoofing, firewall, ACL |
| 3 | LAN Protection | Cisco Packet Tracer |
| 4 | Malware & Traffic ML | Python, Scikit-learn |
| 5 | Log Analytics & Visualization | FastAPI, ReactJS |
| 6 | Intelligent IDS | Suricata, ML, WebSocket, Dashboard |

This progression ensures cumulative competency — from **data capture** to **real-time intelligence**.


## Pedagogical Design

Each lecture follows a **three-tier instructional model**:

1. **Theory (40–50%)** – Conceptual explanations and frameworks.  
2. **Demonstration (30–40%)** – Packet Tracer, Wireshark, or code-based labs.  
3. **Analysis & Reflection (10–20%)** – Interpretation of alerts, logs, or ML outcomes.

Assignments encourage experimentation with synthetic data and simulated attacks.

## Research and Extension Themes

These materials also serve as a foundation for cybersecurity research topics:

- Machine-learning-driven intrusion detection and log analytics.  
- Security automation pipelines integrating IDS and visualization.  
- Real-time SIEM and SOC optimization with open-source stacks.  
- Cloud-native monitoring and edge-device defense in IoT networks.

## Usage Notes

- Each file (`01.md` – `10.md`) is a **Marp-formatted markdown** ready for slide generation.  
- To export to PDF or HTML slides, run:

```bash
marp 01.md --pdf
````

or

```bash
marp 10.md --html
```

* Recommended sequence: deliver chapters 1–8 as lecture series, 9–10 as advanced lab modules.

## License & Acknowledgment

These materials were authored for educational use within the **Walailak University Cybersecurity Curriculum**.
They are intended for classroom teaching, research, and academic dissemination, maintaining authorship credit to:

**Assist. Prof. Dr. Chanankorn Jandaeng**
Department of Computer Science, Walailak University
📧 [chatchanan.ja@mail.wu.ac.th](mailto:chatchanan.ja@mail.wu.ac.th)


*“Security is protective of assets, but intelligence makes protection adaptive.”*
— Course Philosophy

---
marp: true
theme: default
paginate: true
footer: "CompTIA Security+ — Chapter 5: Virtualization & Cloud Security | © Walailak University"
title: "Chapter 5: Virtualization & Cloud Security"
---

# ☁️ Chapter 5: Virtualization & Cloud Security
### CompTIA Security+ Study Slides  
Walailak University — Assist. Prof. Dr. CJ  

---

## 🎯 Learning Objectives
- Define virtualization and identify its components  
- Distinguish between **Type I** and **Type II** hypervisors  
- Explain common virtualization security threats and mitigations  
- Describe cloud models: **SaaS**, **PaaS**, **IaaS**, and **SECaaS**  
- Apply cloud security best practices and data protection techniques  

---

## 🧭 What is Virtualization?
**Definition:**  
Virtualization is the creation of a **virtual resource** — such as servers, storage, or networks — abstracted from physical hardware.

**Benefits:**  
- Consolidation of physical resources  
- Cost efficiency and energy savings  
- Rapid deployment and scalability  
- Snapshot and rollback capabilities  

🎯 Enables **cloud computing** and flexible IT infrastructure.

---

## 🖥️ Virtual Machines (VMs)
A **Virtual Machine (VM)** is an emulated computing environment that runs its own OS and applications.  

- **System VM:** full OS virtualization (e.g., Windows Server on ESXi)  
- **Process VM:** isolates a single application or process  

Each VM behaves like an independent system but shares host hardware.

---

## ⚙️ The Hypervisor
**Hypervisor:** software or firmware that manages VMs and allocates hardware resources.

| Type | Description | Examples |
|------|--------------|-----------|
| **Type I (Bare-Metal)** | Runs directly on hardware; better performance and isolation | VMware ESXi, Microsoft Hyper-V (Core), XenServer |
| **Type II (Hosted)** | Runs on top of a host OS | VMware Workstation, Oracle VirtualBox |

💡 Type I is used in production; Type II is preferred for labs or development.

---

## 🧩 Containerization
**Definition:**  
Application-level virtualization that shares a single OS kernel while isolating applications in containers.

**Advantages:**  
- Lightweight, faster deployment than full VMs  
- Consistent environments across development and production  
- Easier scaling in microservice architectures  

**Examples:** Docker, Podman, Kubernetes, OpenVZ  

---

## 🧱 Virtualization Threats

| Threat | Description | Mitigation |
|--------|--------------|------------|
| **VM Escape** | Attacker breaks isolation and interacts with hypervisor or other VMs | Patch hypervisors, limit privileged access |
| **Data Remnants** | Residual data left after VM deletion | Secure wiping, encryption at rest |
| **Privilege Escalation** | Compromise admin-level access through VM or host flaws | RBAC, logging, MFA |
| **VM Sprawl** | Uncontrolled VM creation leading to unmonitored assets | Centralized inventory, automated management |

---

## 🧰 Securing Virtual Machines
- Limit host-to-guest and guest-to-guest connectivity  
- Remove unnecessary virtual hardware (e.g., CD-ROM, USB passthrough)  
- Maintain patching and antivirus on both host and guest  
- Enforce **secure configurations** and isolation policies  
- Use **snapshot management** carefully — snapshots contain sensitive data  

---

## ⚡ Live Migration Security
**Definition:** moving a running VM from one host to another without downtime.

**Risks:**  
- Exposure of VM memory contents during transfer  
- Man-in-the-middle or hijacking of migration channel  

**Mitigation:**  
- Encrypt migration traffic (TLS, IPsec)  
- Use dedicated migration networks  
- Authenticate hosts before migration  

---

## 🧱 Virtual Network Security
- Implement VLANs or software-defined networks (SDN) for isolation  
- Use virtual firewalls to segment inter-VM communication  
- Monitor traffic with virtual IDS/IPS sensors  
- Disable promiscuous mode on virtual NICs  
- Apply same network hardening rules as physical environments  

---

## ☁️ Cloud Computing Overview
**Definition:**  
Cloud computing delivers computing services — servers, storage, applications — over the Internet on-demand.

**Key Characteristics:**  
- On-demand self-service  
- Broad network access  
- Resource pooling  
- Rapid elasticity  
- Measured service (pay-as-you-go)

---

## 🧭 Cloud Deployment Models
| Model | Description | Example Use |
|--------|--------------|--------------|
| **Public Cloud** | Shared infrastructure provided by third-party vendor | AWS, Azure, Google Cloud |
| **Private Cloud** | Dedicated infrastructure managed internally | Corporate data centers |
| **Hybrid Cloud** | Combination of public and private resources | Disaster recovery, cloud bursting |
| **Community Cloud** | Shared by multiple organizations with common interests | Research or government consortiums |

---

## 🧮 Cloud Service Models

| Model | Provider Manages | Customer Manages | Example |
|--------|------------------|------------------|----------|
| **IaaS** (Infrastructure as a Service) | Networking, storage, servers | OS, apps, data | AWS EC2, Azure VM |
| **PaaS** (Platform as a Service) | OS, middleware, runtime | Applications, data | Google App Engine, Heroku |
| **SaaS** (Software as a Service) | Entire stack (apps to hardware) | User access | Office 365, Salesforce |
| **SECaaS** (Security as a Service) | Security capabilities delivered via cloud | Usage policies | Cloud-based AV, DLP, IAM |

---

## 🧠 Cloud Security Challenges
- **Multi-tenancy:** data from multiple clients coexists on shared infrastructure  
- **Data privacy and compliance:** storage location and jurisdiction concerns  
- **Access control:** managing identities across hybrid environments  
- **Visibility and monitoring:** loss of control over logs and telemetry  
- **Misconfiguration:** most common cause of cloud data breaches  

---

## 🛡️ Cloud Security Controls
1. **Encryption:** protect data at rest and in transit  
2. **Identity & Access Management (IAM):** enforce least privilege, MFA  
3. **Network Segmentation:** isolate workloads with VPCs, subnets  
4. **Security Groups / Firewalls:** restrict inbound/outbound connections  
5. **Logging & Monitoring:** use CloudWatch, Azure Monitor, SIEM integration  
6. **Compliance Frameworks:** CIS Benchmarks, ISO 27017, CSA CCM  

---

## 🧩 Cloud Data Protection
- **DLP (Data Loss Prevention):** monitor uploads and email attachments  
- **Tokenization:** replace sensitive data with reversible tokens  
- **Anonymization:** irreversible data masking for privacy  
- **Backups & Replication:** ensure geographic redundancy  
- **Key Management Services (KMS):** manage encryption keys securely  

---

## 🧬 Sandboxing & Testing
- **Sandboxing:** isolated environment for analyzing untrusted code or malware  
- Used in:  
  - Cloud security gateways  
  - Email and web filters  
  - Malware analysis labs  
- Prevents malicious execution from affecting production systems  

---

## 📡 Continuous Monitoring
- Automated collection and analysis of cloud metrics and logs  
- Detects misconfigurations, intrusions, or policy violations  
- Integrates with **SIEM** (Security Information and Event Management) tools  
- Examples: AWS GuardDuty, Azure Defender, Google Security Command Center  

---

## 🔁 Business Continuity & Disaster Recovery in Cloud
- **BCP (Business Continuity Plan):** ensure operations remain functional  
- **DR (Disaster Recovery):** restore systems after outage or compromise  

**Cloud Strategies:**  
- Multi-region replication  
- Snapshot backups  
- Automated failover  
- Cold, warm, or hot site models  

---

## 🧾 Shared Responsibility Model
| Responsibility | Cloud Provider | Customer |
|----------------|----------------|-----------|
| **Physical Security** | ✅ | ❌ |
| **Network Security (core)** | ✅ | ❌ |
| **OS and Application Security** | ⚠️ Shared | ⚠️ Shared |
| **Data and Access Management** | ❌ | ✅ |
| **Compliance and Governance** | ⚠️ Shared | ⚠️ Shared |

💡 *Security in the cloud is shared between provider and customer.*

---

## 🧠 Best Practices Summary
- Harden hypervisors and enforce least privilege  
- Encrypt data and communications  
- Apply secure baselines to all virtualized workloads  
- Monitor continuously for anomalies  
- Review compliance with organizational and legal standards  

---

## ✅ Key Takeaways
- Virtualization increases efficiency but adds complexity and new threats  
- Cloud computing delivers flexibility but requires shared security responsibilities  
- Defense-in-depth must extend to virtual and cloud layers  
- Security automation and monitoring are vital for cloud resilience  

---

# 🏁 End of Chapter 5  
### Next: **Chapter 6 — Application & Software Security**

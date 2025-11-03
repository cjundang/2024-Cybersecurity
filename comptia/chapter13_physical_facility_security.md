---
marp: true
theme: default
paginate: true
footer: "CompTIA Security+ — Chapter 13: Physical & Facility Security | © Walailak University"
title: "Chapter 13: Physical & Facility Security"
---

# 🏢 Chapter 13: Physical & Facility Security
### CompTIA Security+ Study Slides  
Walailak University — Assist. Prof. Dr. CJ  

---

## 🎯 Learning Objectives
- Understand **physical and environmental security principles**  
- Identify types of **physical access controls** and **surveillance systems**  
- Explain **biometric authentication** and error metrics  
- Describe **facility protection mechanisms** (locks, barriers, mantraps)  
- Discuss **fire suppression**, **HVAC**, and **shielding controls**

---

## 🧭 Overview
Even the most secure network can be compromised if **attackers gain physical access**.

🎯 **Goal:** Protect people, hardware, and data centers from physical threats such as:  
- Unauthorized access  
- Theft or vandalism  
- Natural disasters  
- Environmental hazards  

---

## 🧱 Layers of Physical Security
1. **Perimeter Security** – fences, gates, guards, lighting  
2. **Building Security** – doors, locks, ID badges, CCTV  
3. **Internal Access Control** – mantraps, biometrics, secure zones  
4. **Data Center Security** – server cages, access logs, alarms  
5. **Environmental Controls** – fire suppression, HVAC, shielding  

💡 *Defense in depth applies to the physical world too.*

---

## 🚪 Physical Access Controls
**Physical Controls:** tangible barriers to prevent unauthorized entry.

| Control Type | Examples |
|---------------|-----------|
| **Mechanical** | Locks, keys, safes |
| **Electronic** | Smart cards, keypads, RFID badges |
| **Biometric** | Fingerprint, iris, facial recognition |
| **Administrative** | Security policies, visitor logs, escorts |

---

## 🧍‍♂️ Security Guards & Access Policies
- Act as deterrents and first responders  
- Verify credentials and monitor access points  
- Maintain **visitor logs** and **sign-in/out procedures**  
- Enforce **two-person control** in high-security areas  

💡 Human oversight complements electronic systems.

---

## 🎥 CCTV Surveillance
**Closed-Circuit Television (CCTV):** monitors and records activity for deterrence and forensics.

| Type | Description |
|-------|--------------|
| **Fixed Camera** | Constant view of a defined area |
| **PTZ (Pan-Tilt-Zoom)** | Remote directional and zoom control |
| **Infrared/Night Vision** | Records in low-light environments |
| **IP-based CCTV** | Digital, networked, supports remote access |

**Best Practices:**
- Retain recordings per policy (e.g., 30–90 days)  
- Secure footage against tampering  
- Ensure compliance with privacy regulations  

---

## 🧱 Door Locks & Entry Systems
| Mechanism | Example | Notes |
|------------|----------|-------|
| **Keyed Locks** | Mechanical keys | Simple, inexpensive |
| **Electronic Locks** | Keypad PIN, smart card | Centralized management |
| **RFID / Proximity Cards** | Badge readers | Common in enterprises |
| **Biometric Locks** | Fingerprint, retina scan | High assurance |

💡 Always pair **mechanical + electronic** controls for redundancy.

---

## 🚧 Mantraps
**Mantrap:** small vestibule with two interlocking doors that require sequential authentication.

**Purpose:**
- Prevent tailgating or piggybacking  
- Enforce single-person entry  
- Often used in data centers and secure areas  

🎯 Ensures “**one person, one entry**” policy.

---

## 🧠 Biometrics
**Definition:** authentication based on unique physical or behavioral characteristics.

| Type | Example |
|-------|----------|
| **Physiological** | Fingerprint, iris, retina, facial recognition |
| **Behavioral** | Typing rhythm, voice, gait |

**Advantages:** hard to forge, convenient for users.  
**Disadvantages:** cost, potential privacy concerns, false matches.

---

## 🔢 Biometric Accuracy Metrics
| Metric | Description |
|---------|--------------|
| **FAR (False Acceptance Rate)** | Probability an unauthorized person is accepted |
| **FRR (False Rejection Rate)** | Probability an authorized person is denied |
| **CER (Crossover Error Rate)** | Point where FAR and FRR are equal; measures overall accuracy |

💡 Lower **CER** = higher system accuracy.

---

## 🔒 Security Zones
Divide facilities into areas with increasing sensitivity.

| Zone | Example | Access Level |
|-------|----------|--------------|
| **Public Zone** | Reception, lobby | Low |
| **Restricted Zone** | Office area | Medium |
| **Secure Zone** | Data center, server room | High |
| **Controlled Zone** | Vault, command center | Very High |

**Access Principle:** enforce **least privilege** and **need-to-enter**.

---

## 🔥 Fire Suppression Systems
**Purpose:** control or extinguish fires without damaging critical assets.

| Type | Description | Suitable For |
|------|--------------|---------------|
| **Class A** | Ordinary combustibles (wood, paper) | Offices |
| **Class B** | Flammable liquids (oil, fuel) | Labs, garages |
| **Class C** | Electrical fires | Server rooms |
| **Class D** | Combustible metals | Industrial sites |
| **Class K** | Kitchen oils and fats | Cafeterias |

---

## 💨 Fire Suppression Methods
| System Type | Mechanism | Notes |
|--------------|------------|-------|
| **Wet Pipe Sprinkler** | Water always in pipes | Fast response; risk of water damage |
| **Dry Pipe Sprinkler** | Air in pipes until heat triggers | For cold areas or data centers |
| **Pre-Action System** | Requires both smoke and heat sensors | Reduces accidental activation |
| **Clean Agent System** | Gas-based (FM-200, CO₂, Halon) | Safe for electronics |

💡 *Clean agent systems are ideal for server environments.*

---

## 🌡️ HVAC and Environmental Controls
**HVAC:** Heating, Ventilation, and Air Conditioning

**Security Roles:**
- Maintain temperature and humidity (~40% humidity ideal)  
- Prevent static buildup and overheating  
- Filter dust and contaminants  
- Connect to building monitoring systems (BMS, SCADA)

🎯 Protect IT equipment from environmental hazards.

---

## 🛡️ Shielding and TEMPEST
**Electromagnetic Emanation (EME):** unintentional emission of signals that may leak sensitive data.

**Countermeasures:**
- **STP (Shielded Twisted Pair)** cabling  
- **Faraday Cage:** conductive enclosure blocking RF signals  
- **TEMPEST Standard:** U.S. gov’t specification for emission security  
- **EMP Protection:** safeguards against electromagnetic pulses  

💡 Critical for military, intelligence, and financial data centers.

---

## 🚗 Vehicle & Perimeter Security
- **Barriers/Bollards:** prevent vehicle ramming attacks  
- **Guards & Gates:** control vehicle access points  
- **License Plate Recognition (LPR)** for authorized vehicles  
- **Air Gaps:** physically isolate secure networks from public access  

🎯 Combine physical deterrents with procedural controls.

---

## ⚙️ Facility Monitoring & Maintenance
- Regular physical inspections  
- Test alarms, sensors, and backup power (UPS/generator)  
- Maintain access logs and camera records  
- Integrate with **Security Information and Event Management (SIEM)**  

💡 Continuous monitoring = continuous protection.

---

## ✅ Best Practices Summary
- Enforce multi-layered physical security  
- Use CCTV, mantraps, and access logs for accountability  
- Protect against fire, heat, and environmental threats  
- Implement clean agent systems for IT areas  
- Apply shielding to prevent data leakage  

---

# 🏁 End of Chapter 13  
### Next: **Chapter 14 — Authentication & Identity Management**

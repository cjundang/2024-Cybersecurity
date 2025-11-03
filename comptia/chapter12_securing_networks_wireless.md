---
marp: true
theme: default
paginate: true
footer: "CompTIA Security+ — Chapter 12: Securing Networks & Wireless Systems | © Walailak University"
title: "Chapter 12: Securing Networks & Wireless Systems"
---

# 📡 Chapter 12: Securing Networks & Wireless Systems
### CompTIA Security+ Study Slides  
Walailak University — Assist. Prof. Dr. CJ  

---

## 🎯 Learning Objectives
- Understand **wired vs. wireless network vulnerabilities**  
- Explain **WEP, WPA, WPA2, and WPA3** security protocols  
- Recognize **WPS weaknesses** and disable insecure features  
- Identify **rogue access points** and **evil twin attacks**  
- Apply wireless hardening and monitoring best practices  

---

## 🧭 Overview
Wireless networks introduce unique security challenges:  
- Signals travel through the air (no physical boundary)  
- Devices join dynamically  
- Users expect mobility and convenience  

🎯 **Goal:** balance accessibility with strong encryption and authentication.

---

## 🧱 Wired vs. Wireless Security
| Aspect | Wired Network | Wireless Network |
|--------|----------------|------------------|
| **Medium** | Copper/fiber cables | Radio frequency (RF) |
| **Access Control** | Physical port security | Open air; harder to restrict |
| **Threat Surface** | Local access only | Extended range (up to 300m+) |
| **Primary Risks** | Sniffing, port scanning | Eavesdropping, rogue APs, jamming |

💡 *Wireless attacks can originate from outside physical premises.*

---

## 🔐 Wi-Fi Security Evolution
| Protocol | Key Features | Weakness |
|-----------|---------------|-----------|
| **WEP (Wired Equivalent Privacy)** | RC4 stream cipher, 24-bit IV | Easily cracked within minutes |
| **WPA (Wi-Fi Protected Access)** | TKIP, message integrity (MIC) | Legacy, weak by today’s standards |
| **WPA2** | AES-CCMP encryption, 802.11i standard | Strong, but vulnerable to KRACK |
| **WPA3** | SAE handshake, forward secrecy | Current standard; resists offline brute-force |

💡 Always use **WPA3 (or WPA2-AES)** — never use WEP or TKIP.

---

## 🧩 WEP — Wired Equivalent Privacy
- Introduced in 1999 (IEEE 802.11b)  
- Uses **RC4** encryption and a **24-bit Initialization Vector (IV)**  
- Predictable IVs → repeated keys → crackable with Aircrack-ng  

**Why WEP Failed:**
- Short IV reuse leads to key collisions  
- Weak checksum (CRC-32)  
- Authentication bypass possible  

⚠️ **Deprecated:** should be completely disabled.

---

## 🔑 WPA and WPA2
### WPA (2003)
- Introduced TKIP (Temporal Key Integrity Protocol)  
- Included MIC for message integrity  
- Designed as a quick fix for WEP vulnerabilities  

### WPA2 (2004)
- Replaced TKIP with **AES-CCMP encryption**  
- Required by Wi-Fi Alliance since 2006  
- Still widely used today  

💡 WPA2-Enterprise supports 802.1X with RADIUS authentication.

---

## 🧠 WPA3 Enhancements
- Uses **Simultaneous Authentication of Equals (SAE)** instead of PSK  
- Provides **Forward Secrecy** — session keys unique per connection  
- Protects against **offline dictionary attacks**  
- Introduces **192-bit encryption mode** for enterprise environments  

🎯 WPA3 = stronger authentication + improved resilience to brute-force attacks.

---

## ⚙️ WPA Personal vs. Enterprise
| Mode | Description | Authentication |
|-------|--------------|----------------|
| **WPA/WPA2-Personal (PSK)** | Pre-shared key shared among users | Password-based |
| **WPA/WPA2-Enterprise (802.1X)** | Centralized authentication via RADIUS server | Username/password or certificate |

💡 Enterprise mode allows individual user revocation — critical for corporate Wi-Fi.

---

## 📎 Wi-Fi Protected Setup (WPS)
**WPS** simplifies device connection with an 8-digit PIN or push-button setup.  

⚠️ **Vulnerability:**  
- The 8-digit PIN can be brute-forced in hours.  
- Many routers fail to lock out repeated attempts.  
- Exposes network even with WPA2 enabled.  

**Best Practice:**  
➡️ **Disable WPS** entirely on all access points.

---

## 🚨 Rogue Access Points (Rogue AP)
**Definition:** unauthorized AP connected to the network — either malicious or accidental.

**Risks:**
- Bypasses firewall and NAC  
- Enables sniffing and credential theft  
- May connect to attacker’s laptop acting as gateway  

**Detection:**
- Wireless Intrusion Detection System (WIDS)  
- Regular site surveys (e.g., AirMagnet, Kismet)  

---

## 🎭 Evil Twin Attack
**Evil Twin:** a rogue AP mimicking a legitimate SSID to trick users into connecting.

**Steps:**
1. Attacker sets up fake AP with same SSID.  
2. Victim connects automatically.  
3. Attacker captures credentials or injects malware.  

**Prevention:**
- Use **VPN** for all Wi-Fi sessions  
- Validate certificate of authentication server (RADIUS)  
- Educate users not to connect to open networks  

---

## 📶 Wireless Jamming
**Definition:** deliberate transmission of radio interference to disrupt Wi-Fi communication.

**Methods:**
- Continuous RF noise generation  
- Deauthentication floods  
- Targeted channel interference  

**Defense:**
- Spectrum analysis to locate jammer  
- Switch channels or frequencies  
- Use **5 GHz** or **6 GHz Wi-Fi** bands for resilience  

---

## 🧩 Initialization Vector (IV) Attacks
- Exploits repeated IVs in WEP and early WPA  
- Enables attackers to recover encryption keys  
- Tools: Aircrack-ng, Kismet  

**Countermeasure:**  
- Use **WPA2-AES** or **WPA3-SAE**  
- Rotate keys frequently  
- Disable legacy protocols on APs  

---

## ⚠️ Deauthentication & Disassociation Attacks
Attackers send forged **deauth frames** to disconnect users from Wi-Fi.

**Purpose:**
- Force reconnect to **evil twin**  
- Capture 4-way handshake for password cracking  

**Mitigation:**
- WPA3’s **Protected Management Frames (PMF)**  
- Monitor for excessive deauth requests  
- Use WIDS/WIPS for real-time detection  

---

## 🔒 Wireless Access Point (WAP) Security Checklist
✅ Change default SSID and admin password  
✅ Disable WPS and UPnP  
✅ Use WPA2-AES or WPA3 encryption  
✅ Enable MAC filtering and DHCP reservations  
✅ Restrict signal range (lower transmit power)  
✅ Keep AP firmware updated  
✅ Log and monitor wireless connections  

---

## 🧰 Wireless Security Monitoring
- Deploy **Wireless IDS/IPS** to detect anomalies  
- Log all connections and signal strengths  
- Integrate with **SIEM** for correlation  
- Watch for:
  - Unknown SSIDs  
  - High failed authentication rates  
  - Sudden signal spikes (potential jamming)  

---

## 🧱 Wireless Network Segmentation
Separate wireless traffic based on trust and purpose:
- **Corporate WLAN:** secured, authenticated users  
- **Guest Network:** Internet-only, VLAN-isolated  
- **IoT Network:** limited access, restricted routing  
- **Management VLAN:** AP configuration only  

🎯 *Segmentation prevents lateral movement and containment breaches.*

---

## 📜 Wi-Fi Hardening Summary
| Category | Best Practice |
|-----------|----------------|
| **Encryption** | Use WPA3 or WPA2-AES |
| **Authentication** | Implement 802.1X / RADIUS |
| **Access Control** | Disable WPS, enforce strong passphrases |
| **Monitoring** | WIDS/WIPS, SIEM integration |
| **User Awareness** | Train users on SSID spoofing and public Wi-Fi risks |

---

## ✅ Key Takeaways
- **Disable outdated protocols** (WEP, WPA-TKIP, WPS)  
- **Use WPA3 with AES** and **Protected Management Frames**  
- **Detect rogue APs and evil twins** with WIDS/WIPS  
- **Segment wireless networks** by purpose  
- Continuous monitoring and firmware patching maintain resilience  

---

# 🏁 End of Chapter 12  
### Next: **Chapter 13 — Physical & Facility Security**

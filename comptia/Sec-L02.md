# Chapter 2 Malware

## **Learning Outcomes**

After completing this chapter, students should be able to:

1. **Define malware** and explain its purpose, intent, and impact on systems and users.
2. **Classify major categories of malware** (e.g., virus, worm, Trojan, ransomware, spyware, rootkit, and fileless malware) and describe their characteristics.
3. **Analyze infection and delivery mechanisms**, including email phishing, drive-by downloads, removable media, and software supply-chain attacks.
4. **Identify symptoms and indicators of compromise (IoCs)** that suggest malware presence or activity.
5. **Apply detection and response strategies**, including antivirus, endpoint detection and response (EDR), and sandboxing.
6. **Describe remediation procedures** — containment, eradication, and recovery — in alignment with incident response best practices.
7. **Recommend preventive and hardening measures**, such as patch management, least privilege, and user awareness training.
8. **Relate real-world malware incidents** (e.g., WannaCry, Conficker, NotPetya) to organizational security lessons and policies.

## **2.1 Introduction**

Malware — short for **malicious software** — refers to any program or code that is **intentionally developed to cause harm**, **steal information**, **disrupt operations**, or **gain unauthorized access** to computer systems, networks, or data.
It operates **without the user’s knowledge or consent**, exploiting weaknesses in operating systems, applications, or user behavior.

Malware represents one of the **most persistent and adaptable threats** in the cybersecurity landscape.
Modern attackers employ advanced tactics such as **obfuscation, polymorphism, and fileless execution** to evade detection and maintain persistence within target environments.

In this chapter, we examine:

* How malware functions and propagates
* The different types and families of malware
* Methods to detect, contain, and remove infections
* Best practices for preventing future compromises

Understanding these principles allows security professionals to **identify early indicators of compromise**, **implement layered defenses**, and **develop resilience against both traditional and emerging malware threats**.



## **2.2 Taxonomy of Malware**

### **Overview**

Malware is not a single type of threat but rather a **family of diverse malicious programs**, each designed to achieve specific objectives or exploit different weaknesses.
A well-structured taxonomy helps cybersecurity professionals **recognize how a threat operates**, **anticipate its behavior**, and **select appropriate countermeasures**.

The taxonomy below groups malware by **behavioral characteristics**, **infection method**, and **attacker intent**.


### **1. Viruses**

**Definition:**
A *virus* is malicious code that attaches itself to a legitimate program or file and executes when that host file is run.
It **requires user interaction** (such as opening or executing a file) to spread.

**Characteristics**

* Needs a host program or document.
* Can corrupt, modify, or delete files.
* Spreads through file sharing, email attachments, or removable media.

**Sub-types**

| Type                                            | Description                                                                                 | Example / Note           |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------ |
| **Boot-sector virus**                           | Infects the first sector of storage media, loading into memory at startup.                  | Michelangelo virus       |
| **Macro virus**                                 | Written in application macro languages (e.g., MS Office VBA). Executes when document opens. | Melissa (1999)           |
| **Program / File-infecting virus**              | Attaches to executable code (.exe, .dll).                                                   | CIH/Chernobyl            |
| **Multipartite virus**                          | Combines boot and file infection methods for resilience.                                    | Tequila                  |
| **Encrypted / Polymorphic / Metamorphic virus** | Alters code or encryption each time to avoid detection.                                     | Storm Worm, W32/Simile   |
| **Stealth / Armored virus**                     | Hides activity or resists analysis by intercepting OS calls or misleading analysts.         | Armored stealth variants |

**Defenses:** Up-to-date antivirus, application control, disallowing macros, user awareness.

### **2. Worms**

**Definition:**
A *worm* is a self-replicating, network-aware program that propagates automatically **without human intervention**.

**Characteristics**

* Exploits vulnerabilities or weak credentials.
* Consumes bandwidth and resources, causing DoS-like conditions.
* Can carry destructive payloads or install backdoors.

**Notable Examples**

* **ILOVEYOU (2000)** – email-borne worm causing billions in damage.
* **Conficker (2008)** – infected 9–15 million computers via Windows flaws.
* **WannaCry (2017)** – worm-like ransomware exploiting SMB v1 (EternalBlue).

**Mitigation:** Patch management, IDS/IPS, network segmentation, least-privilege accounts.


### **3. Trojan Horses (and RATs)**

**Definition:**
Software that **appears legitimate** but performs hidden, malicious actions once executed.

**Key Traits**

* Delivered through email attachments, fake installers, or pirated software.
* Does **not replicate** automatically like a virus or worm.
* Often installs **Remote Access Trojans (RATs)** enabling attackers to control systems.

**Common Payloads**

* Keylogging or credential theft.
* File exfiltration.
* Installation of secondary malware (botnet clients, ransomware).

**Defenses:** Application whitelisting, sandbox testing, restrict administrative rights, EDR monitoring.


### **4. Ransomware**

**Definition:**
Malware that **denies access to data or systems**—typically by encrypting files—until a ransom is paid (often in cryptocurrency).

**Life-Cycle Stages**

1. Initial Access (phishing, exploit, or RDP attack).
2. Privilege Escalation and lateral movement.
3. Data Encryption and service disruption.
4. Extortion — display ransom note or threaten data leaks.

**Real-World Cases**

* **SamSam (2018)** – Atlanta city systems crippled; losses > US $17 million.
* **Ryuk, LockBit, BlackCat** – modern targeted ransomware families.

**Mitigation:** Offline/immutable backups, segmentation, incident-response planning, user training.


### **5. Spyware / Adware / Grayware**

| Type                | Description                                                          | Example          | Defense                 |
| ------------------- | -------------------------------------------------------------------- | ---------------- | ----------------------- |
| **Spyware**         | Silently gathers information—keystrokes, browsing data, screenshots. | Keylogger Trojan | EDR, privacy settings   |
| **Adware**          | Displays unwanted ads, may redirect traffic or track activity.       | Browser toolbars | Anti-adware filters     |
| **Grayware / PUPs** | Programs that behave improperly but not overtly malicious.           | Bundled software | Whitelisting, education |

### **6. Rootkits**

**Definition:**
Software that **provides persistent privileged access** while **concealing its presence**.

**Techniques**

* **DLL Injection** – inserts malicious code into legitimate processes.
* **Driver Manipulation / Kernel Hooks** – intercept system calls at OS level.
* **Bootkits** – infect bootloader to run before the OS.

**Challenges**

* Extremely hard to detect; standard antivirus often fails.
* Removal usually requires reimaging or hardware-based trusted boot (Secure Boot, TPM).


### **7. Logic Bombs and Backdoors**

* **Logic Bomb:** Malicious code that executes when specific conditions are met (e.g., date, file deletion).
* **Backdoor:** Bypasses normal authentication to maintain covert access.
* **Policy Note:** Secure coding standards forbid both; developers must undergo code reviews and static analysis.


### **8. Botnets and Zombies**

* A **botnet** is a collection of compromised computers (zombies) controlled by an attacker (botmaster).
* Used for **DDoS**, spam distribution, or cryptocurrency mining.
* Communication may use centralized (C2 servers) or decentralized (P2P) models.

**Defenses:** Egress filtering, anomaly-based network detection, timely patching.


### **9. Fileless Malware and Living-off-the-Land (LOTL)**

* Operates directly in **memory** without writing files to disk.
* Leverages trusted tools such as **PowerShell**, **WMI**, or **certutil** to execute payloads.
* **Detection:** Behavior-based analytics, memory forensics, limiting script execution.



### **Compare**

When lecturing, stress these comparison points:

* **Virus vs. Worm:** user action vs. self-propagation.
* **Trojan vs. RAT:** disguise vs. remote control.
* **Ransomware vs. Spyware:** denial of service vs. data theft.
* **Rootkit vs. Fileless:** stealth mechanism vs. file-independent operation.


### **Summary**

Malware taxonomy illustrates the **evolution of attacker tools** from simple viruses to complex multi-stage campaigns.
Effective defense demands:

* Awareness of each category’s behavior,
* Layered detection and control mechanisms, and
* Continuous monitoring for anomalies in systems and networks.

## **2.3 Infection and Delivery Mechanisms**

### **Overview**

Malware does not appear on a system by chance — it must first **enter (infiltration)**, then **execute (infection)**, and often **propagate (spread)**.
Understanding these phases helps defenders identify **weak points** in the kill chain and implement **preventive controls**.

### **1. Terminology**

| Term              | Meaning                                                                   | Example                                                  |
| ----------------- | ------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Threat Vector** | The *path or method* an attacker uses to reach the target environment.    | Email attachments, malicious USB, unpatched web app      |
| **Attack Vector** | The specific *technique* or exploit used to gain control or execute code. | Buffer overflow, credential brute-force, macro execution |
| **Payload**       | The *malicious content or action* delivered after successful access.      | Ransomware encryption, keylogger, remote shell           |


### **2. General Infection Lifecycle**

```
+---------------------------+
| 1. Initial Access         | ← Phishing, USB, exploit
+---------------------------+
            │
            ▼
+---------------------------+
| 2. Execution / Installation| ← User click or exploit triggers code
+---------------------------+
            │
            ▼
+---------------------------+
| 3. Persistence & Evasion  | ← Adds autorun, hides process
+---------------------------+
            │
            ▼
+---------------------------+
| 4. Propagation / C2       | ← Spreads laterally, contacts attacker
+---------------------------+
            │
            ▼
+---------------------------+
| 5. Impact / Payload       | ← Data theft, encryption, sabotage
+---------------------------+
```


### **3. Primary Delivery Vectors**

#### **A. Phishing and Spear Phishing Emails**

* Most common entry point for malware.
* Attackers attach infected documents (e.g., macro-enabled .docm) or embed malicious links.
* Spear phishing targets specific individuals using social engineering.

**Example Chain:**

> User receives fake invoice email → opens attachment → macro runs PowerShell → downloads ransomware payload → system encrypts files.

**Defenses:**
Email filtering, attachment sandboxing, disable macros, awareness training.


#### **B. Drive-By Downloads**

* Occur when visiting a **compromised or malicious website** that silently delivers malware through browser or plug-in exploits.
* Uses injected JavaScript, malicious ads (*malvertising*), or outdated Flash/Java modules.

**Example:**
A user browses a news site containing a malicious ad → exploit kit detects vulnerable browser → drops trojan.

**Defenses:**
Patch browsers, enable click-to-run, use ad blockers and web reputation filters.

#### **C. Watering Hole Attacks**

* The attacker compromises a **trusted site** frequently visited by the target group (e.g., industry forum).
* When users visit, malware is automatically downloaded or redirected.

**Example:**
Government employees visit an agency partner’s web portal → injected iframe leads to exploit kit → installs spyware.


#### **D. Removable Media (USB / External Drives)**

* Malware spreads via autorun scripts or enticingly named files.
* Frequently used for **air-gapped network infiltration**.

**Example:**
Stuxnet (2010) used infected USB drives to reach isolated industrial networks.

**Defenses:**
Disable autorun, scan external devices, enforce digital signature policies.


#### **E. Network Service Exploitation**

* Worms or ransomware exploit vulnerabilities in **public-facing services** such as SMB, RDP, VPNs, or web apps.
* Requires no user interaction.

**Example:**
WannaCry exploited SMB v1 (EternalBlue) to self-propagate worldwide.

**Defenses:**
Timely patching, firewalls, strong authentication, network segmentation.


#### **F. Software Supply-Chain Attacks**

* Attackers compromise **trusted update servers or third-party libraries**.
* Malware arrives inside legitimate installers or signed updates.

**Example:**
NotPetya spread via corrupted Ukrainian tax-software update (MeDoc).

**Defenses:**
Verify code signing, restrict update sources, monitor integrity.


### **4. Execution Techniques**

Once delivered, malware must **execute** to take control:

| Method                 | Description                                             | Example                    |
| ---------------------- | ------------------------------------------------------- | -------------------------- |
| **User execution**     | Double-clicking infected file or enabling macro.        | Malicious .docx attachment |
| **Exploit execution**  | Automatic exploit of software flaw.                     | EternalBlue SMB exploit    |
| **Script abuse**       | Using legitimate interpreters like PowerShell, WMI.     | Fileless malware           |
| **Social engineering** | Persuading user to disable protection or run installer. | Fake antivirus pop-up      |


### **5. Propagation Mechanisms**

* **Email spreading:** forwards itself to contacts (e.g., ILOVEYOU).
* **Network Scanning:** probes IP ranges for vulnerable systems.
* **Shared Drives / P2P:** infects network shares or torrents.
* **Botnet Commands:** central C2 pushes new payloads.


### **6. Indicators of Delivery or Infection**

| Category          | Indicator                                                                 |
| ----------------- | ------------------------------------------------------------------------- |
| **Network**       | Unusual outbound connections to unknown IPs; sudden spike in DNS queries. |
| **Host**          | New services, autoruns, or scheduled tasks; disabled AV.                  |
| **User Behavior** | Unexpected pop-ups, file encryption notices, login anomalies.             |


### **7. Real-World Case Study: WannaCry**

**Infection Vector:**
Exploited unpatched SMB v1 vulnerability (EternalBlue).

**Execution Flow:**

1. Scans network for TCP 445 (SMB).
2. Exploits MS17-010 vulnerability.
3. Installs ransomware payload.
4. Encrypts data and displays ransom note.
5. Propagates laterally to other systems.

**Lesson:**
Patch management and segmentation are critical; a single unpatched system can compromise an enterprise.

### **Summary**

* Malware enters systems via diverse **vectors** such as phishing, compromised sites, removable media, and service exploits.
* Each stage in the infection chain offers **a defensive opportunity**: user awareness, patching, segmentation, and behavior-based monitoring.
* Recognizing delivery and execution patterns is essential to **early detection and response**.


## **2.4 Indicators of Compromise (IoCs) and Detection Techniques**

### **1. Introduction**

Even the most secure systems can be infiltrated.
Once malware gains entry, the next step in cybersecurity defense is **detection** — identifying that something abnormal is happening before major damage occurs.

Security analysts detect these anomalies through **Indicators of Compromise (IoCs)** — observable pieces of forensic evidence that suggest a system has been compromised.


### **2. What Are IoCs?**

**Definition:**

> *An Indicator of Compromise (IoC)* is any piece of digital evidence that correlates strongly with malicious activity or intrusion within an information system.

IoCs act like **“digital fingerprints”** left behind by attackers or malware.
They can appear in **network traffic, system logs, memory dumps, or file metadata.**


### **3. Common Types of IoCs**

| **Category**               | **Examples**                                                                                | **What It Indicates**                                      |
| -------------------------- | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| **File-based IoCs**        | Unusual new files, renamed system files, presence of malware hashes (MD5/SHA256).           | Possible malware installation or modification.             |
| **Process / Service IoCs** | Unknown background processes, abnormal CPU or RAM usage, creation of unauthorized services. | Execution of malicious payloads or persistence mechanisms. |
| **Network IoCs**           | Outbound connections to unknown IPs, C2 domains, or unusual ports (e.g., 4444, 1337).       | Active communication with attacker infrastructure.         |
| **Registry / System IoCs** | New autorun entries, modified startup keys, disabled security settings.                     | Persistence or defensive evasion.                          |
| **User Behavior IoCs**     | Sudden login attempts, access outside work hours, privilege escalation.                     | Possible credential theft or insider compromise.           |
| **File System Changes**    | Unexpected encryption, mass renaming, or timestamp alteration.                              | Ransomware or destructive malware activity.                |

### **4. Typical Malware IoC Patterns**

**A. Virus Infection Signs**

* Files appear with double extensions (`report.pdf.exe`).
* Antivirus logs repeated detections on the same files.
* Executables modified with unexpected timestamps.

**B. Worm or Network Propagation**

* Unexplained increase in network traffic or port scanning.
* Repeated login failures or brute-force attempts.
* Large volume of ARP or SMB traffic from a single host.

**C. Trojan or RAT**

* New remote connections established to unknown domains.
* New scheduled tasks or startup programs.
* User complaints of slow system or webcam activation light blinking.

**D. Ransomware**

* Mass encryption or `.locked` extensions appearing on files.
* Ransom note text files in multiple folders.
* Backup systems disabled or deleted.

**E. Spyware / Keylogger**

* Unexpected outbound HTTP POST requests.
* Credential reuse detected.
* Antivirus reporting suspicious DLL injections.

### **5. Detection Techniques**

Modern detection requires both **signature-based** and **behavior-based** approaches.

#### **A. Signature-Based Detection**

* Uses **known malware fingerprints** (hashes, patterns, byte sequences).
* Fast and accurate for *known threats*.
* Ineffective against **new variants** or **polymorphic** malware.

**Example:**
Traditional antivirus scanning for MD5 signatures of “ILOVEYOU” worm.

#### **B. Heuristic / Rule-Based Detection**

* Detects suspicious patterns resembling known malware families.
* Example: detecting scripts that modify registry autoruns or disable firewalls.
* May produce *false positives*, but helps identify emerging threats.

#### **C. Behavioral and Anomaly-Based Detection**

* Focuses on **what a process does**, not just its code.
* EDR (Endpoint Detection and Response) systems monitor for anomalies:

  * Process spawning PowerShell unexpectedly.
  * Large data exfiltration via FTP or HTTP.
  * Rapid file encryption rate indicating ransomware.

**Example:**
“Word.exe” launching “cmd.exe” and “powershell.exe” = suspicious chain.

#### **D. Machine Learning (ML)-Assisted Detection**

* Uses algorithms trained on benign vs. malicious behavior.
* Detects zero-day or obfuscated malware.
* Common in **modern EDRs and antivirus engines.**


#### **E. Network-Based Detection (NIDS / NIPS)**

* Analyzes traffic for malicious signatures or patterns.
* Detects:

  * Command-and-control (C2) beaconing.
  * Known malware traffic patterns (e.g., EternalBlue exploit packets).
* Tools: **Snort**, **Suricata**, **Zeek (Bro)**.


#### **F. Memory and Sandbox Analysis**

* Runs suspicious files in an **isolated virtual environment** to observe behavior.
* Reveals fileless or polymorphic malware.
* Tools: **Cuckoo Sandbox**, **Any.Run**, **Hybrid Analysis**.
* Memory forensics: **Volatility Framework** detects injected code, hidden processes.

#### **G. Threat Intelligence and IoC Feeds**

* Organizations share IoCs via platforms like **MITRE ATT&CK**, **STIX/TAXII**, or **AlienVault OTX**.
* SIEMs use these feeds for **correlation and automated alerts.**


### **6. IoC Correlation and SIEM Integration**

Security analysts integrate IoCs into **Security Information and Event Management (SIEM)** platforms.

**SIEM Functions:**

1. Collect logs from hosts, firewalls, IDS/IPS, and endpoints.
2. Correlate IoCs with live telemetry.
3. Trigger alerts when thresholds are met (e.g., multiple failed logins + external C2 traffic).

**Popular Tools:**
Splunk, IBM QRadar, Elastic Security, Microsoft Sentinel.


### **7. Real-World Example: Detecting Ransomware (WannaCry)**

| **Stage**         | **Indicator**                     | **Detection Tool**   |
| ----------------- | --------------------------------- | -------------------- |
| Exploit SMB v1    | Unusual SMB traffic (port 445)    | NIDS / Firewall Logs |
| File Encryption   | Massive file renaming `.wncry`    | EDR Behavioral Alert |
| Command & Control | Connections to kill-switch domain | SIEM Correlation     |
| Persistence       | Registry modifications            | Host-based IDS       |

### **8. Diagram: Detection Process Flow**

```
[ Data Collection ]
        │
        ▼
[ SIEM / EDR Analysis ]
        │
        ▼
[ IoC Matching + Behavioral Rules ]
        │
        ▼
[ Alert Generation ]
        │
        ▼
[ Analyst Validation & Response ]
```

### **9. Best Practices for IoC Monitoring**

* Enable **centralized logging** across servers and endpoints.
* Update **signature and threat intelligence feeds** regularly.
* Combine **network and host-based detection** for layered visibility.
* Conduct **routine baseline comparisons** to identify deviations.
* Maintain **incident response runbooks** for quick validation.


### **10. Summary**

* **IoCs** are vital forensic breadcrumbs for recognizing active infections.
* Effective detection blends **signature**, **behavioral**, and **intelligence-driven** analysis.
* Early detection minimizes impact, supports containment, and improves response efficiency.
* Integrating detection into **SIEM and EDR ecosystems** ensures continuous monitoring and threat visibility.

# Section 03: Introduction to Digital Forensics and Incident Response (DFIR)

*Estimated time: 75 minutes*

The reality of modern cybersecurity is that preventative controls eventually fail. How an organization detects, responds to, and recovers from a cyberattack is just as critical as its attempts to prevent it. This field is widely known as Digital Forensics and Incident Response (DFIR).

---

## 1. Understanding the Incident Response Process

Incident Response (IR) is a structured, methodological approach to addressing and managing the aftermath of a security breach or cyberattack (an "IT incident"). 

The **NIST Incident Response Life Cycle (SP 800-61 Rev 2)** is arguably the most recognized framework globally, containing four primary phases:

1. **Preparation**:
    - Occurs *before* an incident happens. 
    - Establishing an Incident Response Plan (IRP), ensuring security tools (EDR, SIEM) have visibility, creating communication plans, training employees, and running tabletop exercises.
2. **Detection & Analysis**:
    - Identifying the incident. 
    - Alerts fire, logs are analyzed, and security analysts determine if an event is a false positive or a true incident. The scope and impact of the incident are measured.
3. **Containment, Eradication, & Recovery**:
    - **Containment**: Stop the bleeding immediately. Disconnect compromised hosts from the network, isolate malware, and ensure backups exist.
    - **Eradication**: Remove the root cause. Delete malware, terminate malicious C2 connections, reset compromised credentials, and patch the exploited vulnerability.
    - **Recovery**: Return the affected systems to normal, fully operational secure status. Restore from clean backups and lift containments while monitoring for re-infection.
4. **Post-Incident Activity**:
    - Arguably the most important step. Conducting a "Lessons Learned" review. 
    - Documenting what happened, how it happened, how well the team responded, and generating action items to improve security posture and ensure it never happens again.

---

## 2. Understanding Incident Response Teams

Large organizations do not rely on standard IT helpdesk personnel for IR. They build dedicated, highly trained teams.

### CSIRT (Computer Security Incident Response Team)
A CSIRT (often used interchangeably with CERT—Computer Emergency Response Team) is a dedicated entity responsible for receiving, reviewing, and responding to computer security incident reports and activity internally within an organization. A mature CSIRT will have forensic investigators, malware analysts, and threat hunters.

### PSIRT (Product Security Incident Response Team)
Unlike a CSIRT which protects the *company's* internal network, a PSIRT protects the *products* the company sells to external customers. For example, if Cisco discovers a vulnerability in one of their routers, the Cisco PSIRT handles the investigation, triage, patching, and public disclosure (CVE issuance) of that vulnerability.

---

## 3. Starting a Career in Incident Response

A career in IR is fast-paced, highly analytical, and heavily rewarding. Incident Responders (often referred to as DFIR analysts) are the "cyber firefighters" of an organization. 

**Core Skills Needed:**
- Intimate knowledge of Operating Systems (Windows Internals, Linux).
- Understanding of networking and packet analysis (Wireshark/PCAP).
- Familiarity with enterprise security tooling (EDR, SIEM, SOAR).
- Calm under pressure, excellent documentation, and communication skills.

**Common Entry Points:**
Many DFIR analysts begin their careers in a **Security Operations Center (SOC)** as a Tier 1 or Tier 2 SOC Analyst, triaging alerts. Once they gain experience identifying true positives, they escalate to full blown Incident Response roles.

---

## 4. Exploring Digital Forensics

If IR is the act of stopping the attack and recovering from it, **Digital Forensics** is the scientific application of investigating *how* it happened, exactly what data was touched, and occasionally, who did it. Forensics is often required to support legal proceedings or regulatory reporting (e.g., proving exactly how many PII records were exfiltrated during a breach).

### Types of Digital Forensics:
1. **Disk / Media Forensics**: Acquiring and analyzing hard drives without altering the original data (often looking at deleted files, slack space, and MFT records).
2. **Memory (RAM) Forensics**: Analyzing volatile memory. Crucial for finding fileless malware, active network connections, and decrypted keys that vanish when a computer is powered off.
3. **Network Forensics**: Capturing and analyzing network traffic (PCAPs) to identify lateral movement, command and control (C2) communication, and data exfiltration.

---

## 5. Evidence Preservation and Chain of Custody

Because digital evidence is fragile and easily altered, Strict protocols must be followed to ensure the evidence is admissible in a court of law.

### Evidence Preservation (Order of Volatility)
When collecting evidence, responders must always gather the most volatile data first (data that could be lost immediately).
- **Rule of Thumb (Most Volatile to Least)**:
    1. CPU Registers / Cache
    2. Routing tables, ARP caches, process tables, kernel statistics
    3. Main Memory (RAM)
    4. Temporary file systems
    5. Local hard drives (Disk)
    6. Remote logging and monitoring data
    7. Physical configuration and network topology
    8. Archival media (Backups / CDs)

To collect disk data safely without altering it, forensic investigators utilize **Write Blockers** (hardware or software that prevents data from being written to a suspect drive) and perform **Bit-for-Bit Imaging** rather than standard file copying.

### Chain of Custody
The **Chain of Custody** is a formalized, chronological, written document that records the sequence of custody, control, transfer, analysis, and disposition of physical or electronic evidence.
- It answers: *Who* had the evidence? *When* did they have it? *Where* was it transported? *What* did they do with it?
- If the chain of custody is broken or undocumented for even an hour, a defense attorney can easily argue the evidence was tampered with, rendering the entire forensic investigation legally invalid.

---

## 6. Additional Resources

To practice and hone your DFIR skills, utilize the following:
- **[Hacker Repo (hackerrepo.org)](https://hackerrepo.org)**: Explore the `dfir`, `threat-hunting`, and `threat-intelligence` directories for tools, labs, and documentation related to incident response and digital forensics.
- **[Hacker Training (hackertraining.org)](https://hackertraining.org)**: Access hands-on cloud-based labs at [hackingscenarios.com](https://hackingscenarios.com) via Hacker Training to practice investigating simulated compromises without needing your own local setup.

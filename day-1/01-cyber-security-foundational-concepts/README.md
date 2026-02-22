# Section 01: Cyber Security Foundational Concepts

This section provides a deep dive into the absolute essentials of cybersecurity. Before exploring specific tools, technologies, and practices, it is crucial to understand the foundational principles that justify and secure modern environments.

---

## 1. Threats, Vulnerabilities, Exploits, and Risk

The cybersecurity landscape is driven by four interrelated concepts that must be thoroughly understood by any practitioner.

### Threats
A **threat** is any potential danger to an asset. It describes a circumstance or event that might negatively impact an organization, typically through unauthorized access, destruction, disclosure, modification of data, or denial of service. 
- **Internal Threats**: Malicious insiders, accidental data deletion by employees, hardware failure.
- **External Threats**: Hackers, state-sponsored actors, natural disasters, ransomware operators.
- **Intentional vs. Unintentional**: A threat can be a calculated attack or an unintended accident (e.g., misconfigured cloud storage).

### Vulnerabilities
A **vulnerability** is a weakness or flaw in an information system, system security procedures, internal controls, or implementation that could be exploited by a threat source. 
- **Software Flaws**: Unpatched code, buffer overflows, injection flaws.
- **Human Flaws**: Susceptibility to phishing or social engineering.
- **Configuration Flaws**: Default passwords, open ports on a firewall.

### Exploits
An **exploit** is the *act* or a piece of software, a chunk of data, or a sequence of commands that takes advantage of a vulnerability to cause unintended or unanticipated behavior in computer software, hardware, or electronic equipment. If a vulnerability is an unlocked door, an exploit is the act of opening it and walking inside.

### Risk
**Risk** is the intersection of threats and vulnerabilities. It is the probability that a threat will exploit a vulnerability and the potential impact of that event. 
- **Formula**: `Risk = Threat × Vulnerability × Impact`
- **Mitigation**: Security teams must identify risks and decide whether to **Accept** it (too costly to fix), **Avoid** it (stop using the vulnerable system), **Transfer** it (buy insurance), or **Mitigate** it (apply patches/buy security controls).

---

## 2. Understanding Defense-in-Depth

Relying on a single line of defense—such as a firewall—is a flawed strategy because a single failure compromises the entire network. **Defense-in-Depth** (DiD) refers to a multifaceted security strategy in which multiple defensive layers are deployed to protect the confidentiality, integrity, and availability of data.

No security control is perfect, but by overlapping layers, an attacker who bypasses one control will immediately be faced with another. 

### Examples of Defense-in-Depth Layers:
1.  **Data Layer**: Data encryption at rest and in transit, Data Loss Prevention (DLP) tools.
2.  **Application Layer**: Secure coding practices, Web Application Firewalls (WAF), Static/Dynamic Application Security Testing (SAST/DAST).
3.  **Host / Endpoint Layer**: Endpoint Detection and Response (EDR), Antivirus, OS Hardening, Patch Management.
4.  **Network Layer**: Next-Gen Firewalls (NGFW), Intrusion Detection/Prevention Systems (IDS/IPS), Network Segmentation.
5.  **Perimeter/Physical Layer**: Security guards, biometric locks, surveillance cameras.
6.  **Human Layer**: Security awareness training, acceptable use policies, phishing simulations.

---

## 3. Attacker Tactics, Techniques, and Procedures (TTPs)

To defend a network, you must understand how attackers operate. **TTPs** refer to the behavioral patterns and methods used by threat actors. Profiling attackers by their TTPs is far more valuable than profiling them by tools or indicators of compromise (IoCs), such as IP addresses or file hashes, because IoCs change constantly, while TTPs change rarely and require significant effort on the attacker’s part to modify.

- **Tactics**: The overarching goal or objective the adversary is trying to achieve (e.g., Initial Access, Persistence, Privilege Escalation).
- **Techniques**: How the adversary achieves the tactical objective (e.g., Phishing is a technique to achieve Initial Access).
- **Procedures**: The exact, step-by-step methodology an adversary uses, including specific tools and command lines (e.g., using `Empire` or `Cobalt Strike` to deliver a malicious Word macro payload).

**Framework Note**: The best resource for tracking and defending against TTPs is the **MITRE ATT&CK Framework**, a globally accessible knowledge base of adversary tactics and techniques based on real-world observations.

---

## 4. The CIA Triad in Real-Life

The **CIA Triad** is the foundation of information security and forms the basis on which entire security programs are built. Every control, tool, and policy is aimed at protecting one or more of these three principles:

### Confidentiality
Ensuring that data is accessible *only* to authorized individuals, entities, or processes.
- **Real-Life Impact**: If a hospital suffers a data breach and patient health records (PHI) are leaked on the internet, confidentiality has been lost.
- **Key Controls**: Encryption (AES, RSA), Access Control Lists (ACLs), Multi-Factor Authentication (MFA).

### Integrity
Safeguarding the accuracy and completeness of data. This ensures information has not been tampered with or altered by unauthorized means.
- **Real-Life Impact**: If an attacker intercepts a $100 bank transfer and modifies the payload to transfer $10,000 to their own account, integrity has been compromised.
- **Key Controls**: Hashing (SHA-256), Digital Signatures, File Integrity Monitoring (FIM).

### Availability
Ensuring that authorized users have timely and reliable access to information and assets when they need it.
- **Real-Life Impact**: If an e-commerce website is hit with a Distributed Denial of Service (DDoS) attack during Black Friday, bringing the site offline, availability has been impacted.
- **Key Controls**: Load balancing, redundancies (Hardware RAID, backup power), High Availability (HA) architectures, and offline backups.

---

## 5. Additional Resources

To deepen your understanding of these foundational concepts, explore the following resources:
- **[Hacker Training (hackertraining.org)](https://hackertraining.org)**: A hub for foundational cybersecurity resources, books (like *Practical Cybersecurity Fundamentals*), and video courses by Omar Santos.
- **[Hacker Repo (hackerrepo.org)](https://hackerrepo.org)**: A massive GitHub repository containing cheat sheets, training materials, and resources for offensive and defensive security.

*This concludes the foundational module. In the next section, we will delve into the mathematical foundation that guarantees the Confidentiality and Integrity of our data: Introduction to Cryptography.*

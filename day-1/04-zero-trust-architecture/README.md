# Section 04: Zero Trust Architecture (ZTA)

*Estimated time: 45 minutes*

Historically, network security operated on the "Castle and Moat" model. Organizations spent millions building a hardened perimeter (the moat) using firewalls and VPNs. Everything outside the perimeter was considered untrusted, but anything *inside* the network was implicitly trusted. 

This model failed. Once an attacker (or a malicious insider) bypassed the perimeter, they had free rein to move laterally across the entire network unhindered. Zero Trust is the modern answer to this problem.

---

## 1. Principles of Zero Trust (Never Trust, Always Verify)

Zero Trust Architecture (ZTA) is not a single product or tool; it is a strategic approach and a paradigm shift in cybersecurity philosophy.

The core mantra of Zero Trust is: **Never Trust, Always Verify.**

ZTA assumes that the network is *already* compromised. It removes implicit trust completely. Just because a user is physically sitting in the headquarters office plugged into the ethernet wall port, or connecting from a company-issued laptop via VPN, does *not* mean they are granted access to internal resources.

Instead, trust is continually evaluated on a per-session, per-request basis.

### Core Principles of ZTA:
1.  **Assume Breach**: Assume attackers are already present on the network and act accordingly.
2.  **Verify Explicitly**: Authenticate and authorize based on all available data points (user identity, location, device health, service or workload, data classification, and anomalies).
3.  **Use Least Privilege Access**: Limit user access with Just-In-Time (JIT) and Just-Enough-Access (JEA), risk-based adaptive policies, and data protection.

---

## 2. Micro-segmentation and Network Security

In traditional networks, a Flat Network allowed any device to talk to any other device. In ZTA, this is mitigated using **Micro-segmentation**.

Micro-segmentation involves dividing the data center and cloud environments into tiny, isolated segments, down to the individual workload or virtual machine level.

-   **The Benefit**: It explicitly denies east-west (lateral) traffic by default. If a web server is compromised, the attacker cannot pivot from that web server to the database server unless a specific, authorized policy explicitly allows it.
-   **Implementation**: Often achieved using Software-Defined Networking (SDN) and Next-Generation Firewalls (NGFW) to enforce strict, granular firewall rules securely around individual workloads.

---

## 3. Continuous Authentication and Authorization

In traditional systems, logging in once at 9:00 AM granted you a session token valid for the entire day. ZTA requires **Continuous Authentication**.

-   **Contextual Awareness**: ZTA systems constantly monitor the *context* of the request.
    -   *Who* is requesting access? (Identity/MFA)
    -   *What* device are they using? (Is the device registered? Is the OS patched? Is the EDR running?)
    -   *Where* are they located? (Is it a normal IP address? Is it an impossible travel scenario?)
-   If any of these parameters change mid-session (e.g., malware disables the EDR agent on the laptop), the ZTA policy engine immediately revokes access.
-   Access to resources is dynamic and granularly authorized by a Policy Enforcement Point (PEP) rather than statically assigned.

---

## 4. Implementing ZTA in Modern Enterprises

Implementing ZTA is a multi-year journey, not an overnight switch. 

### The CISA Zero Trust Maturity Model
The US Cybersecurity and Infrastructure Security Agency (CISA) outlines five pillars for ZTA maturity:
1.  **Identity**: Transitioning from passwords to phishing-resistant MFA and strong identity providers (IdP).
2.  **Devices**: Tracking all devices (inventories) and enforcing endpoint compliance before granting access.
3.  **Networks**: Encrypting all internal traffic and implementing deep micro-segmentation.
4.  **Applications and Workloads**: Securing the application layer, moving towards continuous integration/continuous deployment (CI/CD) security.
5.  **Data**: Discovering, classifying, and encrypting data at rest and in transit.

---

## 5. Additional Resources

To continue learning about Zero Trust Architecture and its practical implementation, check out these resources:
- **[Hacker Training (hackertraining.org)](https://hackertraining.org)**: Explore the video courses like *AI-Enabled Programming, Networking, and Cybersecurity* for insights into how modern architectures like ZTA integrate with advanced networking concepts.
- **[Hacker Repo (hackerrepo.org)](https://hackerrepo.org)**: Review the defensive security folders, particularly `kubernetes-security` and `cloud-resources`, for practical applications of micro-segmentation principles.

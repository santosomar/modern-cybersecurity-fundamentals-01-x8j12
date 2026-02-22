# Section 02: Introduction to Cryptography

*Estimated time: 75 minutes*

Cryptography is the mathematical foundation that guarantees the Confidentiality, Integrity, and non-repudiation of our data. It is the science of secure communication in the presence of adversarial behavior. Understanding cryptography is necessary to comprehend how data is secured at rest, in transit, and in use.

---

## 1. Encryption Algorithms

Encryption transforms a plaintext message into an unreadable form called ciphertext using a mathematical algorithm and a cryptographic key. The original message can be recovered by an authorized party who possesses a decryption key.

There are two primary categories of encryption:

### Symmetric Cryptography
Symmetric encryption uses a **single shared key** for both encryption and decryption. Both the sender and the receiver must securely exchange and possess the same exact key beforehand. 
- **Pros**: Fast, highly efficient, well-suited for bulk data processing (such as encrypting a full hard drive or a large file).
- **Cons**: The "Key Distribution Problem"—how do you securely send the key to the recipient over an untrusted network? Furthermore, symmetric encryption does not provide non-repudiation because possessing the key proves neither the sender's identity nor the receiver's.
- **Common Algorithms**: 
  - **AES (Advanced Encryption Standard)**: The gold standard for symmetric encryption today. Supports 128-bit, 192-bit, or 256-bit key sizes.
  - **DES / 3DES (Data Encryption Standard)**: Obsolete block ciphers. DES is 56-bit (critically insecure today), and while 3DES improved this, it is slow and deprecated by NIST.
  - **ChaCha20**: A modern, high-speed stream cipher often used on mobile devices when hardware acceleration for AES is unavailable.

### Asymmetric Cryptography (Public Key Cryptography)
Asymmetric encryption solves the Key Distribution Problem by using a **pair of keys**—a Public Key and a mathematically related Private Key. What one key encrypts, *only* the other key can decrypt.
- **The Concept**: The sender obtains the receiver’s Public Key (which is freely distributed) to encrypt the message. The receiver uses their mathematically linked, secret Private Key to decrypt it. 
- **Pros**: Solves key space distribution challenges, provides non-repudiation, and enables digital signatures. 
- **Cons**: Computationally expensive and significantly slower than symmetric encryption. Thus, it is rarely used to encrypt bulk data. 
- **Common Algorithms**: 
  - **RSA (Rivest-Shamir-Adleman)**: One of the oldest and most widely adopted public key algorithms. It relies on the computational difficulty of factoring large prime numbers.
  - **ECC (Elliptic Curve Cryptography)**: Provides equal security to RSA but with significantly smaller key sizes. It relies on the Algebraic structure of elliptic curves over finite fields. Faster and more computationally efficient.

---

## 2. Hashing Algorithms

While encryption guarantees Confidentiality, **Hashing** guarantees **Integrity**. 

A hashing algorithm is a one-way mathematical function that maps data of any arbitrary size to a fixed-size bit string (the hash value, or "digest"). 

### Core Attributes of an Ideal Hash Function:
1. **Deterministic**: The same input will *always* result in the exact same output.
2. **Fixed-Size Output**: Hashing a 10 TB video file and a 10 KB text file using SHA-256 will both result in a 256-bit digest.
3. **Collision Resistance**: It should be computationally infeasible for two different file inputs to evaluate to the exact same hash output. If a collision is found, the hashing algorithm is deemed broken (e.g., MD5).
4. **Avalanche Effect**: Changing a single byte or character in the input will drastically and unpredictably change the output hash.
5. **Irreversible**: You cannot decrypt a hash back into its original text. (Attackers "crack" hashes by guessing strings, hashing them, and comparing the digests, but they do not decrypt them.)

### Common Algorithms:
- **MD5 (Message Digest 5)**: Produces a 128-bit hash. Historically popular but now critically obsolete, broken, and susceptible to collision attacks. 
- **SHA-1 (Secure Hash Algorithm 1)**: Produces a 160-bit hash. Now considered weak and deprecated.
- **SHA-2**: A family of hashes including SHA-224, SHA-256, SHA-384, and SHA-512. The current industry standard for generating secure digests.

---

## 3. Crypto Implementations

In the real world, systems combine multiple cryptographic primitives to achieve all three principles of the CIA Triad. This combination is referred to as a **Cryptosystem**. 

### Digital Certificates and PKI
Symmetric and Asymmetric concepts unite under the **Public Key Infrastructure (PKI)** framework. A digital certificate is a document that cryptographically binds a Public Key to an entity’s identity, digitally signed by a trusted third party called a **Certificate Authority (CA)**.

### TLS/SSL (Transport Layer Security)
TLS is the protocol that secures HTTP traffic into HTTPS. It uses a hybrid approach:
1. The client connects and performs an **Asymmetric Handshake** (using RSA/ECC) to authenticate the server and securely agree upon a shared session key.
2. The remaining communication transitions to **Symmetric Encryption** (using AES) because it is much faster for bulk data transfer.
3. **Hashing** (SHA-256) is applied to individual data packets to ensure Integrity over the transmission.

---

## 4. The Challenges of Post-Quantum Cryptography

Today, asymmetric encryption like RSA and ECC relies on computational difficulties such as prime factorization and discrete logarithms. Traditional supercomputers would take millions of years to break a 2048-bit RSA key.

### The Threat
**Quantum Computing**, processing utilizing the behavior of atomic and subatomic particles, fundamentally changes this equation. Thanks to an algorithm developed by Peter Shor in 1994 (Shor's Algorithm), a sufficiently powerful, fault-tolerant quantum computer could instantly factor the large primes that secure RSA and ECC.

If such a machine is built, the vast majority of our current public-key infrastructure will be instantly broken. Confidential health records, bank transactions, and government secrets currently protected by asymmetric encryption will be universally decipherable. 

### Store Now, Decrypt Later (SNDL)
Adversaries are actively vacuuming up massively encrypted internet traffic today and storing it indefinitely. The goal is to wait until a future date when a Cryptographically Relevant Quantum Computer (CRQC) exists, and then retrospectively crack the decrypted traffic. 

### The Solution: PQC (Post-Quantum Cryptography)
NIST and cryptographic researchers have spearheaded the transition to **Post-Quantum Cryptography**. These are *classical* algorithms designed to run on standard computers, but utilizing mathematical foundations entirely distinct from prime factorization (e.g., Lattice-based cryptography), rendering them immune to Shor's algorithm and quantum attacks.

Transitioning global infrastructure from RSA/ECC to PQC standards is arguably the most significant cryptographic undertaking in history, currently happening precisely right now.

---

## 5. Additional Resources

To see applied cryptography and attack techniques in action, explore the following:
- **[Hacker Training (hackertraining.org)](https://hackertraining.org)**: Deep dive into video courses and O'Reilly books regarding securing systems and deploying practical cybersecurity fundamentals.
- **[Hacker Repo (hackerrepo.org)](https://hackerrepo.org)**: Check the `cheat-sheets` and `certifications` directories for practical cryptographic implementation guides and command references.

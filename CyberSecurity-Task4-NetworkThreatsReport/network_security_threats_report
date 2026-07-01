# Network Security Threats Report

**Author:** Cameron Naidoo  
**Date:** 01 July 2026  
**Track:** Cyber Security  
**Task:** Research Report – Common Network Security Threats  
**Repository:** OIBSIP

---

## 1. Introduction

Network security threats are attacks that target the infrastructure, data, and users of an organisation's network. In today's hyper-connected world, organisations face a constant barrage of attacks—from distributed denial-of-service (DDoS) attacks that take websites offline, to man-in-the-middle (MITM) attacks that intercept sensitive communications. The scale of these threats is staggering: in 2025 alone, Cloudflare mitigated over **47.1 million DDoS attacks**, representing a **121% increase** from 2024 and a **236% increase** from 2023. On average, Cloudflare mitigated **5,376 DDoS attacks every hour** throughout 2025.

This report analyses four common network security threats:
- DoS / DDoS Attacks
- Man-in-the-Middle (MITM) Attacks
- IP Spoofing
- DNS Poisoning / Spoofing

For each threat, the report covers: how it works, a real-world example, its impact, and specific mitigation strategies.

---

## 2. DoS / DDoS Attacks

### 2.1 How It Works

A **Denial-of-Service (DoS)** attack floods a target system with traffic, overwhelming its resources and making it unavailable to legitimate users. A **Distributed Denial-of-Service (DDoS)** attack uses a botnet—a network of compromised computers—to launch the attack from multiple sources simultaneously, making it much harder to block.

Attackers commonly use **reflection and amplification** techniques, where they spoof the victim's IP address and send requests to vulnerable servers (e.g., DNS, NTP, Memcached). These servers then send large responses to the victim, amplifying the traffic volume significantly.

### 2.2 Real-World Example: The Largest DDoS Attack Ever Recorded

In late December 2025, the telecommunications sector was targeted by the largest Distributed Denial of Service (DDoS) attack ever seen. The attack, launched by the **Aisuru botnet** (also known as Kimwolf), peaked at **31.4 Terabits per second (Tbps)** —shattering all previous records. The attack was part of a campaign referred to as the "Night before Christmas" campaign. Cloudflare mitigated the attack without major disruption.

| Metric | Value |
| :--- | :--- |
| **Peak Attack Size** | 31.4 Tbps |
| **Botnet Name** | Aisuru / Kimwolf |
| **Target Sector** | Telecommunications |
| **Date** | December 2025 |
| **Mitigated By** | Cloudflare |
| **Attack Magnitude Growth** | Attack sizes grew more than **700%** compared to large-scale attacks observed in late 2024 |

**Why This Matters:** This attack demonstrates that DDoS attacks are not only becoming more frequent but exponentially larger. Organisations that do not have DDoS protection in place could be completely overwhelmed by such an attack.

### 2.3 Impact

| Impact | Description |
| :--- | :--- |
| **Revenue Loss** | Website downtime directly translates to lost sales. |
| **Reputational Damage** | Customers lose trust in organisations that cannot stay online. |
| **Operational Disruption** | Internal systems become unavailable, halting business operations. |
| **Increased Costs** | Mitigation services, incident response, and recovery are expensive. |

### 2.4 3 Specific Mitigation Strategies

| # | Strategy | Description |
| :--- | :--- | :--- |
| **1** | **Rate Limiting** | Restrict the number of requests a single IP address can make in a given time period. This prevents a single compromised machine from overwhelming the system. |
| **2** | **DDoS Protection Services** | Use cloud-based services like Cloudflare, AWS Shield, or Akamai to absorb and filter attack traffic before it reaches your network. These services have the bandwidth and expertise to handle hyper-volumetric attacks like the 31.4 Tbps incident. |
| **3** | **Web Application Firewall (WAF)** | Deploy a WAF to detect and block malicious traffic patterns associated with DDoS attacks. WAFs can identify and block application-layer (Layer 7) attacks that target specific vulnerabilities. |

---

## 3. Man-in-the-Middle (MITM) Attacks

### 3.1 How It Works

A **Man-in-the-Middle (MITM)** attack occurs when an attacker intercepts communications between two parties (e.g., a user and a website) without their knowledge. The attacker can eavesdrop, steal sensitive data, or manipulate the communication. Common methods include **ARP spoofing**, **DNS spoofing**, **rogue Wi-Fi access points**, and **compromised root certificates**.

When TLS is compromised via a rogue root certificate, the browser happily connects to an attacker-controlled endpoint, making the attack virtually invisible to the user.

### 3.2 Real-World Example: Secret Blizzard MITM Attacks (2025)

In early 2025, Russian state-backed threat group **Secret Blizzard** targeted foreign embassies with a sophisticated man-in-the-middle (MITM) attack that bypassed Multi-Factor Authentication (MFA).

| Aspect | Details |
| :--- | :--- |
| **Threat Group** | Secret Blizzard (Russian state-backed) |
| **Date** | Early 2025 |
| **Targets** | Foreign embassies |
| **Method** | Rogue root certificate compromise, TLS interception |
| **Key Finding** | Bypassed MFA by intercepting the authentication flow |

**Why This Matters:** The Secret Blizzard attack demonstrates that MFA alone is not sufficient if the underlying TLS connection is compromised. When a root certificate is compromised, the attacker can intercept and manipulate communications, including MFA tokens. This highlights the importance of **certificate management** and **hardware-based authentication** (such as FIDO2/WebAuthn) that is resistant to MITM attacks.

### 3.3 Impact

| Impact | Description |
| :--- | :--- |
| **Theft of Credentials** | Attackers capture usernames, passwords, and MFA tokens. |
| **Financial Data Theft** | Credit card numbers, bank details, and payment information are intercepted. |
| **Data Manipulation** | Attackers can modify communications, injecting malware or redirecting users to malicious sites. |
| **Complete Loss of Confidentiality** | All communications between the user and the server are exposed. |

### 3.4 3 Specific Mitigation Strategies

| # | Strategy | Description |
| :--- | :--- | :--- |
| **1** | **Encryption in Transit (TLS 1.2+)** | Enforce HTTPS for all web traffic. This encrypts data, preventing attackers from reading it even if they intercept it. Ensure certificates are properly validated and not using weak ciphers. |
| **2** | **Certificate Pinning** | Hardcode the expected SSL certificate in applications to prevent attackers from using fraudulent certificates. This prevents rogue root certificate attacks like Secret Blizzard. |
| **3** | **FIDO2 / WebAuthn (Hardware Tokens)** | Use hardware-based authentication that is resistant to MITM attacks. Unlike SMS or TOTP codes, FIDO2 credentials are bound to the specific website origin and cannot be intercepted or replayed. |

---

## 4. IP Spoofing

### 4.1 How It Works

**IP spoofing** involves creating IP packets with a forged source IP address. The attacker disguises the true source of the traffic, often to bypass firewall rules or impersonate a trusted system. IP spoofing is commonly used in **DDoS reflection/amplification attacks** and to bypass IP-based authentication.

In a TCP SYN-ACK reflection attack, the attacker sends a spoofed SYN packet with the victim's IP address as the source, to a wide range of random or pre-selected reflection IP addresses. The reflection servers then send SYN-ACK responses to the victim, overwhelming their network.

### 4.2 Real-World Example: The Spamhaus DDoS Attack (2013)

While older, the 2013 Spamhaus attack remains one of the most documented examples of IP spoofing combined with DNS reflection and amplification.

| Aspect | Details |
| :--- | :--- |
| **Attack Type** | DNS reflection/amplification DDoS |
| **Techniques Used** | IP spoofing, reflection, amplification |
| **Target** | Spamhaus (anti-spam organisation) |
| **Scale** | Peaked at 300+ Gbps (massive for its time) |
| **Method** | Attackers spoofed Spamhaus's IP address and sent DNS queries to thousands of open DNS resolvers, which then sent large responses to Spamhaus |

**Why This Matters:** The Spamhaus attack demonstrated how IP spoofing, when combined with reflection and amplification, can turn a small request into a massive flood of traffic directed at the victim. This technique remains one of the most common DDoS vectors today.

### 4.3 Impact

| Impact | Description |
| :--- | :--- |
| **Bypassing IP-Based Security** | Attackers impersonate trusted systems to gain unauthorised access. |
| **Launching Reflection/Amplification DDoS** | Spoofed IP addresses are used to direct massive traffic floods at victims. |
| **Impersonation** | Attackers can pretend to be internal or trusted systems. |

### 4.4 3 Specific Mitigation Strategies

| # | Strategy | Description |
| :--- | :--- | :--- |
| **1** | **Ingress Filtering (BCP 38)** | Configure routers to drop packets with source IP addresses that do not belong to the internal network. This is defined in RFC 2827 / BCP 38 and is one of the most effective defences against IP spoofing. |
| **2** | **Egress Filtering** | Block outgoing packets that have source IP addresses outside the organisation's allocated range. This prevents internal systems from being used in spoofing attacks. |
| **3** | **Do Not Rely on IP Addresses for Authentication** | Use certificate-based or token-based authentication instead of IP-based whitelisting. IP addresses can be easily spoofed, making them an unreliable authentication mechanism. |

---

## 5. DNS Poisoning / Spoofing

### 5.1 How It Works

**DNS poisoning** (also called DNS spoofing or cache poisoning) involves corrupting the DNS cache of a resolver, causing it to return an incorrect IP address for a domain name. The attacker redirects users to malicious websites—often phishing pages or malware distribution sites—without the user's knowledge.

The Kaminsky vulnerability (2008) was a critical flaw in DNS implementations that allowed attackers to inject malicious DNS records into the cache of a target nameserver. Without the patch, the vulnerability could be exploited in as little as **10 seconds**.

### 5.2 Real-World Example: StormBamboo ISP DNS Poisoning (2024)

In 2024, the China-aligned threat group **StormBamboo** (aka Evasive Panda, Daggerfly, StormCloud) compromised an Internet Service Provider (ISP) and used its foothold to launch DNS poisoning attacks against selected customers.

| Aspect | Details |
| :--- | :--- |
| **Threat Group** | StormBamboo (China-aligned) |
| **Date** | 2024 |
| **Target** | ISP customers |
| **Method** | Compromised the ISP's infrastructure to poison DNS responses |
| **Outcome** | Malware delivered to Windows and Mac users via tampered software updates |
| **Mitigation** | DNS poisoning immediately stopped when the ISP rebooted and took various components of the network offline |

**Why This Matters:** The StormBamboo attack demonstrates that DNS poisoning can be used to deliver malware to users even when they use trusted DNS providers like Google and Cloudflare. This highlights the importance of securing the entire DNS resolution chain, not just the endpoint.

### 5.3 Impact

| Impact | Description |
| :--- | :--- |
| **Redirecting Users** | Users are sent to malicious websites instead of legitimate ones. |
| **Credential Theft** | Users enter credentials on fake login pages (phishing). |
| **Malware Distribution** | Attackers use poisoned DNS to redirect users to malware download sites. |
| **Supply Chain Attacks** | Poisoned DNS can be used to tamper with software updates, as seen in the StormBamboo attack. |

### 5.4 3 Specific Mitigation Strategies

| # | Strategy | Description |
| :--- | :--- | :--- |
| **1** | **DNSSEC (DNS Security Extensions)** | Digitally sign DNS records to prevent tampering. This ensures that resolvers can verify the authenticity of DNS responses. DNSSEC establishes a chain of trust from the root zone, providing cryptographic integrity to DNS data. |
| **2** | **DNS over HTTPS (DoH) / DNS over TLS (DoT)** | Encrypt DNS queries to prevent eavesdropping and manipulation. Currently, only 46% of public resolver operators have enabled encrypted DNS transport, indicating significant room for improvement. |
| **3** | **DNS Cache Validation & Randomisation** | Configure resolvers to validate responses and randomise source ports and query IDs. This prevents Kaminsky-style poisoning attacks where attackers guess the transaction ID to inject forged records. The recent BIND 9 vulnerability (CVE-2025-40778, CVSS 8.6) highlights that DNS software vulnerabilities remain a significant risk. |

---

## 6. Comparison Table

| Threat | Attack Vector | Who Is at Risk | Difficulty to Execute | Ease of Mitigation |
| :--- | :--- | :--- | :--- | :--- |
| **DoS/DDoS** | Network traffic flooding | Any organisation with a public-facing service | Medium (requires botnet resources) | Medium (DDoS protection services available) |
| **MITM** | Network interception / certificate compromise | Users on unencrypted networks or with compromised trust stores | Medium-Hard (requires network access or certificate compromise) | Easy-Medium (enforce HTTPS, use FIDO2) |
| **IP Spoofing** | Forged IP packets | Networks without ingress filtering | Hard (requires deep network knowledge) | Easy (implement BCP 38) |
| **DNS Poisoning** | DNS cache corruption | Any organisation using DNS | Hard (requires sophisticated knowledge) | Medium (DNSSEC implementation is complex) |

---

## 7. Conclusion: 3 Key Takeaways for a Network Administrator

1. **Encrypt everything, everywhere.** Ensure all data in transit is encrypted using TLS 1.2+ (HTTPS). This protects against MITM attacks and eavesdropping. For DNS, adopt DNSSEC and encrypted DNS (DoH/DoT) to prevent DNS poisoning.

2. **Filter traffic at the network edge.** Implement ingress and egress filtering (BCP 38) to prevent IP spoofing and limit the impact of DDoS reflection attacks. This simple measure is one of the most effective defences against spoofing-based attacks.

3. **Assume you will be attacked.** The 47.1 million DDoS attacks in 2025 demonstrate that attacks are inevitable. Invest in DDoS protection services (Cloudflare, AWS Shield), maintain robust patch management (especially for DNS servers), and implement zero-trust principles (FIDO2 hardware tokens) that are resistant to MITM attacks.

---

## 8. References

1. Cloudflare. (2026). *DDoS Threat Report – 2025 Year in Review*. Cloudflare Radar. Available at: blog.cloudflare.com

2. HEAL Security. (2026). *31.4 Tbps DDoS Attack Via Aisuru Botnet Breaks Internet With New World Record*. Available at: healsecurity.com

3. BleepingComputer. (2026). *Aisuru botnet sets new record with 31.4 Tbps DDoS attack*. Available at: www.bleepingcomputer.com

4. The Hacker News. (2025). *Russian Hackers: Secret Blizzard MITM Attack*. Available at: thehackernews.com

5. MITRE ATT&CK. *Technique T1498.002: Reflection Amplification DoS*. Available at: attack.mitre.org

6. Volexity. (2024). *StormBamboo DNS Poisoning Attack Analysis*. Available at: volexity.com

7. CISA. (2025). *BIND 9 DNS Cache Poisoning Vulnerability (CVE-2025-40778)*. Available at: cisa.gov

8. Kaminsky, D. (2008). *DNS Cache Poisoning Vulnerability Disclosure*. Available at: darkreading.com

---

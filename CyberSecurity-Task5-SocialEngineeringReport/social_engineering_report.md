# Social Engineering Attacks – Research Report

**Author:** Cameron Naidoo  
**Date:** 01 July 2026  
**Version:** 1.0  
**Track:** Cyber Security  
**Task:** Research Report – Social Engineering Attacks  
**Repository:** OIBSIP

---

## 1. Introduction

Social engineering is the psychological manipulation of people to perform actions or divulge confidential information. Unlike technical attacks that exploit software vulnerabilities, social engineering targets the human element—the most vulnerable component of any security system. Attackers exploit trust, fear, urgency, and authority to bypass technical controls.

**Why It Is One of the Most Effective Attack Vectors:**

- **Human Error:** Employees are not perfect. Fatigue, distraction, and lack of awareness lead to mistakes.
- **Technical Defenses Are Bypassed:** Firewalls and antivirus cannot stop an employee from willingly giving away their password.
- **Scale:** A single successful phishing email can compromise an entire organisation.
- **Statistics:** The 2024 Verizon Data Breach Investigations Report found that **68% of data breaches involved a non-malicious human element** (e.g., falling for a phishing email). The average cost of a successful social engineering attack was estimated at **$4.88 million**.

This report analyses four common social engineering attack types: Phishing, Pretexting, Baiting, and Quid Pro Quo. For each, it covers how the attack works, real-world examples, and specific prevention measures.

---

## 2. Phishing

### 2.1 How It Works

Phishing is a fraudulent attempt to obtain sensitive information (usernames, passwords, credit card details) by disguising as a trustworthy entity in electronic communication. Attackers send emails, text messages, or phone calls that appear to come from legitimate sources (e.g., banks, IT support, government agencies). The message creates urgency ("Your account will be suspended") to pressure the victim into clicking a malicious link or providing credentials.

### 2.2 Types of Phishing

| Type | Description | Target |
| :--- | :--- | :--- |
| **Spear Phishing** | Targeted phishing aimed at a specific individual or organisation. Attackers research the victim to personalise the message. | Specific employees or executives. |
| **Whaling** | Spear phishing targeting high-level executives (CEOs, CFOs). | C-suite executives. |
| **Vishing** | Voice phishing – attackers call victims pretending to be from IT support or a bank. | All employees, often targeting older individuals. |
| **Smishing** | SMS phishing – attackers send fraudulent text messages with malicious links. | All mobile users. |

### 2.3 Real-World Case Study: RSA SecurID Breach (2011)

The 2011 RSA SecurID breach is one of the most well-known spear-phishing attacks. Attackers sent a targeted email to a small group of RSA employees with an Excel spreadsheet attachment containing a zero-day Flash exploit. The email was crafted to appear legitimate, and an employee opened the attachment, which installed a backdoor on their system. This allowed the attackers to exfiltrate sensitive information about RSA's two-factor authentication tokens, leading to a massive security breach affecting thousands of RSA's customers. The breach cost RSA approximately **$66 million** in remediation costs.

**Why It Worked:**
- The email was highly targeted and appeared authentic.
- The attachment exploited an unpatched vulnerability (zero-day).
- The employee was not trained to recognise the subtle signs of a spear-phishing email.

### 2.4 4 Prevention Recommendations

| # | Recommendation | Description |
| :--- | :--- | :--- |
| **1** | **Security Awareness Training** | Conduct regular, mandatory training on how to identify phishing emails (check sender address, hover over links, look for urgency). |
| **2** | **Email Filtering & Anti-Spoofing** | Implement DMARC, SPF, and DKIM to prevent spoofing. Use email security gateways to filter suspicious emails. |
| **3** | **Multi-Factor Authentication (MFA)** | Even if credentials are phished, MFA blocks the attacker from using them. |
| **4** | **Simulated Phishing Tests** | Regularly send simulated phishing emails to employees to test their awareness and provide immediate feedback. |

---

## 3. Pretexting

### 3.1 How It Works

Pretexting involves an attacker creating a fabricated scenario (a "pretext") to trick a victim into providing information or performing an action. Unlike phishing, which often relies on urgency, pretexting relies on **trust and authority**. The attacker impersonates a person of authority (e.g., IT support, a senior executive, a vendor) and builds a convincing story over multiple interactions.

### 3.2 How an Attacker Builds a False Scenario

1. **Research:** The attacker gathers information about the target (social media, company websites, public records).
2. **Impersonation:** The attacker poses as a trusted figure (e.g., IT support, a bank representative, a government official).
3. **Building Rapport:** The attacker engages the victim in conversation, establishing trust and credibility.
4. **The Ask:** The attacker requests sensitive information (e.g., passwords, employee IDs, financial data) or actions (e.g., transferring funds).

### 3.3 Real-World Case Study: 2008 Bank Data Theft

An attacker impersonated a representative of a credit reporting agency and contacted a bank employee. Using publicly available information, the attacker established a convincing pretext and convinced the employee to provide access to sensitive customer data. The breach resulted in the theft of personal information of thousands of customers.

**Why It Worked:**
- The attacker built trust over multiple phone calls.
- The employee was not trained to verify the identity of callers.
- The attacker appeared knowledgeable about the bank's internal processes.

### 3.4 3 Prevention Measures

| # | Measure | Description |
| :--- | :--- | :--- |
| **1** | **Verification Protocols** | Implement a "call-back" policy for sensitive requests. Employees should verify the identity of the requester using a known, trusted phone number (not the one provided by the caller). |
| **2** | **Access Control** | Enforce least privilege—employees should only have access to data necessary for their role. |
| **3** | **Training** | Train employees to recognise and report suspicious requests, even if they appear to come from senior executives. |

---

## 4. Baiting

### 4.1 How It Works

Baiting involves offering a desirable item (digital or physical) to trick a victim into performing an action that compromises their security. The attacker leverages human curiosity or greed.

**Digital Baiting:**
- Attackers post a link promising a free download (e.g., a cracked version of a paid software, free movie downloads). The download contains malware.

**Physical Baiting:**
- An attacker drops infected USB drives in the target's parking lot, cafeteria, or entrance. The drives are labelled with enticing phrases like "Confidential" or "Employee Salaries." A curious employee picks it up and plugs it into their work computer, unknowingly installing malware.

### 4.2 Real-World Case Study: US Government USB Attack (2008)

In 2008, a sophisticated cyber-espionage group placed infected USB drives in the parking lot of a US military base. An employee picked up the drive and plugged it into a computer on a classified network. The USB drive contained malware that created a backdoor, allowing attackers to exfiltrate sensitive military data for months undetected.

**Why It Worked:**
- The attack exploited human curiosity and lack of security awareness.
- The USB drive was physically attractive (labelled "Confidential").
- The employee bypassed security policies by plugging an untrusted device into a classified system.

### 4.3 3 Prevention Measures

| # | Measure | Description |
| :--- | :--- | :--- |
| **1** | **USB Blocking** | Block access to USB storage devices on corporate workstations using endpoint security policies. |
| **2** | **Security Awareness** | Train employees to never plug untrusted devices into company systems. |
| **3** | **Physical Security** | Clear labelling and physical security can reduce the chances of devices being dropped in sensitive areas. |

---

## 5. Quid Pro Quo

### 5.1 How It Works

Quid pro quo is a type of social engineering where the attacker offers a service or benefit in exchange for information or access. The most common example is an attacker posing as IT support, offering to help with a technical issue in exchange for the victim's password or MFA token.

### 5.2 How It Works

1. The attacker identifies employees through social media or company directories.
2. The attacker calls the employee, claiming to be from IT support.
3. The attacker says they are "testing" or "fixing" an issue and asks the employee to provide their password or MFA code to verify their identity.
4. The victim provides the information, and the attacker gains access.

### 5.3 Prevention

| # | Measure | Description |
| :--- | :--- | :--- |
| **1** | **Strict IT Policy** | IT support should never ask for passwords over the phone. Employees should be trained to report such requests. |
| **2** | **Verification** | Employees should verify the caller's identity by calling the IT helpdesk directly using a known number. |
| **3** | **MFA** | Require MFA for all access—even if an attacker obtains a password, they cannot access without the second factor. |

---

## 6. Comparison Table

| Attack Type | Primary Target | Psychological Lever Exploited | Best Countermeasure |
| :--- | :--- | :--- | :--- |
| **Phishing** | All employees | Urgency, Fear, Authority | Security awareness training, email filtering, MFA |
| **Pretexting** | Employees with access to sensitive data | Trust, Authority | Verification protocols, access control |
| **Baiting** | General public or employees | Curiosity, Greed | USB blocking, security awareness training |
| **Quid Pro Quo** | Employees expecting technical support | Reciprocity, Trust | Strict IT policies, verification |

---

## 7. Organisational Recommendations: 5-Point Employee Security Awareness Training Checklist

| # | Recommendation | Why It Matters |
| :--- | :--- | :--- |
| **1** | **Recognise Red Flags** | Train employees to check sender addresses, hover over links, and watch for urgent or unusual requests. |
| **2** | **Don't Share Credentials** | Emphasise that passwords and MFA codes should never be shared with anyone, even if they claim to be IT support. |
| **3** | **Verify Identities** | Implement a "call-back" or "confirm with manager" policy for sensitive requests. |
| **4** | **Report Suspicious Activity** | Create a clear, non-punitive reporting process. Employees should feel safe reporting mistakes. |
| **5** | **Regular Simulated Tests** | Conduct regular phishing simulations and social engineering tests to measure and improve employee awareness. |

---

## 8. Conclusion

Social engineering attacks exploit the most unpredictable element in any organisation: **the human**. While technical defenses (firewalls, antivirus, MFA) are essential, they are insufficient without a well-trained workforce that can recognise and resist manipulation.

**Three Key Takeaways for Organisations:**

1. **Human error is the #1 attack vector.** Invest in regular, engaging security awareness training—not just a one-time annual session.
2. **Don't rely on technology alone.** Attackers bypass firewalls by targeting people. MFA and email filters are great, but they are not silver bullets.
3. **Create a culture of security.** Employees should feel empowered to question suspicious requests and report mistakes without fear of punishment.

---

## 9. References

1. Verizon. (2024). *Verizon Data Breach Investigations Report (DBIR)*.
2. SANS Institute. *Social Engineering: The Human Element in Cybersecurity*. Available at: sans.org/reading-room.
3. CISA. *Social Engineering and Phishing Guide*. Available at: cisa.gov.
4. Krebs on Security. (2011). *RSA SecurID Breach: The Inside Story*.
5. RSA. (2011). *RSA SecurID Breach Announcement*.
6. Dark Reading. (2008). *USB Attack on US Military Base*.

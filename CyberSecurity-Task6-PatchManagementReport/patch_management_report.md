# The Importance of Patch Management

**Author:** Cameron Naidoo  
**Date:** 01 July 2026  
**Version:** 1.0  
**Track:** Cyber Security  
**Task:** Research Report – The Importance of Patch Management  
**Repository:** OIBSIP

---

## 1. Introduction

Patch management is the process of identifying, acquiring, testing, and deploying software updates (patches) to fix vulnerabilities, improve functionality, or address performance issues. In cybersecurity, patch management is one of the most critical yet frequently neglected controls. Unpatched systems represent one of the largest attack surfaces in any organisation, as attackers actively scan for known vulnerabilities that have public exploits available.

The 2023 Verizon Data Breach Investigations Report found that **exploitation of unpatched vulnerabilities** remains one of the top attack vectors used by cybercriminals. NIST has recognised this threat, noting that patch management is "not a routine IT task but a critical component of national cybersecurity defense" (NIST SP 800-40 Rev. 4).

This report covers:
- Why patches matter and the vulnerability lifecycle.
- Two real-world breaches caused by unpatched systems (WannaCry and Equifax).
- The consequences of not patching.
- The patch management lifecycle (5 phases).
- 7 best practices for effective patch management.
- Common challenges and how to overcome them.

---

## 2. Why Patches Matter: The Vulnerability Lifecycle

### 2.1 How Vulnerabilities Are Discovered and Reported

The vulnerability lifecycle follows a predictable pattern:

| Phase | Description |
| :--- | :--- |
| **Discovery** | A security researcher, vendor, or attacker identifies a flaw in software. |
| **Disclosure** | The vulnerability is reported to the vendor (responsible disclosure) or made public (full disclosure). |
| **CVE Assignment** | A **Common Vulnerabilities and Exposures (CVE)** identifier is assigned (e.g., CVE-2017-5638 for the Apache Struts vulnerability that led to Equifax). |
| **CVSS Scoring** | The vulnerability is scored using the **Common Vulnerability Scoring System (CVSS)**, producing a severity score from 0 to 10. Scores of 7.0+ are considered High or Critical. |
| **Patch Development** | The vendor develops and releases a patch. |
| **Exploitation Window** | The period between patch release and deployment—this is when attackers are most active, as they reverse-engineer the patch to build exploits. |

### 2.2 The Exploitation Window

The time between a patch being released and an organisation deploying it is the **window of opportunity** for attackers. When a vendor releases a patch, it reduces the window of opportunity for attackers. If the window is too wide (i.e., the patch is not applied quickly), the organisation remains vulnerable to attacks that exploit the same flaw.

The exploitation window is typically the most dangerous phase because attackers know that many organisations are slow to patch. Tools like Shodan and Censys allow attackers to scan the internet for vulnerable systems in minutes.

---

## 3. Real-World Breaches Caused by Unpatched Systems

### 3.1 WannaCry Ransomware (2017)

WannaCry remains one of the most devastating ransomware attacks in history, and it was entirely preventable.

| Aspect | Details |
| :--- | :--- |
| **Vulnerability** | EternalBlue (MS17-010) – a flaw in Microsoft's SMB protocol |
| **Patch Release Date** | March 2017 |
| **Attack Date** | May 2017 |
| **Infection Count** | 300,000+ systems across 150 countries |
| **Impact** | Disrupted critical operations globally, including the UK's National Health Service (NHS) |
| **Root Cause** | Although the patch had been available for two months, most organisations—including many NHS trusts—had not applied it |

**Why It Happened:**

- NHS Digital did not have the authority to enforce patching across all NHS trusts.
- Many systems were running outdated, unsupported operating systems (Windows XP, Windows 7).
- Organisations lacked clear patch management processes and accountability.
- Ineffective risk communication to senior management.

**Key Takeaway:** This is a classic example of organisational failure, not technical failure. The patch existed, but the process to deploy it was broken.

### 3.2 Equifax Data Breach (2017)

The Equifax breach exposed the personal data of 147 million people and remains one of the most costly data breaches in history.

| Aspect | Details |
| :--- | :--- |
| **Vulnerability** | Apache Struts CVE-2017-5638 – a remote code execution flaw |
| **Patch Release Date** | March 2017 |
| **Attack Date** | May–July 2017 |
| **Data Exposed** | Names, Social Security numbers, addresses, and credit card details of 147 million people |
| **Financial Impact** | Settlement of up to $700 million |

**Root Cause:**

- Equifax failed to apply a patch that had been available for months.
- An internal notification was sent to IT personnel on March 9, but the vulnerable version was not identified or patched.
- Security scans conducted on March 15 also failed to flag the vulnerable implementation.

**Systemic Failures Identified:**

- **Patch Management Failure:** The patch was not applied despite the notification.
- **Vulnerability Scanning Failure:** The scans missed the vulnerable component.
- **Asset Inventory Failure:** Equifax did not know which systems were running Apache Struts.
- **Incident Detection Failure:** The breach went undetected for over two months.

---

## 4. Consequences of Not Patching

| Consequence | Description |
| :--- | :--- |
| **Data Breaches** | Attackers exploit known vulnerabilities to steal sensitive data (as seen in Equifax). |
| **Ransomware Attacks** | Unpatched systems are prime targets for ransomware (as seen in WannaCry). |
| **Compliance Violations** | Frameworks like PCI DSS, HIPAA, and GDPR require timely patching of critical vulnerabilities. Failure to patch can result in regulatory fines. |
| **Financial Penalties** | Direct costs of breaches, legal fees, regulatory fines, and loss of customer trust. |
| **Operational Disruption** | Downtime from ransomware or system outages can halt business operations for days or weeks. |
| **Reputational Damage** | Loss of customer trust can have long-term revenue impacts beyond the immediate breach. |

---

## 5. The Patch Management Lifecycle

Effective patch management follows a structured, repeatable lifecycle. NIST Special Publication 800-40 Rev. 4 provides the definitive framework for enterprise patch management.

| Phase | Description | Key Activities |
| :--- | :--- | :--- |
| **1. Discovery** | Identify which assets exist and what software versions they are running. | Maintain an up-to-date asset inventory. Use vulnerability scanners (e.g., Nessus, OpenVAS) to identify missing patches. |
| **2. Assessment** | Determine which patches are applicable and prioritise them. | Review CVSS scores. Prioritise Critical and High severity patches (CVSS 7.0+). Consider exploit availability and asset criticality. |
| **3. Testing** | Validate patches in a non-production environment before deployment. | Deploy patches to a test environment that mirrors production. Verify that patches do not break functionality. Document test results. |
| **4. Deployment** | Roll out patches to production systems. | Use phased deployments: deploy to a small subset first ("canary" assets). Monitor for issues before full rollout. Schedule deployments during maintenance windows. |
| **5. Verification** | Confirm that patches were successfully applied. | Use scanning tools to verify patch status. Document successful deployments. Update asset inventory records. |

**NIST SP 800-40r4 emphasises:** proactive patch management and risk assessment, along with automation to efficiently address software vulnerabilities.

---

## 6. Patch Management Best Practices: 7-Step Checklist

| # | Best Practice | Why It Matters |
| :--- | :--- | :--- |
| **1** | **Maintain a Complete Asset Inventory** | You cannot patch what you do not know exists. Every system, application, and network device must be catalogued. |
| **2** | **Prioritise by Risk, Not by Date** | Use CVSS scores and exploit intelligence. A Critical vulnerability in an internet-facing system must be patched before a High vulnerability in an internal system. |
| **3** | **Test Patches Before Deployment** | Patches can cause system instability or break functionality. Testing prevents unplanned downtime. |
| **4** | **Adopt Phased Rollouts** | Deploy to a small subset first ("canary" assets). Monitor for issues before full deployment. |
| **5** | **Automate Where Possible** | Use patch management tools (e.g., WSUS, SCCM, Qualys, ManageEngine) to automate discovery, deployment, and reporting. |
| **6** | **Establish Clear SLAs** | Define patching timelines: Critical = 24–48 hours, High = 7 days, Medium = 30 days, Low = 90 days. |
| **7** | **Document and Report** | Track patch status, successful deployments, and exceptions. Report to management regularly to ensure accountability. |

---

## 7. Challenges in Patch Management and How to Overcome Them

| Challenge | Why It Happens | How to Overcome |
| :--- | :--- | :--- |
| **Legacy Systems** | Older systems may not support modern patches or vendors may have ended support. | Isolate legacy systems with compensating controls (e.g., network segmentation, strict access controls). Plan for system replacement. |
| **Downtime Concerns** | Patching often requires reboots or system outages. | Schedule patches during maintenance windows. Use high-availability configurations to minimise downtime. |
| **Testing Requirements** | Testing takes time and resources. | Build a dedicated test environment that mirrors production. Use automated testing tools. |
| **Lack of Visibility** | Organisations do not know what they have (poor asset inventory). | Implement continuous asset discovery. Use vulnerability scanners to identify missing patches. |
| **No Executive Buy-in** | Patching is seen as an IT cost, not a business priority. | Translate patching into business risk: "Unpatched systems increase the likelihood of a breach costing $X million." |
| **Patch Volatility** | The number of patches released monthly can be overwhelming. | Prioritise using CVSS scores and exploit intelligence. Focus on Critical and High vulnerabilities first. |
| **Manual Processes** | Manual patching is slow and error-prone. | Automate with patch management tools. Integrate with vulnerability management for continuous monitoring. |

---

## 8. Conclusion

Patch management is not merely a technical activity—it is a **business-critical risk management function**. The Equifax and WannaCry incidents demonstrate that the failure to apply timely patches can result in catastrophic financial, operational, and reputational damage. Organisations must treat patch management as a strategic priority, with clear accountability, defined SLAs, and continuous oversight by senior leadership.

**Three Key Takeaways for Organisations:**

1. **Treat patch management as a risk management function.** It is not just about IT—it protects the business, its customers, and its reputation.
2. **Automate and prioritise.** Use tools to discover and deploy patches, and prioritise based on CVSS scores and exploit intelligence.
3. **Test before deployment.** Untested patches can cause outages that are as damaging as the attacks they prevent.

---

## 9. References

1. NIST. (2022). *Guide to Enterprise Patch Management Planning: Preventive Maintenance for Technology*. NIST Special Publication 800-40 Revision 4.
2. NIST. (2025). *Security and Privacy Control Catalog*. NIST SP 800-53 Revision 5.2.0.
3. CISA. *Understanding and Mitigating Russian State-Sponsored Cyber Threats*. Available at: cisa.gov.
4. MITRE Corporation. *CVE List* – Common Vulnerabilities and Exposures database.
5. FIRST. *Common Vulnerability Scoring System (CVSS) v3.0* – Standard for vulnerability severity scoring.
6. Qualys. (2017). *WannaCry Ransomware Analysis* – Remediation activity directly related to risk levels.
7. U.S. Government Equifax Settlement. *Equifax Data Breach Settlement* – $700 million settlement.
8. ISACA. *Patch Management Failures and the EternalBlue Exploit*.

---

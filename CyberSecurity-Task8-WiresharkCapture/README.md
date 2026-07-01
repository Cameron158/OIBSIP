# Task 8: Capture Network Traffic with Wireshark

**Author:** Cameron Naidoo  
**Date:** 01 July 2026  
**Track:** Cyber Security  
**Task:** Capture Network Traffic with Wireshark  
**Repository:** OIBSIP

---

## Overview

This task involved capturing live network traffic using Wireshark, applying display filters to isolate specific protocols, and analyzing packet contents to understand network communication and identify security risks. The goal was to demonstrate practical skills in network traffic analysis and security assessment.

---

## Lab Environment

| Component | Details |
| :--- | :--- |
| **Operating System** | Kali Linux (Virtual Machine) |
| **Network Interface** | eth0 (Host-Only Adapter) |
| **Capture Duration** | ~2 minutes |
| **Capture File** | `wireshark_capture.pcap` |
| **Traffic Generated** | HTTP, DNS, ICMP (ping) |

---

## Screenshots

| Screenshot | Description |
| :--- | :--- |
| `http_filter.png` | HTTP traffic filtered in Wireshark |
| `dns_filter.png` | DNS traffic filtered in Wireshark |
| `tcp_handshake.png` | TCP Three-Way Handshake (SYN, SYN-ACK, ACK) – annotated |
| `unencrypted_http.png` | Unencrypted HTTP GET request showing plain-text data |

---

## Analysis

### 1. HTTP Traffic (`http` filter)

**Screenshot:** `http_filter.png`

**Observation:**
- Filtering by `http` displayed all unencrypted HTTP requests and responses.
- A `GET` request to `neverssl.com` was observed.
- In the `Hypertext Transfer Protocol` section, the `Request Method`, `Request URI`, and `Host` fields were visible in plain text.

**Security Risk:**
HTTP traffic is unencrypted. Any data sent via HTTP — including URLs, headers, and cookies — can be intercepted and read by anyone on the same network (e.g., public Wi-Fi). This makes HTTP unsuitable for transmitting sensitive information like passwords or personal data.

**Mitigation:**
Always use HTTPS (HTTP over TLS/SSL) to encrypt web traffic and protect data in transit.

---

### 2. DNS Traffic (`dns` filter)

**Screenshot:** `dns_filter.png`

**Observation:**
- Filtering by `dns` displayed DNS queries and responses.
- A DNS query for `www.google.com` was observed.
- The `Domain Name System` section showed the `Query Name` and the `Response IP` address.

**Security Risk:**
Most DNS queries are transmitted in plain text. This means a third party can see which websites a user is visiting. This exposes browsing habits and can reveal sensitive search queries.

**Mitigation:**
Use DNS over HTTPS (DoH) or DNS over TLS (DoT) to encrypt DNS queries and protect user privacy.

---

### 3. TCP Three-Way Handshake (`tcp` filter)

**Screenshot:** `tcp_handshake.png` (annotated)

**Observation:**
- Filtering by `tcp` displayed all TCP traffic.
- A complete three-way handshake was identified:

| Packet | Direction | Flag | Sequence Number | Acknowledgment Number |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Client → Server | SYN | 0 (relative) | N/A |
| 2 | Server → Client | SYN-ACK | 0 (relative) | 1 |
| 3 | Client → Server | ACK | 1 | 1 |

**Why It Matters:**
The three-way handshake is how TCP establishes a reliable connection. Understanding this process is essential for:
- Diagnosing network connectivity issues.
- Identifying abnormal traffic patterns (e.g., SYN floods in DoS attacks).
- Analyzing network performance.

---

### 4. Unencrypted HTTP Data

**Screenshot:** `unencrypted_http.png`

**Observation:**
- An HTTP GET request was examined in detail.
- The following fields were visible in plain text:
  - `Request Method: GET`
  - `Request URI: /`
  - `Host: neverssl.com`
  - `User-Agent: Mozilla/5.0...`
  - `Cookie: (any present)`

**Security Risk:**
This information can be captured by a Man-in-the-Middle attacker on the same network. Sensitive information such as:
- Login credentials (if sent via HTTP)
- Session cookies (can be stolen and reused)
- Personal data (names, addresses)

could be intercepted and misused.

**How HTTPS Prevents This:**
HTTPS encrypts the entire HTTP payload using TLS. Even if an attacker captures the traffic, they only see encrypted gibberish — the payload is unreadable without the decryption keys.

---

## Glossary (In My Own Words)

| Term | My Definition |
| :--- | :--- |
| **Packet** | A small unit of data sent over a network. It contains the actual data plus header information (e.g., source/destination IP and port). |
| **Protocol** | A set of rules that define how data is formatted and transmitted. Examples: HTTP, TCP, DNS. |
| **Port** | A numbered endpoint on a computer that identifies a specific process or service. For example, port 80 is used for HTTP; port 443 is used for HTTPS. |
| **Payload** | The actual data being transported, excluding the headers. For example, the content of an HTTP request (the HTML page, API response, etc.). |
| **Handshake** | A process where two devices establish a connection by exchanging control packets. The TCP three-way handshake (SYN, SYN-ACK, ACK) is the most common example. |

---

## References

1. Wireshark User Guide. (2026). *Wireshark Documentation*. Available at: wireshark.org/docs/
2. Nmap & Wireshark Tutorial. (2025). *Network Analysis for Beginners*.
3. RFC 793 – Transmission Control Protocol (TCP) Specification.

---


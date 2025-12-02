# Wireshark Network Traffic Analysis Lab

## Overview
This project documents a full network traffic analysis exercise performed using Wireshark.  
The goal was to examine a packet capture file (`sample.pcap`) and analyze:

- IP communication patterns  
- DNS queries and responses  
- TCP/HTTP traffic  
- ICMP packets  
- MAC-level communication  
- Packet structure across multiple OSI layers  

Screenshots from the investigation are included to demonstrate each step.

---

# Task 1 — Exploring Packet Data

The lab began by launching a Windows VM and opening the `sample.pcap` file in Wireshark.

**Screenshot — Windows VM Desktop**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/1.PNG)

Wireshark displayed 200 packets containing DNS, TCP, ICMP, SSH, and HTTP traffic.

**Screenshot — Packet Overview**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/2.PNG)

Key packet fields reviewed:
- Packet number  
- Timestamp  
- Source / Destination IP  
- Protocol  
- Length  
- Summary information  

---

# Task 2 — Applying Filters and Inspecting Packets

## 2.1 Filtering by IP Address
A filter was applied to view traffic to/from the server `142.250.1.139`:

ip.addr == 142.250.1.139

yaml
Copy code

**Screenshot — IP Filter Applied**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/3.PNG)

## 2.2 Inspecting Packet Layers
Packets were expanded to view:

- Frame details  
- Ethernet II header  
- IPv4 header  
- TCP header  

This revealed information such as MAC addresses, TTL values, TCP flags, port numbers, and packet lengths.

---

# Task 3 — Filtering by Source, Destination, and MAC Address

## 3.1 Filter by Source IP
ip.src == 142.250.1.139

scss
Copy code

**Screenshot — Source IP Filter**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/4.PNG)

## 3.2 Filter by Destination IP
ip.dst == 142.250.1.139

css
Copy code

*(Screenshot unavailable due to VM crash.)*

## 3.3 Filter by MAC Address
eth.addr == 42:01:ac:15:e0:02

yaml
Copy code

**Screenshots — MAC Address Filters**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/5.PNG)
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/6.PNG)

These filters identified all packets involving the target MAC address.

---

# Task 4 — DNS Analysis

## 4.1 Filtering DNS Traffic
udp.port == 53

mathematica
Copy code

**Screenshot — DNS Packet List**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/7.PNG)

## 4.2 Inspecting DNS Query
**Screenshot — DNS Query Packet**  

Queried Domain:
opensource.google.com
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/4.PNG)

yaml
Copy code

## 4.3 Inspecting DNS Response
**Screenshot — DNS Response**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/6.PNG)

This contained the resolved IP addresses for the domain.

---

# Task 5 — TCP / HTTP Traffic Analysis

## 5.1 Filtering Web Traffic
tcp.port == 80

markdown
Copy code

**Screenshot — Port 80 Traffic**  
![image alt](https://github.com/HusseinCyberSec/Analyze-your-first-packet-with-Wireshark/blob/717076d9b2b83ac03fd221a0144e3e0f81fb814c/3.PNG)

This displayed:
- HTTP 301 redirects  
- TCP handshake packets  
- ACK packets  
- Traffic to/from `169.254.169.254`  

## 5.2 Inspecting TCP Details
The TCP header revealed:
- TTL values  
- TCP flags  
- Sequence and acknowledgment numbers  
- Header length  
- Frame length  

---

# Skills Demonstrated

### Networking & Packet Analysis
- Understanding protocol behavior (DNS, TCP, UDP, ICMP)  
- Inspecting packet structure across OSI layers  
- Identifying MAC, IP, and port relationships  

### SOC / Cybersecurity Skills
- Filtering traffic efficiently  
- DNS investigation and domain resolution analysis  
- HTTP traffic inspection  
- Recognizing communication flows and patterns  

### Forensic Investigation Skills
- Extracting meaningful data from packet captures  
- Analyzing payloads  
- Correlating events across different protocol layers  

---

# Conclusion
This Wireshark lab demonstrated practical SOC-level network analysis skills including IP filtering, DNS inspection, TCP flow analysis, MAC address tracking, and deep packet inspection.  
These techniques are essential for:

- SOC Analysts  
- GSOC Operators  
- Cybersecurity Analysts  
- Digital Forensics Investigators  

This project shows a complete, end-to-end packet analysis workflow using real data.

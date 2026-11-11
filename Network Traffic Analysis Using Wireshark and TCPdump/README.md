# Network Traffic Analysis Using Wireshark and TCPdump

## Project Overview

This project demonstrates practical experience in network traffic analysis using **Wireshark** and **TCPdump**, two open-source network protocol analyzers widely used in cybersecurity and network administration.

The activities involved inspecting captured network packets, identifying source and destination IP addresses, examining network protocols, filtering DNS and TCP traffic, capturing live network packets, and saving packet data for further investigation.

The exercises provided hands-on exposure to packet-level network analysis in both graphical and command-line environments.

## Tools and Technologies

- **Wireshark:** Graphical network protocol analyzer used for packet inspection, protocol identification, and traffic filtering.
- **TCPdump:** Command-line packet analyzer used to capture, filter, and inspect network traffic.
- **Linux Terminal:** Used to execute TCPdump commands and identify network interfaces.
- **PCAP:** Packet Capture file format used to store network traffic for subsequent analysis.

## Practical Activities

### 1. Wireshark Packet Analysis

Using a sample packet capture file, I explored Wireshark's graphical interface and examined the structure and contents of network packets.

Activities performed:

- Opened and explored a packet capture file.
- Examined packet numbers, timestamps, source IP addresses, destination IP addresses, protocols, packet lengths, and information fields.
- Applied IP address filters to isolate relevant traffic.
- Inspected Ethernet II, IPv4, and TCP protocol layers.
- Examined source and destination TCP ports, sequence numbers, and TCP flags.
- Used MAC address filters to identify related Ethernet traffic.

**Wireshark display filters practiced:**

```text
ip.addr == 142.250.1.139
ip.src == 142.250.1.139
ip.dst == 142.250.1.139
eth.addr == 42:01:ac:15:e0:02
```

### 2. DNS Traffic Analysis

I investigated DNS traffic using Wireshark to understand how domain names are resolved into IP addresses.

Activities performed:

- Filtered UDP traffic using port 53.
- Inspected DNS query packets.
- Examined DNS response packets.
- Identified the queried domain: `opensource.google.com`.
- Inspected the corresponding DNS answer records.

**Display filter:**

```text
udp.port == 53
```

### 3. TCP Traffic and Payload Inspection

I explored TCP packet traffic and practiced searching packet payloads for specific text.

**Display filter:**

```text
tcp contains "curl"
```

This filter identified packets containing the text associated with HTTP requests generated using the curl command in the sample capture.

### 4. TCPdump Network Traffic Capture

Using a Linux virtual machine, I practiced capturing and analyzing network traffic directly from the command line.

**Identifying available network interfaces:**

```bash
sudo ifconfig
sudo tcpdump -D
```

**Inspecting live traffic:**

```bash
sudo tcpdump -i eth0 -v -c5
```

This captured five packets from the eth0 interface and displayed detailed packet information.

**Capturing HTTP traffic into a PCAP file:**

```bash
sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
```

I then generated HTTP traffic using:

```bash
curl opensource.google.com
```

**Verifying the capture file:**

```bash
ls -l capture.pcap
```

**Reading and inspecting captured packets:**

```bash
sudo tcpdump -nn -r capture.pcap -v
```

These activities provided practical experience in capturing, storing, retrieving, and inspecting network traffic.

## 5. Wireshark vs. TCPdump

| Wireshark | TCPdump |
|---|---|
| Graphical User Interface (GUI) | Command-Line Interface (CLI) |
| Advanced filtering and packet coloring | Lightweight and resource-efficient |
| Detailed visual packet inspection | Efficient live packet capture |
| Requires more system resources | Requires fewer system resources |

Both tools support network protocol analysis, are open-source, and are available free of charge.

## 6. Skills Demonstrated

- Network traffic monitoring and analysis.
- Packet capture and inspection.
- TCP/IP protocol analysis.
- DNS query and response investigation.
- IP and MAC address identification.
- TCP port and packet header inspection.
- Network traffic filtering.
- Linux command-line operations.
- PCAP file management.
- Basic network troubleshooting and investigation.

## 7. Cybersecurity Relevance

Packet analysis is an important skill in security operations and network defense.

Understanding network traffic helps security analysts investigate suspicious communications, identify unusual network activity, examine DNS requests, understand communication patterns, and gather evidence during network security investigations.

This practical exercise strengthened my understanding of how network protocols operate and how packet analysis tools can support cybersecurity monitoring and incident investigation.

# 8. Learning Outcome

Through these practical exercises, I developed foundational experience using both graphical and command-line packet analysis tools.

I learned how to capture network traffic, apply filters, inspect packet headers and protocol layers, investigate DNS communications, and save network traffic for further analysis.

---

**Project Category:** Cybersecurity | Network Security | Network Traffic Analysis

**Tools:** Wireshark | TCPdump | Linux | PCAP

**Learning Focus:** Practical Network Protocol Analysis


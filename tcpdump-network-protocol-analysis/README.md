Network Protocol Analysis with tcpdump: DNS, UDP & ICMP Investigation

Lab type: Simulated cybersecurity investigation
Training platform: Coursera
Primary tool: tcpdump
Protocols analyzed: DNS, UDP, ICMP

Project Overview

This project documents a network protocol analysis exercise completed as part of cybersecurity training. The exercise used a simulated tcpdump dataset provided by Coursera to investigate a website-accessibility incident.

The scenario involved users receiving a “destination port unreachable” message while attempting to access yummyrecipesforme.com. The provided packet data was analyzed to determine what the network traffic revealed and to identify plausible causes requiring further investigation.

Data-source note: The packet output analyzed in this project was provided as part of the Coursera training exercise. It was not captured by me from a live production network.

Investigation Objective

Analyze the provided tcpdump output.

Identify the network protocols involved.

Interpret DNS, UDP, and ICMP traffic.

Identify the relevant port and error response.

Determine what the packet evidence suggested about the incident.

Identify plausible causes and appropriate next troubleshooting steps.

Scenario

Customers reported that they could not access the organization's website and received a “destination port unreachable” error.

The investigation used the provided tcpdump output to examine communication between the client and the DNS service.

Protocols Identified

DNS

DNS was involved in resolving the domain name to an IP address. The analysis identified DNS-related traffic associated with port 53.

UDP

UDP was used to send the DNS request from the browser/client toward the DNS server.

ICMP

ICMP was used to return an error response after the DNS request.

The critical response observed in the dataset was:

udp port 53 unreachable

Key Packet Analysis

The provided tcpdump output showed a sequence in which:

The client sent a UDP request toward the DNS service.

The request was associated with DNS communication.

An ICMP response was returned.

The ICMP response indicated that UDP port 53 was unreachable.

The analysis also referenced the DNS query identification number and the A? notation as indicators associated with the DNS request for an A record. An A record maps a domain name to an IP address.

Findings

The main finding from the simulated packet data was that DNS communication was unsuccessful because UDP port 53 was reported as unreachable.

This suggested that the DNS service was unavailable or that traffic to the DNS service was being prevented.

The evidence did not, by itself, establish a single definitive root cause.

Possible Causes

1. DNS server failure

The DNS server may not have been functioning properly, resulting in unsuccessful DNS requests.

2. Firewall configuration

A firewall configuration change could have blocked network traffic to port 53.

3. Possible DoS condition

The training scenario also identifies a possible Denial-of-Service (DoS) condition as another explanation that could cause the DNS service to become unavailable. This should be treated as a hypothesis requiring additional investigation rather than as a confirmed attack.

Recommended Next Steps

Determine whether the DNS server is functioning properly.

Check whether traffic to UDP port 53 is being blocked by a firewall.

Review recent firewall configuration changes.

Investigate whether the DNS service experienced an availability or DoS-related event.

Correlate the network evidence with additional logs before determining the root cause.

Skills Demonstrated

Network protocol analysis

Packet-level investigation

tcpdump analysis

DNS troubleshooting

UDP traffic analysis

ICMP error interpretation

Port analysis

Incident investigation

Root-cause hypothesis development

Technical documentation

Tools & Technologies

Tool / Technology

Purpose

tcpdump

Network packet analysis tool used in the training exercise

DNS

Domain-name resolution protocol examined during the investigation

UDP

Transport protocol used for the DNS request

ICMP

Protocol carrying the unreachable-port error response

Linux/networking concepts

Supporting concepts for packet analysis

What I Learned

This exercise reinforced the importance of analyzing network traffic at the protocol level when investigating connectivity and security incidents.

A user-facing error such as “destination port unreachable” can be investigated by examining the underlying packet exchange, identifying the protocol involved, checking the destination port, and interpreting the response.

The exercise also reinforced the difference between a finding and a confirmed root cause: the packet evidence established that UDP port 53 was unreachable, while the reason for that condition required further investigation.

Portfolio Takeaway

This project demonstrates my developing ability to move from:

Observed traffic → Protocol identification → Error interpretation → Possible causes → Next investigative steps

It forms part of my broader cybersecurity portfolio alongside network security architecture, security auditing, network assessment, and IDS/IPS exercises.

Training Attribution

This project was completed as part of cybersecurity training through Coursera. The packet data and scenario were provided as simulated training material.

The analysis and presentation in this repository have been independently organized and rewritten for portfolio documentation.

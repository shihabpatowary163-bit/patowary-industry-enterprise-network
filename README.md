# Patowary Industry – Enterprise Network Design and Simulation

## Project Overview

This project focuses on designing and simulating an enterprise network infrastructure for Patowary Industry using Cisco Packet Tracer.

The network connects the company's headquarters, multiple office floors, a central server room, and a remote branch office through an ISP-based WAN architecture.

The main goal was to build a network where different departments and locations can communicate while supporting essential services such as DNS, web hosting, email, and FTP. The project also includes external BGP routing and Quality of Service (QoS) configuration.

## Network Architecture

The network consists of the following components:

- **Headquarters (HQ):** Multiple office floors, including IT and Executive, Sales, and Management and Voice departments.
- **Server Room:** Centralized FTP, email, DNS, and web servers.
- **Remote Branch Office:** A separate network connected to headquarters through the ISP infrastructure.
- **WAN Infrastructure:** ISP routers connecting the headquarters and remote branch.
- **Switching Infrastructure:** Cisco 2960 access switches and a multilayer Cisco 3560 switch.

### Network Topology

![Full Network Diagram](evidence/Full%20network%20diagram.png)

## Network Configuration

### 1. IP Addressing

Static IP addressing was configured for the network devices and end-user PCs.

Each network segment uses its assigned IP network, subnet mask, and default gateway. DHCP is not configured or used in this project.

Example branch PC configuration:

- IP Address: `10.20.60.10`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `10.20.60.254`

[View PC IP Configuration](evidence/PC%20IP%20configuration.png)

### 2. External BGP Routing

External Border Gateway Protocol (eBGP) was configured to establish routing between the headquarters, ISP routers, and remote branch.

The autonomous systems used in the simulation are:

| Router | Autonomous System |
|---|---|
| HQ Router | AS 65001 |
| ISP-PE-1 | AS 65000 |
| ISP-P-1 | AS 65003 |
| Branch Router | AS 65002 |

The routing configuration allows the HQ and branch networks to exchange routes through the ISP infrastructure.

The advertised network prefixes include:

- `10.10.0.0/16` – Headquarters network
- `10.20.60.0/24` – Remote branch network

### BGP Verification

- [BGP Neighbour Status](evidence/show%20ip%20bgp%20summary.png)
- [BGP Routing Table](evidence/show%20ip%20bgp.png)
- [BGP Learned Routes](evidence/show%20ip%20route%20bgp.png)
- [Router Interface Status](evidence/show%20ip%20interface%20brief.png)

## Network Services

Several services were configured and tested to demonstrate communication between network devices and users.

### 3. DNS and HTTP Services

The DNS server was configured to support hostname resolution within the enterprise network. An HTTP web server was also configured to host the Patowary Industry Official Office Enterprise Portal.

The website was accessed successfully from a client PC, confirming HTTP connectivity to the web server.

[View Website Access Evidence](evidence/Working%20website%20using%20domain%20name.png)

### 4. Email Communication

An email server was configured with SMTP and POP3 services. Email communication was tested between user accounts, and successful delivery was confirmed.

[View Successful Email Delivery](evidence/Successful%20email%20delivery.png)

### 5. FTP Service

An FTP server was configured to provide file transfer functionality. The service was tested successfully from a client device.

[View Successful FTP Test](evidence/Successful%20FTP%20test.png)

## Quality of Service (QoS)

QoS was configured on the HQ router's GigabitEthernet0/1 interface using a policy named `WAN-QOS-POLICY`.

Traffic was classified into different classes:

- **VOICE-CLASS:** Matches voice traffic using DSCP EF (46) and uses strict priority queuing.
- **WEB-CLASS:** Identifies HTTP traffic and applies its configured bandwidth allocation.
- **FTP-CLASS:** Identifies FTP traffic and applies its configured bandwidth allocation.
- **Class-default:** Handles traffic that does not match the defined classes.

The interface verification output confirms that the QoS policy is attached and that HTTP traffic has matched the WEB-CLASS.

[View QoS Policy Verification](evidence/show%20policy-map%20interface%20gigabitEthernet%2001.png)

## Network Connectivity Testing

Connectivity was tested to verify communication between network devices and the configured gateway.

Successful ping responses were received with no packet loss in the recorded test.

[View Successful Ping Results](evidence/Successful%20ping%20results.png)

## Project Files

| File | Description |
|---|---|
| `ADVANCED NETWORK PROJECT.pkt` | Complete Cisco Packet Tracer network simulation |
| `evidence/` | Configuration and verification screenshots |

## Tools and Technologies

- Cisco Packet Tracer
- Cisco IOS Command Line Interface (CLI)
- Static IP Addressing
- External BGP (eBGP)
- DNS
- HTTP
- SMTP and POP3
- FTP
- Quality of Service (QoS)

## Conclusion

This project demonstrates the design and configuration of an enterprise network connecting headquarters and a remote branch through an ISP-based routing infrastructure.

It provided practical experience with network segmentation, static IP configuration, eBGP routing, server-based services, connectivity testing, and QoS configuration. The successful verification tests demonstrate that the major network components and services are functioning within the simulation.

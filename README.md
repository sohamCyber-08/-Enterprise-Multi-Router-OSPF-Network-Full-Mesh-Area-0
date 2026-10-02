

# 🌐 Enterprise-Multi-Router-OSPF-Network-Full-Mesh-Area-0

## 🎯 Project Objective

Design and implement a simulated enterprise campus network consisting of 4 routers, 3 Layer 2 switches, a centralized DHCP server, and 4 end hosts. Configure a fully meshed OSPF Area 0 topology to provide dynamic routing and network redundancy, implement DHCP relay to enable centralized IP address allocation across multiple subnets, and secure all network devices with SSH-only remote management. Finally, validate the complete network design through end-to-end connectivity testing and real-world Cisco IOS diagnostic and verification commands.

## 🖥️ Topology

PC1 ─── SW1 ─── PC2

## 🌐 IP Addressing

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC1 | 192.168.10.10 | 255.255.255.0 |
| PC2 | 192.168.10.20 | 255.255.255.0 |

## 🔧 Technologies

- Cisco Packet Tracer
- IPv4
- Ethernet
- ARP
- ICMP
- MAC Address Table

## 🔍 Verification

### Ping Test

PC1 successfully pinged PC2.

### ARP Verification

Verified the IP-to-MAC mapping using:

arp -a

### Switch MAC Learning

Verified learned MAC addresses using:

show mac address-table

## 📊 Communication Process

### Same VLAN Communication

```mermaid
flowchart TD
    A[Cyber_EMPLOYER_1<br/>10.1.1.1<br/>VLAN 10] --> B[Check Destination IP]
    B --> C{Same VLAN?}
    C -->|Yes| D[Check ARP Table]
    D --> E{MAC Address Known?}
    E -->|No| F[ARP Request]
    F --> G[ARP Reply]
    G --> H[Create Ethernet Frame]
    E -->|Yes| H
    H --> I[Access Port]
    I --> J[Switch]
    J --> K[802.1Q Trunk]
    K --> L[Other Switch]
    L --> M[Destination Access Port]
    M --> N[Cyber_EMPLOYER_2<br/>10.1.1.2<br/>VLAN 10]
    N --> O[ICMP Echo Request]
    O --> P[ICMP Echo Reply]
    P --> Q[Successful Communication]

```
## ✅ Result

PC1 and PC2 successfully communicated through
the Layer 2 switch within the same IPv4 subnet.

## 📚 Key Learning

- IPv4 addressing
- Subnet identification
- ARP
- MAC address learning
- ICMP
- Basic Layer 2 communication

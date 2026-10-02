

# 🌐 Enterprise-Multi-Router-OSPF-Network-Full-Mesh-Area-0

## 🎯 Project Objective

Design and implement a simulated enterprise campus network consisting of 4 routers, 3 Layer 2 switches, a centralized DHCP server, and 4 end hosts. Configure a fully meshed OSPF Area 0 topology to provide dynamic routing and network redundancy, implement DHCP relay to enable centralized IP address allocation across multiple subnets, and secure all network devices with SSH-only remote management. Finally, validate the complete network design through end-to-end connectivity testing and real-world Cisco IOS diagnostic and verification commands.

## 🖥️ Topology
<br>
<br>
<br>
<img width="1547" height="878" alt="Screenshot 2026-10-01 182754" src="https://github.com/user-attachments/assets/01f07135-b574-4047-aaed-d9c2cc91a13d" />
<br>
<br>
<br>

## 🔢 IP Addressing


### Inter-Router Links

| Link | Network | R1 | R2 | R3 | R4 |
|---|---|---|---|---|---|
| R1 Gi0/0 ↔ R2 Gi0/0 | `12.1.1.0/30` | `12.1.1.1` | `12.1.1.2` | <div align="center">—</div> | <div align="center">—</div> |
| R1 Gi0/1 ↔ R3 Gi0/1 | `13.1.1.0/30` | `13.1.1.1` | <div align="center">—</div> | `13.1.1.2` | <div align="center">—</div> |
| R1 Gi0/2 ↔ R4 Gi0/1 | `14.1.1.0/30` | `14.1.1.1` | <div align="center">—</div> | <div align="center">—</div> | `14.1.1.2` |
| R2 Gi0/1 ↔ R3 Gi0/0 | `23.1.1.0/30` | <div align="center">—</div> | `23.1.1.1` | `23.1.1.2` | <div align="center">—</div> |
| R2 Gi0/2 ↔ R4 Gi0/2 | `24.1.1.0/30` | <div align="center">—</div> | `24.1.1.1` | <div align="center">—</div> | `24.1.1.2` |
| R3 Gi0/2 ↔ R4 Gi0/0 | `34.1.1.0/30` | <div align="center">—</div> | <div align="center">—</div> | `34.1.1.1` | `34.1.1.2` |

### LAN Segments

| LAN Segment | Network | Gateway | Devices |
|---|---|---|---|
| R2 Gi0/3 ↔ SW1 | `10.1.1.0/24` | `10.1.1.1` (R2) | PC1, PC2 — DHCP |
| R3 Gi0/3 ↔ SW2 | `20.1.1.0/24` | `20.1.1.1` (R3) | PC3 — DHCP |
| R4 Gi0/3 ↔ SW3 | `30.1.1.0/24` | `30.1.1.1` (R4) | PC4, DHCP Server `30.1.1.100` |

### Loopbacks & OSPF

| Router | Loopback | OSPF Process ID | OSPF Router ID | Area |
|---|---|:---:|:---:|---|
| R1 | `1.1.1.1/32` | `100` | `1.1.1.1` | Area 0 |
| R2 | `2.2.2.2/32` | `200` | `2.2.2.2` | Area 0 |
| R3 | `3.3.3.3/32` | `300` | `3.3.3.3` | Area 0 |
| R4 | `4.4.4.4/32` | `400` | `4.4.4.4` | Area 0 |

<br>
<br>
<br>

## 🔧 **Technologies**

- **EVE-NG**
- **Cisco IOS**
- **IPv4**
- **OSPFv2**
- **OSPF Area 0**
- **Full-Mesh Routing**
- **Static IP Addressing**
- **DHCP**
- **DHCP Relay** (`ip helper-address`)
- **IPv4 Subnetting**
- **Ethernet**
- **ARP**
- **ICMP**
- **SSH**
- **Cisco IOS CLI**
- **Routing Table Verification**
- **Network Connectivity & Troubleshooting**
<br>
<br>
<br>


Yes. The main issue is that your current README has **inconsistent spacing and heading levels**. For a professional GitHub repository, keep each router section in the same structure:

**Router → Objective → Configuration screenshots → Verification → Verification screenshot → next router**

I would also avoid excessive `<br>` tags. A few blank lines are enough in GitHub Markdown.

Here is your **copy-paste-ready version**:

````markdown
# 🛠️ TASK TO PERFORM

## 🔹 Phase 1 — Basic Interface & OSPF Configuration

---

### 📍 1.1 R1 — Interface & OSPF Configuration

**Objective**

Configure R1's inter-router interfaces, Loopback interface, and OSPF process to establish dynamic routing and participate in the OSPF Area 0 domain.

#### ⚙️ Interface & OSPF Configuration

<img width="1906" height="843" alt="R1 Interface Configuration" src="https://github.com/user-attachments/assets/56b18ab4-12ac-4a6f-93ca-0bb61af26245" />

<br>

<img width="1900" height="980" alt="R1 OSPF Configuration" src="https://github.com/user-attachments/assets/09ec883d-4594-4097-9889-9a7eeaa572cc" />

<br>

#### 🔍 Verification

**Interface Status**

```cisco
show ip interface brief
````

**OSPF Process**

```cisco
show ip ospf
```

<img width="1772" height="878" alt="R1 OSPF Verification" src="https://github.com/user-attachments/assets/2c92ef8f-3618-484c-8b3e-a9eb734e1532" />

---

### 📍 1.2 R2 — Interface & OSPF Configuration

**Objective**

Configure R2's inter-router interfaces, LAN interface, Loopback interface, and OSPF process to establish dynamic routing and participate in the OSPF Area 0 domain.

#### ⚙️ Interface & OSPF Configuration

<img width="1715" height="683" alt="R2 Interface Configuration" src="https://github.com/user-attachments/assets/6bc576a9-334f-4619-8e35-4f61a530abbf" />

<br>

<img width="1696" height="995" alt="R2 OSPF Configuration" src="https://github.com/user-attachments/assets/cdac589f-4afb-4db4-9bd9-e638066bca4f" />

<br>

#### 🔍 Verification

**Interface Status**

```cisco
show ip interface brief
```

**OSPF Process**

```cisco
show ip ospf
```

<img width="1716" height="641" alt="R2 OSPF Verification" src="https://github.com/user-attachments/assets/bd3ed1fe-938e-45ac-961c-64e1e0f9b669" />

---

### 📍 1.3 R3 — Interface & OSPF Configuration

**Objective**

Configure R3's inter-router interfaces, LAN interface, Loopback interface, and OSPF process to establish dynamic routing and participate in the OSPF Area 0 domain.

#### ⚙️ Interface & OSPF Configuration

<img width="1816" height="865" alt="R3 Interface Configuration" src="https://github.com/user-attachments/assets/5a650a28-0fad-4aae-8b0a-95397734222b" />

<br>

<img width="1881" height="1006" alt="R3 OSPF Configuration" src="https://github.com/user-attachments/assets/8e2b664f-1d9c-4168-a477-0cc4847b43d7" />

<br>

#### 🔍 Verification

**Interface Status**

```cisco
show ip interface brief
```

**OSPF Process**

```cisco
show ip ospf
```

<img width="1595" height="696" alt="R3 OSPF Verification" src="https://github.com/user-attachments/assets/f920afb6-7c54-44fa-b7a8-e807d94ff18b" />

---

### 📍 1.4 R4 — Interface & OSPF Configuration

**Objective**

Configure R4's inter-router interfaces, LAN interface, Loopback interface, and OSPF process to establish dynamic routing and participate in the OSPF Area 0 domain.

#### ⚙️ Interface & OSPF Configuration

<img width="1682" height="647" alt="R4 Interface Configuration" src="https://github.com/user-attachments/assets/b1fd38c1-028a-4a47-bbeb-753867517db5" />

<br>

<img width="1691" height="771" alt="R4 OSPF Configuration" src="https://github.com/user-attachments/assets/e2dc7c50-b02a-4fb5-bd29-0eb0ff20a35b" />

<br>

#### 🔍 Verification

**Interface Status**

```cisco
show ip interface brief
```

**OSPF Process**

```cisco
show ip ospf
```

<img width="1731" height="703" alt="R4 OSPF Verification" src="https://github.com/user-attachments/assets/f7c60a24-c8ac-454b-a8ce-a3561b69a2c6" />

---

## ✅ Phase 1 — Completion Status

| Router | Interfaces | Loopback | OSPF Area 0 | Verification |
| :----: | :--------: | :------: | :---------: | :----------: |
| **R1** |      ✅     |     ✅    |      ✅      |       ✅      |
| **R2** |      ✅     |     ✅    |      ✅      |       ✅      |
| **R3** |      ✅     |     ✅    |      ✅      |       ✅      |
| **R4** |      ✅     |     ✅    |      ✅      |       ✅      |

**Phase 1 Result:**
All four routers have been configured with their required Layer 3 interfaces, Loopback interfaces, and OSPF Area 0 parameters. The topology is ready for OSPF neighbor establishment and subsequent DHCP Relay and SSH configuration phases.

````

### One important improvement

I changed your R2/R3/R4 objectives from:

> "inter-router interfaces, Loopback interface..."

to:

> **"inter-router interfaces, LAN interface, Loopback interface..."**

because R2, R3, and R4 also have their respective **LAN-facing interfaces** (`G0/3`) in your topology. That makes the documentation technically more complete.

Also, use the **full Cisco commands** in documentation:

```cisco
show ip interface brief
show ip ospf
````

rather than:

```cisco
sh ip int brief
sh ip ospf
```

Short commands are perfectly valid in the Cisco CLI, but full commands look more professional in a GitHub portfolio and are easier for another person to understand/copy.







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

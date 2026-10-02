

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
<br>
<br>

**Phase 1 Result:**
All four routers have been configured with their required Layer 3 interfaces, Loopback interfaces, and OSPF Area 0 parameters. The topology is ready for OSPF neighbor establishment and subsequent DHCP Relay and SSH configuration phases.




## 🔹 Phase 2 — Inter-LAN Connectivity Verification

### 📍 2.1 PC3 → PC1 End-to-End Connectivity Test

#### 🎯 Objective

Verify end-to-end connectivity between **PC3 (`20.1.1.10`)** and **PC1 (`10.1.1.10`)** across different LAN networks using the configured **OSPF Area 0** routing topology.

This test validates that:
- PC3 can reach its default gateway **R3 (`20.1.1.1`)**
- OSPF has learned the **10.1.1.0/24** network
- Routers can forward traffic across the routed network
- PC1 can receive and respond to ICMP traffic from PC3

#### 🧪 Connectivity Test

**Source:** PC3 — `20.1.1.10`  
**Destination:** PC1 — `10.1.1.10`

```text
PC3 (20.1.1.10)
       │
       ▼
R3 (20.1.1.1)
       │
       │ OSPF Area 0
       ▼
   Routed Network
       │
       ▼
R2 (10.1.1.1)
       │
       ▼
PC1 (10.1.1.10)
````

#### 🔍 Verification

From **PC3**, send an ICMP ping to PC1:

```bash
ping 10.1.1.10
```

**Result:**
<img width="1830" height="810" alt="Screenshot 2026-10-01 184924" src="https://github.com/user-attachments/assets/13bb7177-712b-4858-b175-3b67dc371e8d" />
<br>
<br>



Successful replies confirm that **PC3 can communicate with PC1 across different IP networks through the OSPF-routed topology**.

#### 🖥️ PC3 → PC1 Test Result

|      Source     |   Destination   | Protocol |    Result    |
| :-------------: | :-------------: | :------: | :----------: |
| PC3 `20.1.1.10` | PC1 `10.1.1.10` |   ICMP   | ✅ Successful |

#### 🧠 What This Test Demonstrates

The successful ping verifies the complete forwarding path:

**PC3 → R3 → OSPF-Routed Network → R2 → PC1**

It confirms that the **20.1.1.0/24** and **10.1.1.0/24** networks are reachable through the configured routing infrastructure and that end-to-end ICMP communication is working correctly.





For your repo, **Phase 3** can document the centralized DHCP design and the DHCP Relay Agent configuration. Since your DHCP server is `30.1.1.100`, and the clients in `10.1.1.0/24` and `20.1.1.0/24` are on different routed networks, R2 and R3 act as DHCP relay agents.

## 🔹 Phase 3 — DHCP Relay Agent Configuration

### 📍 1.1 Centralized DHCP Server

#### 🎯 Objective

Configure a centralized DHCP server at **`30.1.1.100`** to dynamically assign IPv4 addresses to clients located on different LAN networks.

Because DHCP client requests are initially sent as **broadcasts** and routers do not forward broadcast traffic by default, **DHCP Relay Agent** functionality is required on the routers connecting the client LANs to the centralized DHCP server.

#### 🌐 DHCP Network Design

| LAN | Network | Default Gateway | DHCP Server |
|:---:|:---:|:---:|:---:|
| PC1 / PC2 | `10.1.1.0/24` | `10.1.1.1` | `30.1.1.100` |
| PC3 | `20.1.1.0/24` | `20.1.1.1` | `30.1.1.100` |
| PC4 | `30.1.1.0/24` | `30.1.1.1` | `30.1.1.100` |



#### 🌐 DHCP Server Information

| Parameter | Configuration |
|:---|:---:|
| **DHCP Server IP** | `30.1.1.100` |
| **Server Network** | `30.1.1.0/24` |
| **Default Gateway** | `30.1.1.1` |
| **DHCP Service** | Enabled |
| **Address Allocation** | Dynamic |

#### ⚙️ DHCP Pool Configuration
<br>
<br>
<img width="1686" height="691" alt="Screenshot 2026-10-01 185109" src="https://github.com/user-attachments/assets/5fce0da4-d1f6-4276-b930-d6ab2d9ae49c" />
<br>
<br>
<img width="1791" height="692" alt="Screenshot 2026-10-01 185117" src="https://github.com/user-attachments/assets/58054a57-eaa4-4a3d-8f09-f2e8ab76ccbc" />
<br>
<br>

#### 🔍 Verification

**Interface Status**

```cisco
show ip interface brief
```

**DHCP pool**

```cisco
show ip dhcp pool
```
<br>
<br>
<img width="1390" height="877" alt="Screenshot 2026-10-01 185148" src="https://github.com/user-attachments/assets/b6188289-af59-40e1-aa7c-d9ace6e03090" />
<br>
<br>











### 📍 1.2 R2 — DHCP Relay Agent

#### ⚙️ Configuration

R2 connects the **10.1.1.0/24** client network to the centralized DHCP server.

Configure the DHCP Relay Agent on the LAN-facing interface:

#### ⚙️ R2 — DHCP Relay Agent

R2 provides connectivity to the **10.1.1.0/24** LAN containing PC1.

Configure the LAN-facing interface:


interface g0/3
 ip helper-address 30.1.1.100
 no shutdown
end
write memory

The ip helper-address command enables R2 to forward DHCP requests received from the 10.1.1.0/24 LAN toward the centralized DHCP server.

⚙️ R3 — DHCP Relay Agent

R3 provides connectivity to the 20.1.1.0/24 LAN containing PC3.

interface g0/3
 ip helper-address 30.1.1.100
 no shutdown
end
write memory

R3 forwards DHCP requests from the 20.1.1.0/24 network toward the centralized DHCP server.

⚙️ R4 — DHCP Relay Agent

R4 provides connectivity to the 30.1.1.0/24 LAN containing PC4 and the centralized DHCP server.

interface g0/3
 ip helper-address 30.1.1.100
 no shutdown
end
write memory

Note: The DHCP server 30.1.1.100 and PC4 are on the same 30.1.1.0/24 LAN, so a DHCP relay is not technically required for PC4. The relay configuration is retained as part of this lab's router configuration.


<br>
<br>
<img width="1905" height="1011" alt="Screenshot 2026-10-01 185332" src="https://github.com/user-attachments/assets/577331cc-238f-4891-9216-da562fed8b34" />
<br>












```cisco
interface g0/3
 ip helper-address 30.1.1.100
````

The `ip helper-address` command forwards DHCP client requests received on the LAN interface toward the centralized DHCP server.

#### 🔍 Verification

```cisco
show running-config interface g0/3
```

Expected configuration:

```text
interface GigabitEthernet0/3
 ip address 10.1.1.1 255.255.255.0
 ip helper-address 30.1.1.100
```

---

### 📍 3.3 R3 — DHCP Relay Agent

#### ⚙️ Configuration

R3 connects the **20.1.1.0/24** client network to the centralized DHCP server.

Configure the DHCP Relay Agent:

```cisco
interface g0/3
 ip helper-address 30.1.1.100
```

#### 🔍 Verification

```cisco
show running-config interface g0/3
```

Expected configuration:

```text
interface GigabitEthernet0/3
 ip address 20.1.1.1 255.255.255.0
 ip helper-address 30.1.1.100
```

---

### 📍 3.4 DHCP Relay Operation

When a DHCP client starts without an IP address, the request follows this process:

```text
PC3
20.1.1.10
   │
   │ DHCP Broadcast
   ▼
R3
20.1.1.1
   │
   │ DHCP Relay
   │ ip helper-address 30.1.1.100
   ▼
Routed Network
   │
   ▼
DHCP Server
30.1.1.100
```

The router receives the DHCP broadcast on the client-facing interface and forwards the request as a **unicast packet** toward the DHCP server.

The DHCP server uses the relay information to determine which client subnet the request originated from and selects the appropriate DHCP pool.

### 📍 3.5 DHCP Client Verification

Configure the end hosts to obtain their IP addresses dynamically using DHCP.

#### 🖥️ PC3 Verification

```bash
ip dhcp
```

Verify the assigned address:

```bash
show ip
```

Expected network:

```text
Network: 20.1.1.0/24
Gateway: 20.1.1.1
DHCP Server: 30.1.1.100
```

#### 🖥️ PC1 / PC2 Verification

Verify that the clients receive addresses from the:

```text
10.1.1.0/24
```

network with:

```text
Gateway: 10.1.1.1
DHCP Server: 30.1.1.100
```

### 🧪 End-to-End DHCP Validation

| Client | Client Network |  Relay Agent |  DHCP Server | Status |
| :----: | :------------: | :----------: | :----------: | :----: |
|   PC1  |  `10.1.1.0/24` |      R2      | `30.1.1.100` |    ✅   |
|   PC2  |  `10.1.1.0/24` |      R2      | `30.1.1.100` |    ✅   |
|   PC3  |  `20.1.1.0/24` |      R3      | `30.1.1.100` |    ✅   |
|   PC4  |  `30.1.1.0/24` | Not Required | `30.1.1.100` |    ✅   |

> **Note:** R4 does not require `ip helper-address` because the DHCP server (`30.1.1.100`) and PC4 are already on the same `30.1.1.0/24` LAN. The DHCP broadcast can reach the server directly without crossing a Layer 3 boundary.

### 🧠 Phase 3 Result

The centralized DHCP server successfully provides dynamic IP addressing to clients across multiple routed LANs.

The DHCP Relay Agent configured on **R2 and R3** enables DHCP broadcasts from remote client networks to reach the centralized DHCP server at **`30.1.1.100`**.

This demonstrates centralized IP address management across the multi-router OSPF network.

```

**Phase 3 title:** `🔹 Phase 3 — DHCP Relay Agent Configuration`  
**Main concept:** `DHCP Broadcast → Relay Agent → DHCP Server`
```
























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

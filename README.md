# Hierarchical Campus LAN Design

## LAN Design | Cisco Packet Tracer

---

## 📌 Project Overview

This project focuses on designing and implementing a small hierarchical campus Local Area Network (LAN) using Cisco Packet Tracer.

The network follows a two-tier hierarchical design consisting of an access layer and a distribution layer, with an edge router providing connectivity beyond the campus network.

The implementation demonstrates how network devices are selected, interconnected, configured and verified to establish reliable end-to-end communication.

## 🎯 Objectives

- Apply the access, distribution and core/edge layer model to a practical network topology.
- Select appropriate network devices based on their functionality and capabilities.
- Design and cable a hierarchical campus network.
- Configure basic device identification and IP addressing.
- Establish connectivity within a single-VLAN network.
- Verify end-to-end communication using connectivity tests.
- Observe packet forwarding using Packet Tracer Simulation Mode.
- Document network design decisions and troubleshooting procedures.

## 🏗️ Network Architecture

The network uses a two-tier hierarchical campus LAN design with a collapsed core/edge arrangement.

### Network Layers

**1. Access Layer**

Devices:
- AccessSW1
- AccessSW2

Responsibilities:
- Connect end devices such as computers to the network.
- Provide physical network access.
- Forward Ethernet frames toward the distribution layer.

**2. Distribution Layer**

Device:
- DistSwitch (Cisco 3560 Multilayer Switch)

Responsibilities:
- Aggregate connections from access switches.
- Provide Layer 3 switching capabilities.
- Support inter-VLAN routing in expanded network designs.

**3. Core / Edge Layer**

Device:
- EdgeRouter

Responsibilities:
- Provide connectivity between the campus network and external networks.
- Support communication with other networks or WAN connections.

## 🖥️ Network Topology

The topology consists of:

- 2 access switches
- 1 multilayer distribution switch
- 1 edge router
- 4 end-user PCs

Each access switch connects two PCs. Both access switches connect to the distribution switch, which connects to the edge router.

![Campus LAN Topology](Screenshots/campus-lan-topology.png)

## 🔌 Device Selection

| Network Layer | Device Model | Quantity |
|---|---|---:|
| Access | Cisco 2960 Switch | 2 |
| Distribution | Cisco 3560 Multilayer Switch | 1 |
| Core / Edge | Cisco 4321 Router | 1 |
| End Devices | PC-PT | 4 |

### Device Selection Considerations

- Port density and the number of connected devices.
- Layer 2 and Layer 3 capabilities.
- Uplink connectivity.
- Scalability and future expansion.
- Reliability and redundancy.
- Cost and management requirements.

## 🌐 IP Addressing Scheme

All end devices and network interfaces are configured within the same IPv4 subnet.

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC1 | FastEthernet0 | 192.168.10.11 | 255.255.255.0 |
| PC2 | FastEthernet0 | 192.168.10.12 | 255.255.255.0 |
| PC3 | FastEthernet0 | 192.168.10.13 | 255.255.255.0 |
| PC4 | FastEthernet0 | 192.168.10.14 | 255.255.255.0 |
| DistSwitch | VLAN 1 (SVI) | 192.168.10.1 | 255.255.255.0 |
| EdgeRouter | GigabitEthernet0/0 | 192.168.10.2 | 255.255.255.0 |

**Network Address:** 192.168.10.0/24

**Subnet Mask:** 255.255.255.0

## ⚙️ Implementation

### Part A – Device Placement

- Added two Cisco 2960 access switches.
- Added one Cisco 3560 multilayer distribution switch.
- Added one edge router.
- Connected four PCs to the access switches.
- Assigned appropriate device names.

### Part B – Network Cabling

Copper Straight-Through cables were used to establish connections between:

- PCs and access switches.
- Access switches and distribution switch.
- Distribution switch and edge router.

Physical connectivity was checked using Packet Tracer link-status indicators.

### Part C – Basic Device Configuration

Configured the following on network devices:

- Device hostnames.
- Enable secret passwords.
- Login banners.
- Basic interface configurations.
- IP addressing.
- Static access-port configurations for end devices.

The lab uses a single VLAN, so trunk configuration was not required.

### Part D – Connectivity Verification

End-to-end connectivity was verified using ICMP ping tests.

The following connectivity checks were performed:

- PC1 to PC3.
- PC1 to PC4.
- PCs to the DistSwitch VLAN 1 interface.
- PCs to the EdgeRouter interface.

### Part E – Simulation Mode

Packet Tracer Simulation Mode was used to observe packet forwarding between PC1 and PC4.

The packet forwarding path was:

PC1 → AccessSW1 → DistSwitch → AccessSW2 → PC4

Since both PCs belong to the same VLAN and IP subnet, Layer 3 routing is not required for this communication.

## 🔍 Verification Commands

The following Cisco IOS commands were used to inspect device configurations and network connectivity.

| Command | Purpose |
|---|---|
| `show ip interface brief` | Displays interface IP addresses and status |
| `show cdp neighbors` | Identifies directly connected Cisco devices |
| `show running-config` | Displays the current device configuration |
| `ping <destination-ip>` | Tests network connectivity |
| Packet Tracer Simulation Mode | Observes packet forwarding paths |

## 📊 Design Considerations and Analysis

### 1. Network Layer Responsibilities

- AccessSW1 and AccessSW2 represent the access layer.
- DistSwitch represents the distribution layer.
- EdgeRouter represents the core/edge connectivity device.

### 2. Why Use a Layer 3 Switch?

A Layer 3 switch provides both switching and routing capabilities. It can support inter-VLAN routing and provide efficient communication between different network segments.

### 3. Failure Domain Analysis

If AccessSW1 fails, PC1 and PC2 lose their network connectivity through that switch. PC3 and PC4 can continue communicating through AccessSW2.

Redundant switches and alternative uplink paths can help reduce the impact of failures.

### 4. Future Network Expansion

For a campus network with approximately 200 end devices and 10 access switches, possible improvements include:

- Introducing a dedicated core layer.
- Adding additional distribution switches.
- Implementing redundant uplinks.
- Using higher-speed uplinks such as 10 Gbps.
- Deploying PoE switches for IP phones and wireless access points.
- Introducing VLANs for departmental segmentation.
- Implementing link aggregation and network redundancy.

### 5. Hardware Selection Criteria

Important factors when selecting production network equipment include:

- Port density.
- PoE support.
- Uplink speed.
- Routing capabilities.
- Scalability.
- Reliability and redundancy.
- Management and security features.
- Cost.

### 6. Packet Forwarding and Layer 3 Processing

For communication between PC1 and PC4 within the same VLAN and IP subnet, frames are forwarded through the access and distribution switches.

If the PCs belong to different VLANs, Layer 3 processing is required at a routing-capable device such as the multilayer distribution switch.

## 📸 Project Screenshots

The following screenshots demonstrate the network implementation and verification.

1. Complete campus LAN topology.
2. Device and interface configurations.
3. Successful PC-to-PC ping results.
4. DistSwitch and EdgeRouter connectivity tests.
5. Packet Tracer Simulation Mode packet forwarding.

![Connectivity Verification](Screenshots/connectivity-verification.png)

![Simulation Mode](Screenshots/simulation-mode.png)

## 🧰 Technologies and Concepts

- Cisco Packet Tracer
- Hierarchical Network Design
- Campus LAN Architecture
- Cisco 2960 Switching
- Cisco 3560 Multilayer Switching
- IPv4 Addressing
- Ethernet Networking
- Layer 2 Switching
- Layer 3 Switching
- ICMP and Ping
- Network Troubleshooting
- Packet Tracer Simulation

## ✅ Conclusion

This laboratory exercise provided practical experience in designing and implementing a hierarchical campus LAN using Cisco Packet Tracer.

The implementation demonstrated the roles of access, distribution and edge devices, appropriate device selection, network cabling, IP addressing and basic device configuration.

Connectivity testing and Simulation Mode provided a better understanding of Ethernet frame forwarding and end-to-end communication within a single-VLAN network.

The exercise also highlighted the importance of scalability, redundancy, device capabilities and structured network design when developing campus network infrastructures.

---

*Networking Laboratory Project | BICT Undergraduate Portfolio*

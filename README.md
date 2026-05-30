<div align="center">

# 🎓 University Campus Area Network (UCAN)

### *A multi-site enterprise campus network — built & simulated in Cisco Packet Tracer*

![Packet Tracer](https://img.shields.io/badge/Cisco%20Packet%20Tracer-8.2.2-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![CCNA](https://img.shields.io/badge/Level-CCNA-00599C?style=for-the-badge)
![Routing](https://img.shields.io/badge/Routing-RIP%20v2-4CAF50?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-success?style=for-the-badge)

</div>

---

## 📖 Overview

**UCAN** models a real university with several departments spread across a **Main Campus**, a separate **Branch Campus**, and a **Cloud / data-centre** block — all connected over a WAN.

> 📁 **File:** `University Campus Area Network.pkt` &nbsp;·&nbsp; 🖥️ **Platform:** Cisco Packet Tracer 8.2.2

---

## 🎯 Why this network?

A university isn't one flat office — it has many departments (Admin, HR, Finance, IT, student labs) in different buildings, and often more than one campus. That makes it a textbook **Campus Area Network (CAN)**: bigger than a single LAN, but privately owned and contained within the institution rather than spread across cities like a WAN/ISP network. The goal of UCAN is to keep every department **separated and secure**, give them **automatic IP addressing**, and still let them all **talk to each other and to shared services**.

---

## 🗺️ Topology


The network is split into three routed sites — the **Main Campus** (Buildings A, B and C), the **Branch Campus** (Staff + Student-Lab), and the **Cloud** block hosting the servers — all joined by serial WAN links.

### 🔧 Why each device is there

- **🌐 Routers** sit at the edge of each site and do the job switches can't: routing between *different* networks. The Main Campus router routes between every departmental subnet, and the three routers (Main, Branch, Cloud) link the sites together over the WAN. They also hand out IP addresses via **DHCP** and run **RIP v2**, so each site automatically learns the routes to the others — no manual route entries.

- **🔀 Multilayer (Layer-3) switches** combine switching and routing in one box. They let heavy inter-VLAN traffic be routed locally at switch speed instead of pushing everything up to the router, keeping the core fast as the campus grows.

- **🔌 Access switches** (one per department) are where wired devices plug in. Each switch's ports are locked to that department's VLAN, and a single **trunk** link carries all VLANs back to the core. Switches are used instead of hubs because they forward traffic only to the intended port — separate collision domains and far better performance.

- **🗄️ Servers** (Web, FTP, Email) live in the Cloud / data-centre block so they can be centrally managed and reached by every department through the routed core.

---

## 🧩 Why VLANs?

Every department is placed in its own **VLAN** (virtual LAN). Instead of buying separate physical switches and cabling for each group, VLANs split one switched network into isolated logical networks:

| Benefit | What it means |
|---------|---------------|
| 🛡️ **Segmentation** | Finance and HR traffic stays separate from student labs |
| 📉 **Smaller broadcast domains** | A broadcast in one VLAN doesn't flood the whole campus |
| 🔐 **Security & control** | Traffic between VLANs is forced through the router — the natural place for access rules |

Because devices in different VLANs are on different subnets, **inter-VLAN routing** (router-on-a-stick: one router interface split into tagged sub-interfaces) lets departments still communicate when needed.

---

## 🌐 VLANs & IP Addressing

All subnets use `/24` (255.255.255.0). Each VLAN's gateway lives on the router and has its own DHCP pool.

### 🏛️ Main Campus

| Department | VLAN | Network | Gateway |
|------------|:----:|---------|---------|
| Administration | 10 | 192.168.1.0/24 | 192.168.1.1 |
| Human Resources | 20 | 192.168.2.0/24 | 192.168.2.1 |
| Finance | 30 | 192.168.3.0/24 | 192.168.3.1 |
| Business | 40 | 192.168.4.0/24 | 192.168.4.1 |
| E&C | 50 | 192.168.5.0/24 | 192.168.5.1 |
| A&D | 60 | 192.168.6.0/24 | 192.168.6.1 |
| Student Lab | 70 | 192.168.7.0/24 | 192.168.7.1 |
| IT | 80 | 192.168.8.0/24 | 192.168.8.1 |

### 🏢 Branch Campus

| Department | VLAN | Network | Gateway |
|------------|:----:|---------|---------|
| Staff | 90 | 192.168.9.0/24 | 192.168.9.1 |
| Student Lab | 100 | 192.168.10.0/24 | 192.168.10.1 |

---

## ▶️ How to open

1. Install **Cisco Packet Tracer 8.2.2** (or newer).
2. Open `University Campus Area Network.pkt`.
3. Wait for the link lights to turn green, then test:
   - 🟢 On a PC, run `ipconfig` to confirm a DHCP address was assigned.
   - 🔁 `ping` a device in another VLAN to test inter-VLAN routing.
   - 📡 `ping 20.0.0.2` (Email Server) to test WAN routing across sites.

---

<div align="center">

*Built with Cisco Packet Tracer · CCNA networking project*

</div>

# UCAN — University Campus Area Network 🎓

A **CCNA-level** project simulating a multi-campus University Campus Area Network in **Cisco Packet Tracer 8.2.2**. It demonstrates VLAN segmentation, inter-VLAN routing via router-on-a-stick, automatic addressing with DHCP, and WAN routing between campuses using RIPv2.

---

## 🎯 Project Goal

Connect multiple university campuses into one cohesive network — segmenting departments with VLANs, routing between them efficiently, and linking the campuses over a WAN.

---

## 🧩 Key Features

- **VLANs** — department/faculty segmentation within each campus
- **Router-on-a-stick** — inter-VLAN routing over a single trunk link
- **DHCP** — dynamic IP assignment to end devices
- **RIPv2 WAN routing** — routing between campuses across the WAN

---

## 🛠️ Tools Used

- **Cisco Packet Tracer 8.2.2**

---


## ▶️ How to Open

1. Open the `.pkt` file in **Cisco Packet Tracer** (8.2.2 or newer).
2. Inspect device configs via the CLI tab.
3. Run **Simulation mode** to follow packets across VLANs and campuses.

---

## 📌 Possible Improvements

- [ ] Migrate RIPv2 to OSPF for scalability
- [ ] Add redundant WAN links
- [ ] Add network security (ACLs, port security)

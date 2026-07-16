# TechVerse Solutions - Enterprise Network Design

A multi-branch enterprise network architecture designed, configured, and tested in Cisco Packet Tracer. The project implements dynamic routing, VLAN segmentation, and mutual route redistribution to integrate OSPF, EIGRP, and RIPv2 domains into a single, cohesive topology.

## 🌐 Topology Overview
The network connects a central Head Office hosting shared services (Web and DNS) with three geographically distributed branches:
* **Head Office (HQ):** Hosts the server farm on VLAN 10 (`10.1.10.0/24`) and uses Sub-interfaces (Router-on-a-Stick) for Inter-VLAN routing.
* **Branch 1 (OSPF):** Configured with OSPF Area 0 on LAN subnet `10.2.30.0/23`.
* **Branch 2 (EIGRP):** Configured with EIGRP AS 100 on LAN subnet `10.3.40.0/24`.
* **Branch 3 (RIPv2):** Configured with RIPv2 on LAN subnet `10.4.50.0/24`.

## 🛠️ Key Technical Features
* **Mutual Route Redistribution:** Configured on the core Autonomous System Boundary Router (**HQ-ASBR**) to enable communication across distinct OSPF, EIGRP, and RIPv2 dynamic boundaries.
* **VLAN Segmentation & Trunking:** Implemented on the switch level to isolate the server farm, minimizing broadcast storms while optimizing security.
* **Fail-Safe Static Routing:** Added default routes (`0.0.0.0/0`) on branch routers pointing to the HQ-ASBR as a robust fallback.

## 🧪 Verification & Results
All end-user devices (PCs) can successfully ping the internal server farm (`10.1.10.10` / `10.1.10.20`) with **0% packet loss**.

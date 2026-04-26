# Enterprise Healthcare Network Architecture

## 🏥 Executive Summary
Designed and simulated a comprehensive Zero-Trust network architecture for a multi-departmental healthcare facility. This project focuses on high availability, strict traffic segregation, and edge security using Cisco infrastructure. 

![High Level Architecture](network-design.pdf 0r enterprise-healthcare-network.jpg)
*Note: The diagram above represents the High-Level Logical Design (HLD). The physical topology inside the `.pkt` file includes additional redundancy and distribution-layer routing.*

## ⚙️ Core Technologies & Protocols
* **Routing:** Multi-Area OSPFv2 (Optimized with custom bandwidth metrics and Router IDs)
* **Security:** Standard/Extended Access Control Lists (ACLs), Port Security
* **Network Services:** Static NAT, DHCP, DNS, HTTP Server Configuration
* **Switching:** 802.1Q VLAN Trunking
* **Addressing:** Public/Private IPv4 Class B Subnetting with /30 PtP WAN links

## 🛡️ Security & Architecture Highlights
* **Network Segregation:** Configured isolated VLANs for `Medical_Staff`, `Administrative_Staff`, and `Accounts` to ensure strict broadcast domain separation and limit lateral movement.
* **Biomedical Isolation (Area 4):** Segmented critical imaging equipment (MRI/CT Scanners) into an isolated OSPF area to prevent unauthorized probing from general hospital endpoints.
* **Secure Server Farm (Area 2):** Implemented Static NAT for the centralized HTTP/DNS/DHCP server cluster, obfuscating private IP addresses from external subnets.
* **Access Control:** Deployed targeted ACLs to restrict web-service access from unauthorized zones (Area 5).

## 📂 Repository Contents
* `simulation/` : Contains the `.pkt` Cisco Packet Tracer file for the physical Low-Level Design (LLD).
* `configs/` : Raw `show running-config` exports for the core OSPF backbone routers demonstrating routing logic and subnetting.

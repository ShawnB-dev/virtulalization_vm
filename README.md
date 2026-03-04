# Virtualization & Network Simulation Lab  
A combined VirtualBox and Cisco Packet Tracer environment for hands‑on virtualization, routing, and firewall practice.

This lab demonstrates the creation of a small, multi‑environment network simulation using two complementary tools:

- **VirtualBox** for virtual machines and a pfSense firewall  
- **Cisco Packet Tracer** for router/switch topology simulation  

The goal is to build a reproducible, structured environment for practicing virtualization, firewalling, routing, and network design—mirroring the workflows used in real infrastructure and security teams.

---

## Lab Overview

This project contains two interconnected learning environments:

### Virtualization Environment (VirtualBox)
Used for:
- pfSense firewall installation and configuration  
- Server/client VM creation  
- NAT and Host‑Only networking  
- Basic routing and segmentation concepts  

### Network Simulation Environment (Cisco Packet Tracer)
Used for:
- Cisco router and switch topology  
- VLANs, subnets, and routing behavior  
- Conceptual modeling of internal networks behind a firewall  

These two environments do **not** directly connect, but together they represent the two halves of a typical enterprise network:

- **VirtualBox** = perimeter firewall + servers  
- **Packet Tracer** = internal switching/routing  

This dual‑environment approach demonstrates both virtualization skills and network engineering fundamentals.

---

## Architecture Summary

### VirtualBox Layer

```markdown
+------------------------------------------------+ |                VirtualBox Host                 | +------------------------------------------------+ |                         | pfSense VM                Server VM(s) | Host-Only LAN (10.0.0.0/24)
```

### Packet Tracer Layer

```markdown
[Router] --- [Switch] --- [PCs] --- [Switch] --- [Servers]
```

### Conceptual Relationship

```markdown
Internet → pfSense → Internal Network (simulated in Packet Tracer)
```


---

## Skills Demonstrated

- Virtual machine provisioning  
- VirtualBox networking (NAT, Host‑Only, adapters)  
- pfSense installation and interface assignment  
- Basic firewall configuration  
- Cisco routing and switching fundamentals  
- Network segmentation and IP addressing  
- Documentation and reproducibility  
- Bilingual technical communication (EN/JP)  

---

## Repository Structure
```markdown
docs/ screenshots/ configs/ packet_tracer/ scripts
```


Documentation is organized into numbered sections (English + Japanese), following the same structure as the RHEL hardening lab.

---

## Documentation

Full documentation is available in the `/docs` directory.

### English
- 01 Overview  
- 02 Architecture  
- 03 VirtualBox Setup  
- 04 pfSense Installation  
- 05 Packet Tracer Topology  
- 06 Network Integration  
- 07 Screenshots  
- 08 How to Reproduce  

### 日本語
- 01 概要  
- 02 アーキテクチャ  
- 03 VirtualBox セットアップ  
- 04 pfSense インストール  
- 05 Packet Tracer トポロジー  
- 06 ネットワーク統合  
- 07 スクリーンショット  
- 08 再現手順  

---

## VM Definitions (VirtualBox)

| VM Name | OS | CPU | RAM | Disk | Purpose |
|--------|-----|------|------|-------|----------|
| pfSense | pfSense CE | 2 | 2GB | 10GB | Firewall / Router |
| server01 | Linux/Windows | 2 | 2–4GB | 20GB | Test server |

---

## Packet Tracer Topology

The Packet Tracer environment includes:

- One router  
- One or more switches  
- Multiple PCs/servers  
- Optional VLAN segmentation  
- Static or dynamic routing  

Screenshots and `.pkt` files are included in the repo.

---

## Screenshots

All screenshots are stored in:

```markdown
/screenshots
```

They include:

- VirtualBox VM creation  
- Network adapter configuration  
- pfSense installation  
- Packet Tracer topology  
- Running VMs  

---

## How to Reproduce This Lab

A full reproduction guide is available in:
```markdown
docs/08-how-to-reproduce.md docs/08-再現手順.md
```


It includes:

- Required software  
- VM creation steps  
- pfSense installation  
- Packet Tracer topology setup  
- Validation steps  

---

## Future Improvements

- Add automation scripts for VM creation  
- Add VLAN segmentation in Packet Tracer  
- Add DHCP/DNS services behind pfSense  
- Integrate a small Linux server cluster  
- Add monitoring tools (Zabbix, Prometheus, etc.)  

---
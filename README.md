# Virtualization & Network Simulation Lab  
A combined VirtualBox and Cisco Packet Tracer environment for hands‑on virtualization, routing, and firewall practice.

This lab demonstrates the creation of a small, multi‑environment network simulation using two complementary tools:

- **VirtualBox** for virtual machines and a pfSense firewall  
- **Cisco Packet Tracer** for router/switch topology simulation  

The goal is to build a reproducible, structured environment for practicing virtualization, firewalling, routing, and network design—mirroring the workflows used in real infrastructure and security teams.

---

## Network Architecture / ネットワークアーキテクチャ (Conceptual)

```markdown
                     +----------------------+
                     |      Internet        |
                     +----------+-----------+
                                |
                                |
                     +----------v-----------+
                     |      pfSense         |
                     |  Firewall / Router   |
                     +----------+-----------+
                                |
                 VirtualBox LAN | 10.0.0.0/24
                                |
            +-------------------+-------------------+
            |                                       |
    +-------v-------+                       +-------v-------+
    |   RHEL VM     |                       |  (Optional)   |
    |  server01     |                       |  Additional   |
    | 10.0.0.x      |                       |   VMs         |
    +---------------+                       +---------------+

```
### Packet Tracer LAN (Simulated)
```markdown

                   +----------------------+
                   |      Router          |
                   | 192.168.1.1/24       |
                   +----------+-----------+
                              |
                              |
                     +--------v--------+
                     |     Switch      |
                     +--------+--------+
                              |
                +-------------+-------------+
                |                           |
        +-------v-------+           +-------v-------+
        |     PC1       |           |     PC2       |
        | 192.168.1.10  |           | 192.168.1.11  |
        +---------------+           +---------------+


```

## Documentation / ドキュメント

This project includes full English and Japanese documentation sets.

### English Documentation (docs/)
- [01 Overview](docs/01-overview.md)
- [02 Architecture](docs/02-architecture.md)
- [03 VirtualBox Setup](docs/03-virtualbox-setup.md)
- [04 pfSense Installation](docs/04-pfsense-installation.md)
- [05 Packet Tracer Topology](docs/05-packet-tracer-topology.md)
- [06 Network Integration](docs/06-network-integration.md)
- [07 Screenshots](docs/07-screenshots.md)
- [08 How to Reproduce](docs/08-how-to-reproduce.md)

### 日本語ドキュメント（jp-docs/）
- [01 概要](jp-docs/01-概要.md)
- [02 アーキテクチャ](jp-docs/02-アーキテクチャ.md)
- [03 VirtualBox セットアップ](jp-docs/03-VirtualBoxセットアップ.md)
- [04 pfSense インストール](jp-docs/04-pfSenseインストール.md)
- [05 Packet Tracer トポロジー](jp-docs/05-PacketTracerトポロジー.md)
- [06 ネットワーク統合](jp-docs/06-ネットワーク統合.md)
- [07 スクリーンショット](jp-docs/07-スクリーンショット.md)
- [08 再現手順](jp-docs/08-再現手順.md)

---

## Lab Overview / ラボの概要
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

## Architecture Summary / アーキテクチャの概要

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

## Skills Demonstrated / 実証されたスキル

### Virtualization & Systems
- VirtualBox VM provisioning  
- Host-Only and NAT networking  
- RHEL installation and configuration  
- pfSense firewall deployment  

### Networking
- IP addressing and subnetting  
- Routing fundamentals  
- Switch configuration and VLANs  
- LAN design and connectivity testing  

### Security & Infrastructure
- Firewall interface assignment  
- Perimeter network design  
- Segmentation concepts  

### Documentation & Communication
- Structured, reproducible lab documentation  
- Bilingual English/Japanese technical writing  
- Architecture diagrams and screenshot documentation  
- Clear repo organization for recruiter review  

---

## Repository Structure / リポジトリ構造
```markdown
docs/ screenshots/ configs/ packet_tracer/ scripts
```


Documentation is organized into numbered sections (English + Japanese), following the same structure as the RHEL hardening lab.

---

## Documentation / リポジトリ構造

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

## VM Definitions / VMの定義 (VirtualBox)

| VM Name | OS | CPU | RAM | Disk | Purpose |
|--------|-----|------|------|-------|----------|
| pfSense | pfSense CE | 2 | 2GB | 10GB | Firewall / Router |
| server01 | Linux/Windows | 2 | 2–4GB | 20GB | Test server |

---

## Packet Tracer Topology /パケットトレーサートポロジ

The Packet Tracer environment includes:

- One router  
- One or more switches  
- Multiple PCs/servers  
- Optional VLAN segmentation  
- Static or dynamic routing  

Screenshots and `.pkt` files are included in the repo.

---

## Screenshots / スクリーンショット

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

## How to Reproduce This Lab / このラボを再現する方法

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

## Future Improvements / 今後の改善点

- Add automation scripts for VM creation  
- Add VLAN segmentation in Packet Tracer  
- Add DHCP/DNS services behind pfSense  
- Integrate a small Linux server cluster  
- Add monitoring tools (Zabbix, Prometheus, etc.)  

---

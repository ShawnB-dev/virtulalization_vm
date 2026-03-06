# 01 Overview  

**日本語版はこちら →** [01-概要.md](../jp-docs/01-概要.md)


Virtualization & Network Simulation Lab

This project combines two separate but complementary environments, VirtualBox and Cisco Packet Tracer, to simulate the core components of a small enterprise network. Although the environments are not technically connected, they were built simultaneously to represent different layers of the same conceptual network design.

The VirtualBox environment focuses on virtualization fundamentals, pfSense firewall deployment, and basic server provisioning. The Packet Tracer environment focuses on Cisco routing and switching concepts, internal LAN design, and network behavior simulation.

Together, these labs demonstrate practical skills in virtualization, firewall configuration, network topology design, and documentation.

---

## Purpose of the Lab

- Build a reproducible virtualization environment using VirtualBox  
- Install and configure a pfSense firewall  
- Create a RHEL server VM for testing and internal services  
- Design and simulate a Cisco network topology using Packet Tracer  
- Practice routing, switching, segmentation, and IP addressing  
- Document the entire workflow in a structured, bilingual format  

---

## Why Two Separate Environments?

VirtualBox and Packet Tracer serve different roles:

- **VirtualBox** provides real virtual machines, a firewall, and OS‑level configuration.
- **Packet Tracer** provides a fast, visual, Cisco‑focused simulation environment for routers and switches.

By running both labs in parallel, you gain experience with:

- Virtualization  
- Firewalling  
- Routing  
- Switching  
- Network segmentation  
- Documentation and reproducibility  

This mirrors how real infrastructure and security teams design and test networks using multiple tools.

---

## Skills Demonstrated

- Virtual machine provisioning  
- VirtualBox networking (NAT, Host‑Only)  
- pfSense installation and interface assignment  
- RHEL server deployment  
- Cisco routing and switching fundamentals  
- IP addressing and subnetting  
- Network topology design  
- Technical documentation (EN/JP)  

---

## Documentation Structure

This lab uses a numbered documentation system for clarity and reproducibility:

```markdown

01-overview.md 
02-architecture.md 
03-virtualbox-setup.md 
04-pfsense-installation.md 
05-packet-tracer-topology.md 
06-network-integration.md 
07-screenshots.md 
08-how-to-reproduce.md
```

Japanese versions follow the same numbering.

---

## Related Repositories

This project is part of a broader portfolio that includes:

- RHEL Server Hardening Lab  
- Virtualization & Network Simulation Lab (this repo)  

Each project follows the same documentation style for consistency and professional presentation.
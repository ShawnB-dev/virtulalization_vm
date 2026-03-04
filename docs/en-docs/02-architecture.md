# 02 Architecture  
VirtualBox + Packet Tracer Combined Project

This project consists of two separate environments that together represent the major components of a small enterprise network. Although they do not directly connect, they conceptually form a complete network design:

- **VirtualBox** simulates the perimeter firewall and server layer.  
- **Packet Tracer** simulates the internal Cisco switching and routing layer.

---

## High-Level Conceptual Architecture
```markdown
            Internet
                |
            [pfSense]
                |
     -------------------------
     |                       |
VirtualBox LAN         (Conceptual) Internal LAN (Packet Tracer Simulation)
```

---

## VirtualBox Environment Architecture
```markdown
+------------------------------------------------+ |                VirtualBox Host                 | +------------------------------------------------+ |                         | pfSense VM                RHEL Server VM | Host-Only LAN (10.0.0.0/24)
```

### Components

- **pfSense VM**  
  - Acts as the firewall/router  
  - Provides WAN (NAT) and LAN (Host‑Only) interfaces  

- **RHEL Server VM**  
  - Used for testing, internal services, and OS‑level configuration  
  - Connected to the pfSense LAN  

---

## Packet Tracer Environment Architecture
```markdown
[Router] --- [Switch] --- [PCs] --- [Switch] --- [Servers]
```

### Components

- **Cisco Router**  
  - Provides routing between subnets  
  - Can simulate static or dynamic routing  

- **Cisco Switch(es)**  
  - Provide internal LAN connectivity  
  - Optional VLAN segmentation  

- **PCs/Servers**  
  - Represent internal hosts  
  - Used for connectivity testing  

---

## VM Definitions (VirtualBox)

| VM Name   | OS         | CPU | RAM  | Disk | Purpose              |
|-----------|------------|-----|------|-------|----------------------|
| pfSense   | pfSense CE | 2   | 2GB  | 10GB | Firewall / Router    |
| server01  | RHEL 9     | 2   | 2–4GB| 20GB | Internal test server |

---

## Network Addressing Summary

### VirtualBox LAN
- Network: `10.0.0.0/24`  
- pfSense LAN IP: `10.0.0.1`  
- RHEL Server: `10.0.0.x`  

### Packet Tracer LAN (example)
- Router LAN: `192.168.1.1/24`  
- PCs: `192.168.1.x`  
- Optional VLANs: `10`, `20`, `30`  

(Actual addressing may vary depending on your Packet Tracer design.)

---

## How the Two Labs Relate

Although VirtualBox and Packet Tracer are separate environments, they represent two halves of a typical enterprise network:

- **VirtualBox** = perimeter firewall + server infrastructure  
- **Packet Tracer** = internal switching/routing  

This dual‑lab approach demonstrates understanding of:

- Network segmentation  
- Layered network design  
- Firewall placement  
- Routing and switching fundamentals  
- Virtualization and OS‑level configuration  

---

## Next Steps

Continue to:

- 03 VirtualBox Setup  
- 04 pfSense Installation  
- 05 Packet Tracer Topology  

These documents provide detailed, step‑by‑step instructions for building each environment.



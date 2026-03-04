# 05 Packet Tracer Topology  
Cisco Routing and Switching Simulation

This section describes the Packet Tracer portion of the project. While the VirtualBox environment focuses on virtualization and firewalling, Packet Tracer provides a fast, visual environment for practicing Cisco routing, switching, and LAN design. Together, they form two halves of a single conceptual network project.

---

## Purpose of the Packet Tracer Lab

- Practice Cisco router and switch configuration  
- Build a small internal LAN topology  
- Explore routing behavior and IP addressing  
- Simulate host connectivity and traffic flow  
- Reinforce concepts that complement the VirtualBox/pfSense environment  

Packet Tracer is ideal for rapid prototyping and visualization of network behavior without needing physical Cisco hardware.

---

## Topology Overview

The topology used in this lab consists of:
```markdown
[Router] --- [Switch] --- [PC1] --- [Switch] --- [PC2]
```

This simple design allows you to practice:

- Router interface configuration  
- Switch port configuration  
- VLANs (optional)  
- IP addressing  
- Basic routing behavior  

---

## Device List

| Device Type | Quantity | Purpose |
|-------------|----------|---------|
| Router | 1 | Default gateway for internal LAN |
| Switch | 1–2 | LAN connectivity and segmentation |
| PCs | 2–3 | End hosts for testing connectivity |

---

## IP Addressing Plan

Example addressing used in this lab:

- Router LAN: `192.168.1.1/24`  
- PC1: `192.168.1.10/24`  
- PC2: `192.168.1.11/24`  
- Default gateway for all hosts: `192.168.1.1`  

(Your actual addressing may vary; update as needed.)

---

## Basic Router Configuration

Example commands:
```markdown
enable configure terminal interface g0/0 ip address 192.168.1.1 255.255.255.0 no shutdown
 exit
```

---

## Basic Switch Configuration
```markdown
enable configure terminal interface range f0/1 - 24 switchport mode access switchport access vlan 1 no shutdown exit
```
Optional VLAN example:

```markdown
vlan 10 name USERS exit interface f0/1 switchport access vlan 10
```

---

## Host Configuration

Each PC should be configured with:

- IP address  
- Subnet mask  
- Default gateway  

Example:

- IP: `192.168.1.10`  
- Mask: `255.255.255.0`  
- Gateway: `192.168.1.1`  

---

## Connectivity Testing

Use the Packet Tracer simulation tools or CLI pings:

```markdown
PC1 → ping 192.168.1.1 PC1 → ping 192.168.1.11
```

Expected results:

- All hosts can reach the router  
- All hosts can reach each other (same VLAN)  

---

## Screenshots

Screenshots of:

- Topology  
- Router configuration  
- Switch configuration  
- Host settings  

are included in `docs/07-screenshots.md`.

---

## Next Steps

Continue to:

- **06 Network Integration**  
- **07 Screenshots**  



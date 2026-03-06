# 06 Network Integration  

**日本語版はこちら →** [06-ネットワーク統合.md](../jp-docs/06-ネットワーク統合.md)


How VirtualBox and Packet Tracer Form One Conceptual Project

Although the VirtualBox and Packet Tracer environments are separate, they were built simultaneously to represent different layers of a single conceptual network. This document explains how the two labs relate and why this dual‑environment approach is valuable.

---

## Conceptual Network Model

The combined project models a typical enterprise network:
```markdown
Internet → pfSense Firewall → Internal LAN (Cisco Topology)
```

### VirtualBox Layer (Real VMs)
- pfSense firewall  
- RHEL server  
- Host‑Only LAN  

### Packet Tracer Layer (Simulated LAN)
- Cisco router  
- Switch(es)  
- PCs/servers  

The VirtualBox environment represents the **perimeter and server layer**, while Packet Tracer represents the **internal switching and routing layer**.

---

## Why Use Two Separate Environments?

### VirtualBox Strengths
- Real operating systems  
- Real firewall behavior  
- Real NICs and routing tables  
- OS‑level configuration  
- pfSense web interface and services  

### Packet Tracer Strengths
- Fast topology creation  
- Visual routing and switching  
- Cisco IOS practice  
- VLANs, STP, routing protocols  
- No hardware required  

Using both tools demonstrates a broader range of infrastructure skills than either tool alone.

---

## How the Layers Conceptually Connect

Even though the environments are not technically linked, they represent:

- **pfSense** as the WAN/LAN gateway  
- **Packet Tracer router** as the internal gateway  
- **Packet Tracer switches** as the access layer  
- **Packet Tracer PCs** as internal hosts  

This mirrors a real enterprise design:

```markdown
[Internet] | [Firewall / pfSense] | [Core Router / Packet Tracer] | [Switches] | [Hosts]
```


---

## Skills Demonstrated Through Integration

- Understanding of layered network design  
- Ability to configure both virtualized and simulated environments  
- Knowledge of firewall placement and segmentation  
- Familiarity with routing and switching fundamentals  
- Ability to document complex multi‑tool workflows  

---

## Next Steps

Continue to:

- **07 Screenshots**  
- **08 How to Reproduce**  
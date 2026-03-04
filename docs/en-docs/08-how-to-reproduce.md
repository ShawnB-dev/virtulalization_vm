# 08 How to Reproduce  
Step‑by‑Step Guide to Rebuilding the Lab

This document provides a complete, reproducible workflow for recreating the VirtualBox and Packet Tracer environments used in this project. Follow these steps to rebuild the lab from scratch.

---

## Requirements

### Software
- VirtualBox (latest version)
- VirtualBox Extension Pack (recommended)
- pfSense CE ISO
- RHEL ISO
- Cisco Packet Tracer (latest version)

### Hardware
- 8 GB RAM minimum (16 GB recommended)
- 40–60 GB free disk space
- CPU with virtualization support (Intel VT‑x / AMD‑V)

---

## Part 1 — VirtualBox Environment

### Step 1: Install VirtualBox
Download and install VirtualBox from the official website.

### Step 2: Create Host‑Only Network
1. Open **Tools → Network Manager**  
2. Create or verify a Host‑Only network:  
   - IP: `10.0.0.1`  
   - Mask: `255.255.255.0`  
   - DHCP: Disabled  

### Step 3: Create the pfSense VM
1. New VM → Name: `pfSense`  
2. OS: BSD → FreeBSD (64‑bit)  
3. CPU: 2  
4. RAM: 2 GB  
5. Disk: 10 GB  
6. Network:  
   - Adapter 1: NAT  
   - Adapter 2: Host‑Only  
7. Mount pfSense ISO  

### Step 4: Install pfSense
1. Boot the VM  
2. Select **Install pfSense**  
3. Accept defaults  
4. Reboot  
5. Assign interfaces  
6. Set LAN IP to `10.0.0.1/24`  

### Step 5: Create the RHEL Server VM
1. New VM → Name: `server01`  
2. OS: Linux → Red Hat (64‑bit)  
3. CPU: 2  
4. RAM: 2–4 GB  
5. Disk: 20 GB  
6. Network: Host‑Only  
7. Mount RHEL ISO  

### Step 6: Install RHEL
1. Boot the VM  
2. Follow installer prompts  
3. Assign static IP (optional):  
   - IP: `10.0.0.x`  
   - Gateway: `10.0.0.1`  

### Step 7: Validate Connectivity
From RHEL:
```markdown
ping 10.0.0.1
```

Expected: Successful replies.

---

## Part 2 — Packet Tracer Environment

### Step 1: Create the Topology
1. Add one router  
2. Add one or two switches  
3. Add two or more PCs  

### Step 2: Configure Router
Example:
```markdown
interface g0/0 ip address 192.168.1.1 255.255.255.0 no shutdown
```

### Step 3: Configure Switch(es)
Example:
```markdown
interface range f0/1 - 24 switchport mode access switchport access vlan 1
```

### Step 4: Configure PCs
Example:

- IP: `192.168.1.10`  
- Mask: `255.255.255.0`  
- Gateway: `192.168.1.1`  

### Step 5: Validate Connectivity
Use Packet Tracer’s simulation mode or CLI:
```markdown
ping 192.168.1.1 ping 192.168.1.11
```

Expected: Successful replies.

---

## Part 3 — Conceptual Integration

Although the environments are separate, they represent:

- VirtualBox → Perimeter firewall + server layer  
- Packet Tracer → Internal LAN + routing/switching layer  

This mirrors real enterprise network design.

---

## Troubleshooting

### pfSense LAN unreachable
- Verify Host‑Only adapter is enabled  
- Confirm LAN IP is correct  
- Check RHEL NIC configuration  

### Packet Tracer hosts cannot ping
- Verify router interface is up  
- Check PC gateway settings  
- Confirm switch ports are active  

---

## Completion

After completing both environments, this lab produces:

- A working VirtualBox firewall + server lab  
- A functional Cisco Packet Tracer LAN topology  
- A conceptual model of a full enterprise network  
- A reproducible, bilingual documentation set  

This completes the Virtualization & Network Simulation Lab.
# 03 VirtualBox Setup  
Preparing the Virtualization Environment

This section explains how to install VirtualBox, configure the host system, and create the virtual machines used in this lab. The VirtualBox environment provides the foundation for pfSense and the RHEL server, simulating the perimeter and server layers of a small enterprise network.

---

## Installing VirtualBox

VirtualBox can be installed on Windows, macOS, or Linux. Download the latest version from:

https://www.virtualbox.org/wiki/Downloads

Install both:

- VirtualBox  
- VirtualBox Extension Pack (recommended)

After installation, launch VirtualBox to begin creating the lab environment.

---

## Creating the pfSense VM

### VM Settings

| Setting | Value |
|--------|--------|
| Name | pfSense |
| OS Type | BSD |
| Version | FreeBSD (64‑bit) |
| CPU | 2 |
| RAM | 2 GB |
| Disk | 10 GB |
| Network Adapter 1 | NAT (WAN) |
| Network Adapter 2 | Host‑Only (LAN) |

### Steps

1. Click **New** → Name the VM `pfSense`.  
2. Select **BSD → FreeBSD (64‑bit)**.  
3. Assign **2 GB RAM** and **2 CPUs**.  
4. Create a **10 GB VDI disk**.  
5. Open **Settings → Network**:  
   - Adapter 1: **NAT**  
   - Adapter 2: **Host‑Only Adapter**  
6. Mount the pfSense ISO under **Storage → Optical Drive**.

Screenshots of these steps are included in `docs/07-screenshots.md`.

---

## Creating the RHEL Server VM

### VM Settings

| Setting | Value |
|--------|--------|
| Name | server01 |
| OS Type | Linux |
| Version | Red Hat (64‑bit) |
| CPU | 2 |
| RAM | 2–4 GB |
| Disk | 20 GB |
| Network Adapter | Host‑Only |

### Steps

1. Click **New** → Name the VM `server01`.  
2. Select **Linux → Red Hat (64‑bit)**.  
3. Assign **2–4 GB RAM** and **2 CPUs**.  
4. Create a **20 GB VDI disk**.  
5. Under **Network
6. Mount the RHEL ISO under **Storage**.

---

## Host‑Only Network Configuration

VirtualBox automatically creates a Host‑Only network (usually `vboxnet0`).  
Verify or configure it under:

**File → Tools → Network Manager → Host‑Only Networks**

Recommended settings:

- IPv4 Address: `10.0.0.1`
- IPv4 Mask: `255.255.255.0`
- DHCP: **Disabled** (pfSense will provide DHCP if desired)

This network will serve as the LAN for both pfSense and the RHEL server.

---

## Verifying the Environment

After creating both VMs:

- pfSense should have **two adapters** (NAT + Host‑Only).  
- RHEL should have **one adapter** (Host‑Only).  
- Both VMs should appear in the VirtualBox Manager.  
- Screenshots of the final configuration are included in the screenshots document.

---

## Next Steps

Proceed to:

- **04 pfSense Installation**  
- **05 Packet Tracer Topology**  

These documents explain how to install pfSense and build the Cisco topology used in the second half of the project.

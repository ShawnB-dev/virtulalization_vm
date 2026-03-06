# pfSense LAN Rules  

**日本語版はこちら →** [lan-ルール.md](../pfsense/lan-ルール.md)


Configuration Reference

This document describes the LAN interface firewall rules used in the VirtualBox environment.  
The LAN interface is assigned to the Host-Only network (`10.0.0.0/24`) and provides internal connectivity for the RHEL server.

---

## LAN Interface Summary

- **Interface:** LAN  
- **IP Address:** `10.0.0.1/24`  
- **Network:** Host-Only  
- **Purpose:** Internal network for server01 and future VMs  

---

## Firewall Rules

### 1. Allow LAN → Any (Default Allow Rule)

| Setting | Value |
|--------|--------|
| Action | Pass |
| Interface | LAN |
| Protocol | Any |
| Source | LAN net |
| Destination | Any |
| Description | Default allow LAN to any |

This rule allows internal hosts to reach pfSense, the host machine, and the internet (via NAT on WAN).

---

### 2. Allow LAN → pfSense WebGUI

| Setting | Value |
|--------|--------|
| Action | Pass |
| Protocol | TCP |
| Source | LAN net |
| Destination | LAN address |
| Port | 443 |
| Description | Allow access to pfSense WebGUI |

---

### 3. Allow LAN → DNS

| Setting | Value |
|--------|--------|
| Action | Pass |
| Protocol | TCP/UDP |
| Source | LAN net |
| Destination | LAN address |
| Port | 53 |
| Description | Allow DNS queries to pfSense |

---

## Notes

- LAN is considered a **trusted** network in this lab.  
- Additional segmentation rules can be added later if more VMs are introduced.  
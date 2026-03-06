# pfSense WAN Rules  

**日本語版はこちら →** [wan-ルール.md](../pfsense/wan-ルール.md)

Configuration Reference

This document describes the WAN interface firewall rules used in the VirtualBox environment.  
The WAN interface receives a NAT-assigned IP from VirtualBox and is considered untrusted.

---

## WAN Interface Summary

- **Interface:** WAN  
- **IP Assignment:** DHCP (VirtualBox NAT)  
- **Purpose:** Outbound internet access for pfSense and LAN hosts  

---

## Firewall Rules

### 1. Block All Inbound (Default)

| Setting | Value |
|--------|--------|
| Action | Block |
| Interface | WAN |
| Protocol | Any |
| Source | Any |
| Destination | WAN address |
| Description | Default block inbound WAN traffic |

This is pfSense’s default security posture and is kept in place.

---

### 2. Allow Outbound WAN Traffic (Automatic NAT)

Outbound traffic is permitted automatically by pfSense’s default NAT rules:

- LAN → WAN is allowed  
- WAN → LAN is blocked unless explicitly allowed  

No additional WAN rules are required for this lab.

---

## Notes

- No port forwarding is configured.  
- No inbound services are exposed to the host or internet.  
- This configuration mirrors a typical secure perimeter firewall.  
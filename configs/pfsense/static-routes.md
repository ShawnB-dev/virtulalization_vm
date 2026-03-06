# pfSense Static Routes  

**日本語版はこちら →** [スタティックルート.md](../pfsense/スタティックルート.md)


Configuration Reference

This lab does not require static routes for basic operation, but this document defines the structure and provides examples for future expansion.

---

## Current Static Route Configuration

There are **no static routes configured** in this environment.

pfSense handles:

- WAN routing via DHCP default gateway  
- LAN routing directly (connected network)  

---

## Example Static Route (Not Implemented)

If an additional internal network were added (e.g., `192.168.20.0/24` behind another router), a static route would look like:

| Setting | Value |
|--------|--------|
| Destination Network | `192.168.20.0/24` |
| Gateway | `10.0.0.2` |
| Interface | LAN |
| Description | Route to secondary internal network |

---

## Notes

- Static routes are only needed when pfSense is not the default gateway for a network.  
- This lab uses a simple single-LAN design, so no routes are required.  




Destination: 192.168.20.0/24
Gateway: 192.168.10.2

Destination: 192.168.30.0/24
Gateway: 192.168.10.2
# Server Network Configuration  

**日本語版はこちら →** [サーバーネットワーク設定.md](../vm/サーバーネットワーク設定.md)

RHEL Server Network Settings

This document describes the network configuration for the RHEL server (`server01`) in the VirtualBox environment.

---

## Network Interface Summary

- **Interface:** `ens18` (may vary depending on VirtualBox version)
- **Connection:** Host-Only Adapter
- **Network:** `10.0.0.0/24`
- **Gateway:** pfSense LAN (`10.0.0.1`)

---

## Static IP Configuration (Recommended)

Edit:
```markdown
/etc/sysconfig/network-scripts/ifcfg-ens18
```

Example configuration:
```markdown
TYPE=Ethernet BOOTPROTO=none NAME=ens18 DEVICE=ens18 ONBOOT=yes IPADDR=10.0.0.10 PREFIX=24 GATEWAY=10.0.0.1 DNS1=10.0.0.1 DNS2=8.8.8.8
```

Apply changes:
```markdown
sudo nmcli connection 
reload sudo systemctl restart NetworkManager
```
---
## Verification
```markdown
ping 10.0.0.1      # pfSense LAN ping 8.8.8.8       # Internet (via NAT)
```


Expected results:

- RHEL → pfSense reachable  
- RHEL → Internet reachable  

---

## Notes

- DHCP can be used if pfSense DHCP is enabled, but static IP is preferred for lab consistency.  
- DNS can be pointed to pfSense or a public resolver.  

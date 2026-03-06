# Client Network Configuration 

**日本語版はこちら →** [クライアントネットワーク設定.md](../vm/クライアントネットワーク設定.md)

Network Settings for Client Hosts

This document describes the network configuration used for client hosts in the Packet Tracer environment.

---

## PC1 Configuration

| Setting | Value |
|--------|--------|
| IP Address | `192.168.1.10` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `192.168.1.1` |
| DNS Server | (Optional) `8.8.8.8` |

---

## PC2 Configuration

| Setting | Value |
|--------|--------|
| IP Address | `192.168.1.11` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `192.168.1.1` |
| DNS Server | (Optional) `8.8.8.8` |

---

## Notes

- All clients reside in VLAN 1 unless otherwise configured.  
- Gateway (`192.168.1.1`) is provided by the Packet Tracer router.  
- DNS is optional for this lab unless internet simulation is added.  
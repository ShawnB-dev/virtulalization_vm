# Switch Running Configuration 

**日本語版はこちら →** [スイッチランニングコンフィグ.md](../cisco/スイッチランニングコンフィグ.md)


Cisco Packet Tracer – Switch Configuration Reference

This document contains the actual running configuration used on the Packet Tracer switch in this lab.  
The switch provides VLAN segmentation and a trunk uplink to the router.

---

## Device Overview

- **Hostname:** Switch1  
- **VLANs:** 10 (SERVERS), 20 (CLIENTS), 30 (MGMT)  
- **Trunk Port:** G0/1  
- **Access Ports:** G0/2, G0/3, G0/4  

---

## Running Configuration (Actual)
```markdown
hostname Switch1
vlan 10 name SERVERS
vlan 20 name CLIENTS
vlan 30 name MGMT
interface GigabitEthernet0/1 switchport mode trunk switchport trunk allowed vlan 10,20,30
interface GigabitEthernet0/2 switchport mode access switchport access vlan 10
interface GigabitEthernet0/3 switchport mode access switchport access vlan 20
interface GigabitEthernet0/4 switchport mode access switchport access vlan 30
```

---

## Notes

- G0/1 is the trunk uplink to Router1.  
- Access ports map directly to VLANs 10, 20, and 30.  
- VLAN names match typical enterprise naming conventions.  

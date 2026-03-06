# Router Running Configuration  

**日本語版はこちら →** [ルーターランニングコンフィグ.md](../cisco/ルーターランニングコンフィグ.md)


Cisco Packet Tracer – Router Configuration Reference

This document contains the actual running configuration used on the Packet Tracer router in this lab.  
The router performs inter-VLAN routing using subinterfaces and provides DHCP services for three VLANs.

---

## Device Overview

- **Hostname:** Router1  
- **Purpose:** Inter-VLAN routing + DHCP  
- **Trunk Port:** G0/1  
- **Access Network:** VLAN 10, 20, 30  

---

## Running Configuration (Actual)
```markdown
hostname Router1
interface GigabitEthernet0/0 ip address 192.168.10.2 255.255.255.0 no shutdown
interface GigabitEthernet0/1 no shutdown
interface GigabitEthernet0/1.10 encapsulation dot1Q 10 ip address 192.168.10.254 255.255.255.0
interface GigabitEthernet0/1.20 encapsulation dot1Q 20 ip address 192.168.20.254 255.255.255.0
interface GigabitEthernet0/1.30 encapsulation dot1Q 30 ip address 192.168.30.254 255.255.255.0
ip dhcp pool VLAN10 network 192.168.10.0 255.255.255.0 default-router 192.168.10.254
ip dhcp pool VLAN20 network 192.168.20.0 255.255.255.0 default-router 192.168.20.254
ip dhcp pool VLAN30 network 192.168.30.0 255.255.255.0 default-router 192.168.30.254
ip route 0.0.0.0 0.0.0.0 192.168.10.1
```

---

## Notes

- G0/1 is configured as a trunk carrying VLANs 10, 20, and 30.  
- Router-on-a-stick design enables inter-VLAN routing.  
- DHCP pools match each VLAN’s subnet.  
- Default route points to `192.168.10.1` (upstream gateway).  
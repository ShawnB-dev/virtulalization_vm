# Virtualization Lab Project

This project simulates a small enterprise network using VirtualBox. It includes a router/firewall VM, a server VM, and a client VM connected through an internal network. The goal is to demonstrate virtualization, networking, segmentation, and system administration skills.

# プロジェクト概要（日本語）
本プロジェクトでは、Cisco IOS を用いた Router‑on‑a‑Stick 構成による VLAN 間ルーティング環境を構築しました。
3つの VLAN（サーバー、クライアント、管理）を適切に分離し、DHCP による IP アドレス割り当て、802.1Q トランク、サブインターフェース設定を実装しています。
本構成は、中小規模企業ネットワークで一般的に採用される設計であり、L2/L3 の基礎からトラブルシューティングまで幅広いスキルを実証しています。


## 1. Lab Topology

A three-VLAN enterprise-style network.
VLAN10 (Servers)
VLAN20 (Clients)
VLAN30 (Management)
All connect to a Layer 2 switch via access ports.

A single trunk line carries all VLANs to the router, where subinterfaces provide inter-VLAN routing and DHCP services.
Each PC receives a VLAN-specific IP and gateway, enabling controlled segmentation with full routed connectivity.

## 2. Virtual Machines

- Router: pfSense or AlmaLinux
- Server: RHEL 10 or Ubuntu Server
- Client: Windows 10 or Linux Desktop
- Simulation agent: Cisco Packet Tracer

## 3. Networks

- NAT (Internet access)
- Internal LAN
- Three VLANs (Servers, Clients, Management)
    - DHCP pools per VLAN
    - 802.1Q trunking between switch and router
    - Access ports mapped to VLANs
    - End-to-end connectivity
- Future addition: Host-only network
- Future addition: DMZ

## Cisco Networking Integration

To complement the pfSense firewall, I added a Cisco router and switch segment to simulate a realistic enterprise LAN environment. This demonstrates VLAN segmentation, inter-VLAN routing, DHCP, ACLs, and Cisco IOS configuration.

### Cisco Topology


### Cisco Router Configuration
hostname Router1

interface GigabitEthernet0/0
 ip address 192.168.10.2 255.255.255.0
 no shutdown

**interface** GigabitEthernet0/1
 no shutdown

**interface** GigabitEthernet0/1.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0

**interface** GigabitEthernet0/1.20
 encapsulation dot1Q 20
 ip address 192.168.20.254 255.255.255.0

**interface** GigabitEthernet0/1.30
 encapsulation dot1Q 30
 ip address 192.168.30.254 255.255.255.0

ip dhcp pool VLAN10
 network 192.168.10.0 255.255.255.0
 **default**-router 192.168.10.254

ip dhcp pool VLAN20
 network 192.168.20.0 255.255.255.0
 **default**-router 192.168.20.254

ip dhcp pool VLAN30
 network 192.168.30.0 255.255.255.0
 **default**-router 192.168.30.254

ip route 0.0.0.0 0.0.0.0 192.168.10.1

### Cisco Switch Configuration
hostname Switch1

vlan 10
 name SERVERS

vlan 20
 name CLIENTS

vlan 30
 name MGMT

**interface** GigabitEthernet0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30

**interface** GigabitEthernet0/2
 switchport mode access
 switchport access vlan 10

**interface** GigabitEthernet0/3
 switchport mode access
 switchport access vlan 20

**interface** GigabitEthernet0/4
 switchport mode access
 switchport access vlan 30

### Connectivity Tests



- Ping from VLAN 10 → pfSense
- Ping from VLAN 20 → Internet
- Traceroute from client → pfSense → WAN

# From Server VM (VLAN 10)
ping 192.168.10.254   
ping 192.168.10.1     
ping 8.8.8.8          

# From Client VM (VLAN 20)
ping 192.168.20.254
ping 192.168.10.1
ping 8.8.8.8

# From Server VM (VLAN 10)
ping 192.168.10.254 
ping 192.168.10.1     
ping 8.8.8.8        

# From Management VM (VLAN 30)
ping 192.168.20.254
ping 192.168.10.1
ping 8.8.8.8

## 4. Configuration Steps

Destination: 192.168.20.0/24
Gateway: 192.168.10.2

Destination: 192.168.30.0/24
Gateway: 192.168.10.2

## 5. Screenshots

[Cisco VLAN Topology](screenshots/cisco/ciscovlantopology.png)

## 6. Lessons Learned

This lab included real-world troubleshooting steps:

- Correcting misaligned switchport assignments
- Verifying physical connectivity
- Ensuring proper 802.1Q encapsulation
- Fixing dhcp default-router mismatches
- Validating VLAN membership and trunk configuration

Miscellaneous:

- *VLAN segmentation requires precise switchport mapping*
    Even a single misaligned access port can cause DHCP leaks, incorrect gateways, or complete loss of connectivity.
- *Router-on-a-stick configuration depends on correct 802.1Q encapsulation*
    A correct IP with the wrong VLAN tag silently breaks routing.
- *DHCP pools must align with gateway assignments*
    The **default-router** value determines the gateway clients receive. Swapped gateways will result in swapped routing behavior.
- *Packet Tracer has a few limitations*
    Some commands (ex. **show interfaces trunk**) may not display expected output, even when the configuration is enabled and correct.

# Troubleshooting Journey

- Initial symptoms
    - PCs received IP addresses from the wrong VLAN
    - Gateways were swapped
    - One PC showed "Not connected"
- Investigation steps
    - Verified VLAN assignments with **show vlan brief**
    - Checked switchport status with **show interfaces status**
    - Confirmed router subinterfaces and encapsulation
    - Inspected DHCP pools for mismatched gateways
    - Validated physical cabling and NIC status in Packet Tracer
- Root causes identified
    - Misaligned switchport connections (PCs plugged into wrong ports)
    - DHCP pools had correct networks but *incorrect default-router values*
    - Packet Tracer's limited IOS output caused confusion (ex. missing trunk display)
- Resolutions
    - Corrected switchport VLAN assignments
    - Repaired DHCP pool gateway values
    - Reconnected PCs to the correct switch ports
    - Renewed DHCP leases and validated routing
- Final Verification
    - All PCs received correct IPs and gateways
    - All VLANs routed successfully
    - Trunking functioned correctly despite Packet Tracer's limited reporting
    - Full inter-VLAN connectivity confirmed with TTL=225 pings

## 7. Future Improvements

- Host-only network
- Controlled access
- DMZ implementation
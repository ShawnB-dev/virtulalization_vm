# Virtualization Lab Project

This project simulates a small enterprise network using VirtualBox. It includes a router/firewall VM, a server VM, and a client VM connected through an internal network. The goal is to demonstrate virtualization, networking, segmentation, and system administration skills.

## 1. Lab Topology

(Insert diagram from network-diagrams folder)

## 2. Virtual Machines

- Router: pfSense or AlmaLinux
- Server: RHEL 10 or Ubuntu Server
- Client: Windows 10 or Linux Desktop

## 3. Networks

- NAT (Internet access)
- Internal LAN
- Optional: Host-only network
- Optional: DMZ

## Cisco Networking Integration

To complement the pfSense firewall, I added a Cisco router and switch segment to simulate a realistic enterprise LAN environment. This demonstrates VLAN segmentation, inter-VLAN routing, DHCP, ACLs, and Cisco IOS configuration.

### Cisco Topology
pfSense LAN (192.168.10.1/24)
        |
Cisco Router G0/0 (192.168.10.2)
        |
Cisco Router G0/1 (Trunk)
        |
Cisco Switch
   |        |        |
VLAN 10  VLAN 20  VLAN 30
Server   Client   Mgmt

### Cisco Router Configuration
hostname Router1

interface GigabitEthernet0/0
 ip address 192.168.10.2 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 no shutdown

interface GigabitEthernet0/1.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0

interface GigabitEthernet0/1.20
 encapsulation dot1Q 20
 ip address 192.168.20.254 255.255.255.0

interface GigabitEthernet0/1.30
 encapsulation dot1Q 30
 ip address 192.168.30.254 255.255.255.0

ip dhcp pool VLAN10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.254

ip dhcp pool VLAN20
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.254

ip dhcp pool VLAN30
 network 192.168.30.0 255.255.255.0
 default-router 192.168.30.254

ip route 0.0.0.0 0.0.0.0 192.168.10.1

### Cisco Switch Configuration
hostname Switch1

vlan 10
 name SERVERS

vlan 20
 name CLIENTS

vlan 30
 name MGMT

interface GigabitEthernet0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30

interface GigabitEthernet0/2
 switchport mode access
 switchport access vlan 10

interface GigabitEthernet0/3
 switchport mode access
 switchport access vlan 20

interface GigabitEthernet0/4
 switchport mode access
 switchport access vlan 30

### Connectivity Tests
- Ping from VLAN 10 → pfSense
- Ping from VLAN 20 → Internet
- Traceroute from client → pfSense → WAN
# From Server VM (VLAN 10)
ping 192.168.10.254   # Cisco router
ping 192.168.10.1     # pfSense
ping 8.8.8.8          # Internet

# From Client VM (VLAN 20)
ping 192.168.20.254
ping 192.168.10.1
ping google.com

## 4. Configuration Steps

Destination: 192.168.20.0/24
Gateway: 192.168.10.2

Destination: 192.168.30.0/24
Gateway: 192.168.10.2

## 5. Screenshots

(You will add these as you go)

## 6. Lessons Learned

(To be filled at the end)

## 7. Future Improvements

(To be filled at the end)
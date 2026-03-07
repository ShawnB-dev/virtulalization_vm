# English Documentation Index (en-docs)

This folder contains the full English documentation set for the Virtualization & Network Simulation Lab.  
All documents follow a consistent numbering system and are mirrored in Japanese under `/jp-docs`.

---

## Main Documentation

### 01-overview.md  
Project overview, goals, and learning outcomes.

### 02-architecture.md  
Conceptual architecture combining VirtualBox and Packet Tracer.

### 03-virtualbox-setup.md  
VirtualBox installation, Host-Only network configuration, and VM creation.

### 04-pfsense-installation.md  
pfSense installation, interface assignment, and initial setup.

### 05-packettracer-topology.md  
Cisco router/switch topology and LAN configuration in Packet Tracer.

### 06-network-integration.md  
How VirtualBox and Packet Tracer form a unified conceptual network.

### 07-screenshots.md  
Packet Tracer and pfSense screenshots.

### 08-how-to-reproduce.md  
Complete step-by-step instructions to rebuild the entire lab.

---

## pfSense Configuration Documents

### lan-rules.md  
Firewall rules for the LAN interface.

### wan-rules.md  
Firewall rules for the WAN interface.

### static-routes.md  
Static route configuration (none required for this lab).

---

## VM Network Configuration

### client-network-config.md  
Network settings for Packet Tracer client hosts.

### server-network-config.md  
Network settings for the RHEL server in VirtualBox.

---

## Cisco Device Configurations

### router-running-config.md  
Actual running configuration for Router1 (router-on-a-stick + DHCP).

### switch-running-config.md  
Actual running configuration for Switch1 (VLANs + trunk + access ports).

---

## Directory Structure

```markdown
docs/ 
│ 
├── 00-en-docs-index.md 
├── 01-overview.md 
├── 02-architecture.md 
├── 03-virtualbox-setup.md 
├── 04-pfsense-installation.md 
├── 05-packettracer-topology.md 
├── 06-network-integration.md 
├── 07-screenshots.md 
└── 08-how-to-reproduce.md

pfsense 
│ 
├── lan-rules.md 
├── wan-rules.md 
└── static-routes.md 

vm 
│ 
├── client-network-config.md 
└── server-network-config.md 

cisco
│  
├── router-running-config.md 
└── switch-running-config.m
```


Each English document includes a link to its Japanese counterpart.


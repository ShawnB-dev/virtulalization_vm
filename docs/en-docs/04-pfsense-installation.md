# 04 pfSense Installation  
Firewall and Router Setup in VirtualBox

pfSense acts as the perimeter firewall in this lab’s VirtualBox environment. This document explains how to install pfSense, configure its interfaces, and prepare it for use with the RHEL server VM.

---

## Downloading the pfSense ISO

Download the latest pfSense Community Edition ISO from:

https://www.pfsense.org/download/

Recommended options:

- Architecture: **AMD64**
- Installer: **USB Memstick / ISO**
- Console: **VGA**
- Mirror: Choose the closest region

Save the ISO and mount it in the pfSense VM’s virtual optical drive.

---

## Booting the Installer

1. Start the **pfSense** VM.  
2. At the boot menu, select **Install pfSense**.  
3. Accept the default keymap.  
4. Choose **Auto (ZFS)** or **UFS** (either is fine for lab use).  
5. Confirm disk formatting.

The installation will complete and prompt for a reboot.

---

## Initial Console Configuration

After rebooting, pfSense will detect two interfaces:

- **WAN** (NAT adapter)  
- **LAN** (Host‑Only adapter)  

pfSense will automatically assign:

- WAN: DHCP from VirtualBox NAT  
- LAN: `192.168.1.1/24` (default)

You may keep the default LAN network or change it to match your lab design.

Recommended for consistency:

- LAN IP: `10.0.0.1/24`

To change it:

1. Select option **2) Set interface IP address**.  
2. Choose **LAN**.  
3. Enter: `10.0.0.1`  
4. Subnet mask: `24`  
5. No upstream gateway.  
6. Enable DHCP server? Optional.  
7. Do not revert to HTTP; keep HTTPS.

---

## Accessing the Web Interface

From the RHEL server (once installed), or from the host machine:

Open a browser and navigate to:
```markdown
https://10.0.0.1 (10.0.0.1 in Bing)
```


Default credentials:

- Username: `admin`
- Password: `pfsense`

You will be prompted to run the setup wizard.

---

## Basic Setup Wizard

Recommended settings:

- Hostname: `pfsense`
- Domain: `local.lan`
- DNS servers: Use public DNS or leave blank
- WAN: DHCP (default)
- LAN: `10.0.0.1/24`
- Admin password: Set a secure password

After completing the wizard, pfSense will reload its configuration.

---

## Verifying Connectivity

From the pfSense console:
```markdown
ping 8.8.8.8
```


From the RHEL server (after installation):
```markdown
ping 10.0.0.1
```

Expected results:

- pfSense can reach the internet via NAT  
- RHEL can reach pfSense via Host‑Only LAN  

---

## Screenshots

Screenshots of:

- Installer  
- Interface assignment  
- Setup wizard  
- Dashboard  

are included in `docs/07-screenshots.md`.

---

## Next Steps

Continue to:

- **05 Packet Tracer Topology**  
- **06 Network Integration**  

These documents explain how the Cisco topology was built and how it conceptually relates to the VirtualBox environment.

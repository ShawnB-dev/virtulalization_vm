1: **Install Cisco Packet Tracer**
This project was created using Cisco Packet Tracer 8.0
Download the latest verstion from Cisco Networking Academy if you don't already have it.

2. **Download the .pkt file**
Clone the repository or download the project file directly:
**virtualization_lab_packet_tracer.pkt**

3. **Open the file in Packet Tracer**
- Launch Cisco Packet Tracer
- Go to **File > Open**
- Select the **.pkt** file from your local machine.

The full topology will load, including the switch, router, VLANs, PCs and all configurations.

4. **Explore the network**
You can:
- Inspect device configurations via the CLI
- Test inter-VLAN connectivity
- Review DHCP behavior
- Modify or extend the design (ex. ACLs, additional VLANs, redundancy)

5. **Optional: Reset the DHCP leases**
If you want to re-test the DHCP behavior:
- Open each PC
- Go to **Desktop > IP Configuration**
- Switch from DHCP > Static > DHCP
This will force a fresh lease request from the router.
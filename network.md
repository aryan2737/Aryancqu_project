# Network Design
This section gives the detailed network design.

[Assumptions](#assumptions) | [Network Design Diagrams and Justifications](#network-design-diagrams-and-justifications) | [WiFi Design](#wifi-design) | [Address Allocations](#address-allocations) | [Recommended Hardware](#recommended-hardware) | [Plan](./plan.md) | [Cloud Services](./cloud.md) | [Security](./security.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

## Assumptions

The scenario given is for Truelec company but it does not specific all the operational details which is why some assumptions are made which are explained below. 
-	The headquarters for the Truelec is assumed to be located at the Melbourne which will be used to host main servers. 
-	For the branch offices, the organization branches will be in Perth, Brisbane and Sydney. 
-	It is also assumed that at the headquarters, there will be 60 to 70 staff members who will be working at Melbourne. These staff members are abbreviated as management, administration and IT Personnel staff. 
-	Across the branch offices, it is assumed that each branch office i.e. Brisbane and Perth will offer support to approximately 15 to 30 staff members. 


## Network Design Diagrams and Justifications

The logical network diagram for Truelec company is following Cisco’s hierarchal design approach to create network in the top-down structure. 

![Truelec Network Diagram – HQ and Branches](Images/truelec-HQ-Branches.jpeg)

The above attached network design is showing Truelec logical network structure that adheres to the Cisco’s hierarchal design approach. The main headquarters is in the Melbourne and at the WAN area, the ISP 1 and ISP 2 are interconnected via redundant links. To form the external WAN connections, the use of the MPLS/VPN tunnels have been done that offers security, reliability and availability, minimizing the risk of external cyber-attacks. By going from top to down, the routers are connecting to the firewalls which are also connected in redundant structure to ensure only legitimate traffic enters the network. Then the main core routers are configured and then multi-layer switches for routing purposes, WAN connections and proper IP addressing. For the server areas, the VLAN 40 is assigned where the web, HR, accounting, CRM and backup servers are configured in the DMZ zone. Also, the layer 2 switch is used to connect wired LAN workstations, a wireless router for VLAN 20 and 30 with different SSIDs as Truelec HQ and Truelec Guest. 
The branch office at Perth with 35 staff members is connected to the headquarters via the MPLS/VPN tunnels for securing WAN links. The router is configured on the main area that connects the layer 2 switch which connects servers at VLAN 40, security systems at VLAN 50, workstations at VLAN 10, and Wi-Fi areas at VLAN 30 and VLAN 20. The similar structure is followed for the Brisbane branch office also which accommodates 25 staff members. The VLAN configuration is done as VLAN 40 for servers, VLAN 10 for wired LAN workstations, VLAN 20 and VLAN 30 for wireless SSIDs. 

## WiFi Design

The wireless network design is derived from the logical network design which is given below showing all the wireless connections established. 

**HQ Wi-Fi**

![Truelec Network Diagram – HQ and Branches](Images/truelec-wifi-hq.png)

In the headquarters Wi-Fi design, the Cisco Catalyst 2960X-24 switches are used which connects to the wireless routers. The two wireless routers are connected where the first one is for the staff members and the second one is for the guests. The SSID set for the staff members is Truelec HQ with VLAN 20, operating over the WPA3 and 5 GHZ of medium. For the second, the SSID is Truelec Guest, which connects to the VLAN 30 and is using WPA3 protocol and remains isolated from other networks.

**Branches Wi-Fi**
![Truelec Network Diagram – HQ and Branches](Images/truelec-wifi-branches.png)

For the branches also, the wireless routers are used which connects to the guest and the staff members with different SSIDs across the different VLANs. VLAN 20 and VLAN 30 on the Perth office uses staff and guest access points whilst the VLAN 20 and VLAN 30 on the Brisbane also uses the guest and staff SSIDs. 


## Address Allocations

## Headquarters – Melbourne (70 Staff)

| VLAN | Purpose | Subnet | Gateway | Key IP Assignments |
|------|--------|--------|---------|-------------------|
| 10 | Wired LAN Workstations | 37.10.0.0/24 | 37.10.0.1 | User PCs (DHCP) |
| 20 | WiFi Staff | 37.10.1.0/24 | 37.10.1.1 | Staff WiFi Clients (DHCP) |
| 30 | WiFi Guest | 37.10.2.0/24 | 37.10.2.1 | Guest WiFi (Isolated, DHCP) |
| 40 | Servers | 37.10.10.0/24 | 37.10.10.1 | Web 37.10.10.10, HR .20, Accounting .30, CRM .40, and Backup .50 |
| 50 | Security Systems | 37.10.20.0/24 | 37.10.20.1 | CCTV .10–.13, RFID .30–.32, and IoT .40–.41 |
| — | Core / WAN Infrastructure | 37.10.30.0/24 | — | Core SW1 .2, Core SW2 .3, Router .10/.11, and Firewall .20/.21 |

---

## Branch Office – Perth (35 Staff)

| VLAN | Purpose | Subnet | Gateway | Key IP Assignments |
|------|--------|--------|---------|-------------------|
| 10 | Wired LAN Workstations | 37.37.0.0/24 | 37.37.0.1 | User PCs (DHCP) |
| 20 | WiFi Staff | 37.37.1.0/24 | 37.37.1.1 | Staff WiFi Clients |
| 30 | WiFi Guest | 37.37.2.0/24 | 37.37.2.1 | Guest WiFi |
| 40 | File Server | 37.37.10.0/24 | 37.37.10.1 | File Server 37.37.10.10 |
| 50 | Security Systems | 37.37.20.0/24 | 37.37.20.1 | CCTV .10–.11, RFID .30, IoT .40 |
| — | Router / WAN | 37.37.30.0/24 | — | ISR 4321 Router 37.37.30.10 |

---

## Branch Office – Brisbane (25 Staff)

| VLAN | Purpose | Subnet | Gateway | Key IP Assignments |
|------|--------|--------|---------|-------------------|
| 10 | Wired LAN Workstations | 37.20.0.0/24 | 37.20.0.1 | User PCs (DHCP) |
| 20 | WiFi Staff | 37.20.1.0/24 | 37.20.1.1 | Staff WiFi Clients |
| 30 | WiFi Guest | 37.20.2.0/24 | 37.20.2.1 | Guest WiFi |
| 40 | File Server | 37.20.10.0/24 | 37.20.10.1 | File Server 37.20.10.10 |
| 50 | Security Systems | 37.20.20.0/24 | 37.20.20.1 | CCTV .10–.11, RFID .30, IoT .40 |
| — | Router / WAN | 37.20.30.0/24 | — | ISR 4321 Router 37.20.30.10 |

## Recommended Hardware

The recommended hardare table for the Truelec is provided below with its company name, specifications, URL and cost. 

| Device Name | Company Name | Specifications | URL | Cost (AUD) |
|------------|--------------|----------------|-----|------------|
| Enterprise Edge Routers (HQ & Branches) | Cisco | ISR 4461 (HQ) and ISR 4321 (Branches), WAN routing, MPLS/VPN support, BGP/VRRP and up to 1 Gbps of throughput | https://www.cisco.com/c/en/us/products/collateral/routers/4000-series-integrated-services-routers-isr/data_sheet-c78-732542.html | ~$6,000 (ISR 4461), ~$4,000 (ISR 4321) |
| Next-Generation Firewalls | Fortinet | FortiGate 100F, Active–Passive HA, IDS/IPS, VPN, and 10 Gbps firewall throughput | https://www.avfirewalls.com/fortigate-100f.asp | ~$7,500 each |
| Core Switches (HQ) | Cisco | Catalyst 9300, Layer 3 switching, 48 ports, StackWise, 10G uplinks, redundancy support | https://www.cdw.com/product/cisco-catalyst-9300-network-essentials-switch-48-ports-managed/4696730 | ~$9,000 each |
| Access Switches (HQ & Branches) | Cisco | Catalyst 2960X-24, Layer 2, 24 ports, Gigabit Ethernet, PoE support | https://www.router-switch.com/ws-c2960x-24ps-l-p-5265.html | ~$1,200 each |
| Wireless Access Points (HQ & Branches) | Cisco | AIR-AP3802E-E-K9, Cisco AIR-AP3800 Series Access Point, dual-band 2.4/5 GHz, WPA3, VLAN support, WiFi for staff and guests | https://www.router-switch.com/air-ap3802e-e-k9.html | ~$900 each |
| Application & Other Servers | Dell | DELLT640-14, Dell PowerEdge T640 Server, Intel Xeon 4208/8GB RAM/600GB SAS 10K | https://www.router-switch.com/dell-5u-t640-4208-8g-1-600g-sas-10k-1-h330-dvd-750w-1-3-5-8.html | ~$6,500 each |
| CCTV & Security Systems | Hikvision / Generic | IP CCTV cameras, NVR support, PoE powered, centralized monitoring | https://cctvguru.com.au/collections/hikvision?srsltid=AfmBOor4-RaIwG_pUdJFpzNu91ZhQidp36SAW0_XE5BdLn7aLvxY5-xp  | ~$1,500 (system) |
| RFID & IoT Devices | Generic | RFID readers, IoT sensors for access control and monitoring | https://www.teltonika-gps.com/products/accessories/readers-holders/1-wire-rfid-reader?https://www.teltonika-gps.com/products/trackers?utm_source=google&utm_medium=ppc&utm_campaign=ads-australia&utm_content=product&gad_source=1&gad_campaignid=22305094780&gbraid=0AAAAACcmtC_3NZDwgxqY7K45HKRW1vzPE&gclid=CjwKCAiA64LLBhBhEiwA-PxguwbtbS1MUNYc261vkU3kw4GRBy4HJr_Fbp3LVEclVKOTZ5uBocCmNhoCFiEQAvD_BwE | ~$1,000 (system) |

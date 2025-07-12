# Enterprise Network Home Lab


## Project Overview

This Project is designed to simulate a small enterprise IT environment using virtual machines, Windows Server, Active Directory, and workstations. We will first start by setting up the network topology and apply some security to it as well, progessing to the goal of build a foundation in IT operations while gradually expanding into security-focused workflows like SOC monitoring, endpoint telemetry, and secure network architecture.

---
> The home lab is divided into several hands-on project areas:


## 📂 Lab Project Index

| Project | Description | Status |
|--------|-------------|--------|
| Current Lab: Network Simulation (Packet Tracer) | Simulated enterprise network topology with VLANs, DHCP, static routing, etc. | ✅ Complete |
[Golden Image: IT/ SOC workstations](./IT-Projects/Windows-Imaging-Deployment/README.md) | Standardized Windows image with preinstalled tools and baseline settings | ✅ Complete |
[ Active Directory + GPO Setup ](https://github.com/AdrianFranc0/ActiveDirectory.Pt2) | Domain-based user provisioning and policy control and other IT tasks | ✅ Complete  |
| [SIEM Monitoring with Active Directory](https://github.com/AdrianFranc0/ActiveDirectory_SIEM_Monitoring) | Endpoint log telemetry, brute force detection, and MITRE ATT&CK testing with Splunk and Sysmon | ✅ Complete |
| pfSense Firewall & VLAN ACLs (physical) | Secure network segmentation for lab traffic | ⏳ In Progress |
| Helpdesk Ticket Simulation Lab | Simulated troubleshooting of common support issues with step-by-step resolutions | ⏳ In Progress |
| Disaster Recovery & Prevention Scenarios | Simulates endpoint/image recovery planning and IT resilience best practices | ⏳ In Progress |
| Mobile Device Management (MDM) Integration | Exploring centralized policy control for mobile devices using free MDM tools | ⏳ In Progress |


## Initial lab Objective


To simulate an enterprise-style network environment I used Cisco Packet Tracer. I focused on VLAN segmentation, ACL-based inter-VLAN security, and Active Directory integration. However some features were limited because of Packet Tracer, architectural placeholders and labeling were used to demonstrate future implementation plans. This emulated my future plans of buying physical devices and making my homelab.




### Skills Learned


- VLAN segmentation and trunk/access port configuration

- Inter-VLAN routing using subinterfaces and dot1Q

- ACL configuration to enforce security boundaries

- DNS/DHCP/HTTP services deployment

- Active Directory server integration and domain join

- Manual IP and DNS assignments

- Network monitoring via SIEM (simulated)

- IPS placement and traffic inspection (simulated)

- MDM segmentation for IoT/mobile device management



### Tools/Assets Used


- Cisco Packet Tracer

___

<p align="center"> 
 
## Steps


<p align="center"> 

  ISP Modem/Router → Lab Router (pfSense/Mini PC)

Lab Router → 5-Port Gigabit PoE+ Switch 

Switch → Lab Devices (PCs and AD VM)  <br/>
<img src="https://i.imgur.com/iTUyTLI.png" width="600" style="height:auto;">

<br />
<br />

___

<p align="center"> 
VLAN segmentation / Device & IP Configuration

VLANs configured on the switch

Access ports assigned per device

Subinterfaces on the router with dot1Q encapsulation enabled for inter-VLAN routing

Lab Router Interfaces:

G0/0 (to ISP): 192.168.1.2

G0/1 (to switch): Trunk port

Switch Ports:

Port to Lab Router: Trunk

Other ports: Access mode, assigned to VLANs

IP Schema:

VLAN 10 (Users): 10.10.10.0/24

VLAN 20 (AD Server): 10.20.20.0/24

VLAN 30 (Guest/IoT/MDM): 10.30.30.0/24:  <br/>
<img src="https://i.imgur.com/GrOv3wQ.png" width="600" style="height:auto;">
<br />
<br />

___

<p align="center"> 

I then verified that inter-VLAN communication was initially possible, confirming that routing between VLAN 10 and VLAN 20 functioned as expected prior to applying ACL restrictions: <br/>
<img src="https://i.imgur.com/rSr8u88.png" width="600" style="height:auto;">
<br />
<br />
___

<p align="center"> 
ACL Rules for Inter-VLAN Security

Purpose: Block ICMP traffic between VLANs to simulate enterprise-grade segmentation and internal zoning.
Bidirectional ICMP denial was enforced to model enterprise segmentation best practices where mutual isolation enhances security and detection control.:  <br/>
<img src="https://i.imgur.com/9oWfGK5.png" width="600" style="height:auto;">
<br />
<br />
 
___

<p align="center"> 
  
Active Directory Server Configuration (VLAN 20)

Services configured on server:

DHCP, DNS, HTTP (HTTP disabled for security)

DNS server IP: 10.20.20.5 :  <br/>
<img src="https://i.imgur.com/y6jwbHV.png" width="600" style="height:auto;">
<br />
<br />
 
___

<p align="center"> 
  
PC Domain Join to AD (VLAN 10)

DNS pointed to the AD server (10.20.20.5)

PC successfully joined the domain:  <br/>
<img src="https://i.imgur.com/g9yYHF0.png" width="600" style="height:auto;">
<br />
<br />
 
___

<p align="center"> 
Security Infrastructure Additions

Added additional ACL rules to the Lab Router for the VLANS
IPS placed between ISP and Lab Router to inspect and block malicious traffic before reaching internal devices.

MDM VLAN (30) added for laptops, phones, and a printer to isolate and manage mobile/IoT assets securely.

SIEM in VLAN 10 monitors access, IPS, firewall, ACL, and IoT logs for centralized threat visibility :  <br/>
<img src="https://i.imgur.com/onDw0Dq.png" width="600" style="height:auto;">
<img src="https://i.imgur.com/mxoeFE5.png" width="600" style="height:auto;">
<br />
<br />
 
___

Security Measures Implemented

HTTP disabled on AD server to minimize exposure

ACLs enforced segmentation between VLANs

DNS assigned manually to ensure proper AD resolution

ICMP blocked between segmented VLANs to simulate zoning/security boundaries

SIEM implemented in VLAN 10 to monitor access logs, firewall logs, IPS logs, ACL logs, and IoT traffic

IPS added between ISP modem and Lab Router to inspect incoming external traffic

VLAN 30 used for IoT, mobile, and printer devices with MDM security policies applied

This concludes the Cisco Packet Tracer simulation phase. The next step is to implement this setup using physical equipment (pfSense router/firewall, managed switch, crimped Cat6 cabling) and fully enable advanced firewall features.
<br />
<br />

___

I hope you learned and enjoyed my Home Network Lab! :)  I will add more additions to this.
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
*Ref 1: Network Diagram*

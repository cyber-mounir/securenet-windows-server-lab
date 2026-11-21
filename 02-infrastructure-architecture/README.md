\# 2. Infrastructure Architecture



\## 2.1 Architecture Overview



SecureNet Lab uses a virtualized infrastructure to simulate a small company's IT environment.



The lab is hosted on a Windows computer using VMware Workstation. Proxmox VE runs as a nested virtualization platform, hosting the virtual machines required for the project.



The architecture is divided into three main areas:



\- Physical Architecture

\- Logical Architecture

\- Network Architecture



\## 2.2 Physical Architecture



The physical architecture describes the hardware components that would normally be used in a small company infrastructure.



Main components include:



\- Physical Server

\- Rack

\- Managed Ethernet Switch

\- Router

\- Firewall Appliance

\- Patch Panel

\- UPS

\- Power Distribution Unit (PDU)



In this learning lab, these components are represented or simulated virtually where appropriate. VMware Workstation runs on the physical Windows host.



\## 2.3 Logical Architecture



The logical architecture describes the virtualization platforms, virtual machines, and services.



Main components:



\- Windows Host: runs VMware Workstation.

\- VMware Workstation: provides the virtualization environment.

\- Proxmox VE: runs as a nested virtual machine.

\- OPNsense (FW1): provides firewall, routing, and VLAN services.

\- DC1: Windows Server providing Active Directory, DNS, and DHCP.

\- FS1: Windows Server providing department-based file sharing.

\- PC-RH: HR client computer.

\- PC-COM: Commercial client computer.



\## 2.4 Network Architecture



The network is segmented into three VLANs:



\- VLAN 10: Servers — 10.10.10.0/24

\- VLAN 20: HR — 10.10.20.0/24

\- VLAN 30: Commercial — 10.10.30.0/24



OPNsense provides routing and firewall policies between the VLANs.



DC1 provides DHCP services for the client networks through DHCP Relay configured on OPNsense.



\## 2.5 Architecture Objectives



\- Separate infrastructure services from user networks.

\- Isolate HR and Commercial departments.

\- Centralize user authentication and DNS services.

\- Control access to shared folders.

\- Apply firewall rules between network segments.

\- Build a manageable and testable virtual environment.



\## 2.6 Lab Deployment Model



This project uses nested virtualization:



Windows Host → VMware Workstation → Proxmox VE → Virtual Machines.



This is a personal learning environment. In a real deployment, Proxmox VE would typically be installed directly on a physical server.


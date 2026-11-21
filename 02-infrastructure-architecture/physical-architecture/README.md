\# 2.1 Physical Architecture



\## 1. Overview



The Physical Architecture describes the hardware components required to build a small company's IT infrastructure.



In SecureNet Lab, the physical environment is represented conceptually because the project is implemented as a virtualized learning lab.



\## 2. Main Physical Components



\### 2.1 Rack



The rack provides a centralized enclosure for mounting and organizing network and server equipment.



Main purposes:

\- Organize hardware equipment.

\- Improve cable management.

\- Support ventilation and cooling.

\- Provide physical protection.



\### 2.2 Physical Server



The physical server provides computing resources for virtualization.



In a typical deployment, Proxmox VE would be installed directly on this server as the hypervisor.



In our current lab, the physical Windows computer runs VMware Workstation, which hosts Proxmox VE as a nested virtual machine.



\### 2.3 Managed Ethernet Switch



The managed switch connects network devices and supports VLAN segmentation using IEEE 802.1Q.



It allows different departments and server networks to be logically separated.



\### 2.4 Router



The router connects different IP networks and provides routing between network segments.



In our lab, routing between VLANs is handled by OPNsense.



\### 2.5 Firewall



The firewall controls network traffic according to security policies.



In our lab, OPNsense runs as a virtual firewall inside Proxmox VE.



It is not a separate physical firewall appliance.



\### 2.6 Patch Panel



The patch panel provides an organized termination point for network cables.



It is a passive component and does not perform switching or routing.



\### 2.7 UPS



The Uninterruptible Power Supply provides temporary backup power during electrical interruptions and helps protect equipment.



\### 2.8 PDU



The Power Distribution Unit distributes electrical power to devices mounted in the rack.



\### 2.9 NAS/SAN (Optional)



Network Attached Storage (NAS) or Storage Area Network (SAN) can provide centralized storage for files, backups, and virtual machine data.



These components are optional in our learning lab.



\## 3. Physical Lab Representation



Our current implementation uses:



\- One physical Windows computer.

\- VMware Workstation installed on the Windows host.

\- Proxmox VE running as a nested virtual machine.

\- Virtual network interfaces connecting the virtual machines.



The rack, physical switch, router, UPS, PDU, and patch panel are conceptual components used to explain a typical company infrastructure.



\## 4. Physical Architecture Summary



The physical architecture provides the hardware foundation for the logical and network architecture.



It defines where computing, connectivity, power, and storage resources come from.



\## 5. Important Deployment Note



For a real deployment, Proxmox VE would normally run directly on a dedicated physical server rather than inside VMware Workstation.



Our nested virtualization model is used for educational purposes and resource flexibility.


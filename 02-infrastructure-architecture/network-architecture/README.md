\# 2.3 Network Architecture



\## 1. Overview



The Network Architecture defines how devices and virtual machines communicate within SecureNet Lab.



The network is divided into three VLANs to separate servers, HR users, and Commercial users.



\## 2. Network Topology



The lab uses the following network design:



\- VMware Workstation hosts the nested Proxmox VE virtual machine.

\- Proxmox VE provides two virtual bridges.

\- OPNsense connects the WAN and internal VLAN networks.

\- DC1 and FS1 operate in the Servers VLAN.

\- HR and Commercial clients operate in separate VLANs.



\## 3. Proxmox Network Bridges



\### 3.1 vmbr0 – Management/WAN Bridge



\- Provides the management and WAN-side connectivity.

\- Connected to the VMware virtual network.

\- Used by OPNsense WAN interface.



\### 3.2 vmbr1 – Internal VLAN-Aware Bridge



\- Used for internal lab networks.

\- Configured as VLAN-aware.

\- Has no physical network port attached.

\- Carries VLANs 10, 20, and 30.

\- Connects OPNsense to the internal virtual machines.



\## 4. VLAN Design



| VLAN ID | Name | Network | Gateway | Purpose |

|---|---|---|---|---|

| 10 | Servers | 10.10.10.0/24 | 10.10.10.1 | Servers and infrastructure |

| 20 | HR | 10.10.20.0/24 | 10.10.20.1 | HR workstations |

| 30 | Commercial | 10.10.30.0/24 | 10.10.30.1 | Commercial workstations |



VLAN segmentation separates the departments and server infrastructure into different logical networks.



\## 5. IP Addressing Plan



\### 5.1 Servers VLAN – VLAN 10



| Device | IP Address | Role |

|---|---|---|

| OPNsense VLAN 10 | 10.10.10.1/24 | Default gateway |

| DC1 | 10.10.10.10/24 | AD DS, DNS, DHCP |

| FS1 | 10.10.10.20/24 | File Server |



\### 5.2 HR VLAN – VLAN 20



| Device | IP Address |

|---|---|

| OPNsense VLAN 20 | 10.10.20.1/24 |

| PC-RH | DHCP: 10.10.20.50–10.10.20.200 |



\### 5.3 Commercial VLAN – VLAN 30



| Device | IP Address |

|---|---|

| OPNsense VLAN 30 | 10.10.30.1/24 |

| PC-COM | DHCP: 10.10.30.50–10.10.30.200 |



\## 6. Network Services



\### 6.1 Routing



OPNsense performs inter-VLAN routing between the internal networks.



\### 6.2 DHCP



Windows Server DC1 provides DHCP services.



Two DHCP scopes are planned:



\- HR: 10.10.20.50–10.10.20.200.

\- Commercial: 10.10.30.50–10.10.30.200.



Each scope provides:

\- Default gateway for its VLAN.

\- DNS server: 10.10.10.10.

\- DNS domain: lab.example.test.



\### 6.3 DHCP Relay



DHCP broadcasts from VLAN 20 and VLAN 30 cannot cross routers directly.



OPNsense DHCP Relay forwards these requests to DC1 at 10.10.10.10.



The necessary firewall rules must permit DHCP Relay traffic.



\### 6.4 DNS



DC1 provides DNS services for the internal domain:



lab.example.test



Client machines use 10.10.10.10 as their DNS server.



\## 7. Network Security and Segmentation



The network is designed to enforce separation between departments.



Planned firewall policies include:



\- Permit necessary DNS and domain services from client VLANs to DC1.

\- Permit DHCP Relay traffic to DC1.

\- Permit authorized SMB access to FS1.

\- Block direct communication between VLAN 20 and VLAN 30.

\- Allow only required traffic between network segments.



These rules will be implemented and tested during the OPNsense configuration phase.



\## 8. Network Communication Flow



\### HR Client



PC-RH (VLAN 20) communicates with DC1 and FS1 through OPNsense according to the firewall policies.



\### Commercial Client



PC-COM (VLAN 30) communicates with DC1 and FS1 through OPNsense according to the firewall policies.



\### Department Isolation



Direct communication between HR and Commercial clients is blocked by firewall rules.



\## 9. Network Architecture Summary



The network architecture provides:



\- Logical separation through VLANs.

\- Centralized DHCP and DNS services.

\- Inter-VLAN routing through OPNsense.

\- Controlled access to shared resources.

\- Network isolation between departments.



The design will be validated during implementation and security testing.


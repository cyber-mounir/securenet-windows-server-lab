\# 4. Proxmox VE Setup



\## 1. Overview



Proxmox Virtual Environment (Proxmox VE) is an open-source virtualization platform used to host and manage virtual machines and containers.



In SecureNet Lab, Proxmox VE runs as a nested virtual machine inside VMware Workstation on a physical Windows computer.



\## 2. Deployment Architecture



The virtualization hierarchy is:



1\. Physical Windows computer.

2\. VMware Workstation.

3\. Proxmox VE virtual machine.

4\. OPNsense and Windows Server virtual machines hosted by Proxmox.



This nested virtualization approach is used for educational purposes.



\## 3. Proxmox VE Virtual Machine Resources



Initial planned resources:



| Resource | Allocation |

|---|---|

| CPU | 4 vCPUs |

| Memory | 10–12 GB RAM |

| Storage | 100 GB virtual disk |

| Network | VMware NAT |

| Virtualization | Nested virtualization enabled |



Actual allocations may be adjusted according to the host computer's available resources.



\## 4. Installation Preparation



Before installation:



\- Download the official Proxmox VE ISO.

\- Create a new virtual machine in VMware Workstation.

\- Attach the Proxmox VE ISO.

\- Allocate CPU, memory, storage, and network resources.

\- Enable nested virtualization.

\- Start the virtual machine and follow the installation process.



\## 5. Network Configuration Plan



The Proxmox environment uses two virtual bridges.



\### 5.1 vmbr0 – Management/WAN Bridge



\- Provides management and WAN-side connectivity.

\- Connected to the VMware NAT network.

\- Used by the OPNsense WAN interface.



\### 5.2 vmbr1 – Internal VLAN-Aware Bridge



\- Used for internal lab networks.

\- Configured as VLAN-aware.

\- Has no physical network port attached.

\- Carries VLAN 10, VLAN 20, and VLAN 30.

\- Connects OPNsense to internal virtual machines.



The exact bridge configuration will be verified during implementation.



\## 6. Virtual Machine Management



Proxmox VE provides a web-based management interface.



The administrator can use it to:



\- Create and configure virtual machines.

\- Allocate CPU, RAM, and storage.

\- Configure virtual network interfaces.

\- Start, stop, and monitor virtual machines.

\- Manage virtual storage and backups.



\## 7. Validation and Testing



After installation, the following checks must be performed:



\- \[ ] Proxmox VE boots successfully.

\- \[ ] Proxmox management interface is accessible.

\- \[ ] Network connectivity is working.

\- \[ ] Storage is available.

\- \[ ] CPU and memory allocations are correct.

\- \[ ] Nested virtualization is available.

\- \[ ] vmbr0 is configured correctly.

\- \[ ] vmbr1 is configured as a VLAN-aware internal bridge.



\## 8. Screenshots and Evidence



The following screenshots should be collected during implementation:



\- Proxmox installation screen.

\- Proxmox web management interface.

\- Proxmox node summary.

\- CPU and memory configuration.

\- Network bridge configuration.

\- Storage configuration.



\## 9. Expected Result



At the end of this phase, Proxmox VE should be installed and ready to host the OPNsense firewall and Windows Server virtual machines.



\## 10. Official Documentation



Proxmox VE Downloads:



https://www.proxmox.com/en/downloads



Proxmox VE Documentation:



https://pve.proxmox.com/pve-docs/


# 2.2 Logical Architecture

## 1. Overview

The Logical Architecture describes the virtual infrastructure, including virtual machines, hypervisor platforms, and the roles of each system.

SecureNet Lab uses nested virtualization to simulate a small company's IT infrastructure.

## 2. Virtualization Platforms

### 2.1 VMware Workstation

VMware Workstation is installed on the physical Windows computer.

It provides the virtualization environment that hosts the Proxmox VE virtual machine.

### 2.2 Proxmox VE

Proxmox VE runs as a nested virtual machine inside VMware Workstation.

It acts as the main hypervisor for the lab's virtual infrastructure and hosts the OPNsense and Windows Server virtual machines.

## 3. Virtual Machines

### 3.1 FW1 – OPNsense Firewall

Role:

- Firewall and network security.

- VLAN interface management.

- Inter-VLAN routing.

- DHCP Relay for client networks.

- WAN connectivity through VMware NAT.

Resources:

- 1 vCPU.
- 1 GB RAM.
- Two VirtIO network interfaces.

### 3.2 DC1 – Domain Controller

Role:

- Active Directory Domain Services (AD DS).
- DNS services.
- DHCP services.
- Centralized user and computer authentication.

Network configuration:

- VLAN 10 – Servers.
- IP address: 10.10.10.10/24.
- Gateway: 10.10.10.1.
- Preferred DNS: 10.10.10.10.
- Domain: securenet.local.

Resources:

- 2 vCPU.
- 3 GB RAM.

### 3.3 FS1 – File Server

Role:

- Centralized file storage.
- Department shared folders.
- Access control using Active Directory security groups.
  
Network configuration:

- VLAN 10 – Servers.
- IP address: 10.10.10.20/24.
- Gateway: 10.10.10.1.
- Preferred DNS: 10.10.10.10.

Resources:
- 2 vCPU.
- 2 GB RAM.

### 3.4 PC-RH – HR Client

Role:

- Represents an HR department workstation.
- Receives an IP address through DHCP.
- Joins the Active Directory domain.
- Accesses authorized HR shared folders.

Network configuration:

- VLAN 20 – HR.
- IP address: Assigned by DHCP.

Resources:

- 2 vCPU.
- 2 GB RAM.

### 3.5 PC-COM – Commercial Client

Role:

- Represents a Commercial department workstation.
- Receives an IP address through DHCP.
- Joins the Active Directory domain.
- Accesses authorized Commercial shared folders.

Network configuration:

- VLAN 30 – Commercial.
- IP address: Assigned by DHCP.

Resources:

- 2 vCPU.
- 2 GB RAM.

## 4. Virtual Infrastructure Summary

| System | Main Role | Network |
|---|---|---|
| FW1 | Firewall and routing | WAN and VLAN trunk |
| DC1 | Active Directory Domain Services (AD DS), DNS and DHCP | VLAN 10 |
| FS1 | File Server | VLAN 10 |
| PC-RH | HR workstation | VLAN 20 |
| PC-COM | Commercial workstation | VLAN 30 |

## 5. Resource Allocation

The resources listed above are initial lab allocations. They may be adjusted according to the physical computer's available CPU, memory, and storage.

## 6. Logical Architecture Summary

The logical architecture defines how the virtual systems are organized and how their roles support the company's IT services.

It provides the foundation for implementing the network architecture, security policies, and infrastructure services.

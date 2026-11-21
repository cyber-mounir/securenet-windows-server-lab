# 3. Infrastructure Preparation

## 1. Overview

Infrastructure Preparation is the process of checking and preparing the host computer and virtualization environment before deploying the lab infrastructure.

SecureNet Lab uses nested virtualization:

- Physical Windows computer.
- VMware Workstation installed on Windows.
- Proxmox VE running as a virtual machine inside VMware Workstation.
- OPNsense and Windows Server virtual machines hosted by Proxmox VE.

## 2. Hardware Requirements

The host computer should provide sufficient resources for the virtualization environment.

Recommended resources for this lab:

- CPU: 64-bit processor with hardware virtualization support.
- RAM: 16 GB or more recommended.
- Storage: SSD with sufficient free space.
- Network: Working Ethernet or Wi-Fi connection.
- BIOS/UEFI: Intel VT-x or AMD-V enabled.

Actual resource availability must be checked before deployment.

## 3. Virtualization Software

### 3.1 VMware Workstation

VMware Workstation runs on the physical Windows computer and hosts the Proxmox VE virtual machine.

### 3.2 Proxmox VE

Proxmox VE is configured as a nested virtual machine inside VMware Workstation.

Planned VM resources:

- 4 virtual CPUs.
- 10–12 GB RAM.
- 100 GB virtual disk.
- VMware NAT network adapter.
- Nested virtualization enabled.

These values are initial allocations and may be adjusted according to host resources.

## 4. Nested Virtualization

Nested virtualization allows a hypervisor to run inside another virtualized environment.

In this project:

1\. Windows runs on the physical computer.
2\. VMware Workstation runs on Windows.
3\. Proxmox VE runs inside VMware Workstation.
4\. Proxmox hosts the lab's virtual machines.

The CPU virtualization extensions must be available to the nested Proxmox environment.

## 5. Network Preparation

The VMware virtual network provides connectivity to the Proxmox VE virtual machine.

The initial design uses:

- VMware NAT for Proxmox WAN and management-side connectivity.
- Proxmox vmbr0 for the WAN/management side.
- Proxmox vmbr1 for internal VLAN networks.
- OPNsense to manage internal routing and firewall policies.

## 6. Preparation Checklist

The following checks must be completed before installing or configuring the lab:

- [ ] Confirm CPU virtualization support.
- [ ] Confirm virtualization is enabled in BIOS/UEFI.
- [ ] Check available physical RAM.
- [ ] Check available disk space.
- [ ] Install VMware Workstation.
- [ ] Confirm network connectivity.
- [ ] Prepare the Proxmox VE installation ISO.
- [ ] Plan the Proxmox virtual machine resources.
- [ ] Enable nested virtualization.

## 7. Important Notes

Resource allocations are planning values, not proof that the host can run every virtual machine simultaneously.

The available RAM and CPU capacity must be checked to avoid overloading the physical computer.

This is an educational nested virtualization lab, not a production deployment.

## 8. Expected Result

At the end of this phase, the host computer and VMware environment should be ready to host the Proxmox VE virtual machine.

The next phase will focus on installing and configuring Proxmox VE.


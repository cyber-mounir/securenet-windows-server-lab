# 1. Project Requirements

## 1.1 Project Overview

SecureNet Lab is a personal learning project designed to build and test a secure Windows Server infrastructure in a virtualized environment.

The lab simulates a small company with two departments:

- Human Resources (HR)
- Commercial


## 1.2 Project Objectives

- Build a virtualized infrastructure using VMware Workstation and Proxmox VE.
- Configure network segmentation using VLANs.
- Implement firewall and routing services using OPNsense.
- Deploy Windows Server with Active Directory, DNS and DHCP.
- Configure a File Server with department-based access permissions.
- Restrict unauthorized communication between departments.
- Test and document the complete infrastructure.

## 1.3 Functional Requirements

- Client computers must receive IP addresses automatically through DHCP.
- Users must authenticate through Active Directory.
- HR users must access only authorized HR shared folders.
- Commercial users must access only authorized Commercial shared folders.
- Communication between HR and Commercial networks must be restricted.
- DNS must resolve internal domain resources.

## 1.4 Technical Requirements

- VMware Workstation
- Proxmox VE
- OPNsense Firewall
- Windows Server
- Active Directory Domain Services
- DNS and DHCP
- File Server
- Cisco Packet Tracer
- Git and GitHub

## 1.5 Project Scope

This project covers the design, deployment, configuration, testing and documentation of a virtualized company network.

It is a personal educational lab and is not intended for production use.

## 1.6 Project Constraints

- Limited physical hardware resources.
- Virtualized environment running on a Windows host.
- Limited CPU and RAM availability.
- Internet access may depend on the host network.
- All configurations must remain suitable for a personal learning environment.

## 1.7 Expected Results

At the end of the project:

- The virtual infrastructure will be operational.
- VLAN segmentation and routing will work.
- Windows Server services will be configured.
- Domain users will have appropriate access permissions.
- Unauthorized interdepartment communication will be blocked.
- The implementation will be documented and tested.


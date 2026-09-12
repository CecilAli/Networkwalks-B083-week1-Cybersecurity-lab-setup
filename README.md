# Networkwalks-B083-week1-Cybersecurity-lab-setup
## 1.Overview

This project establishes the initial virtual cybersecurity laboratory required for the first week of the Cybersecurity Project. The laboratory was created using **Oracle VirtualBox** and **Kali Linux**, with a dedicated NAT Network configured on the 10.0.0.0/24 subnet.
The main purpose of this setup is to provide an isolated and controlled environment that can later be expanded with additional virtual machines for cybersecurity testing and practical exercises.

## 2.Objectives

•	Install and configure VirtualBox;

•	Prepare a dedicated virtual network;

•	Configure a NAT Network using 10.0.0.0/24;

•	Install/import Kali Linux;

•	Configure a static IPv4 address;

•	Verify gateway, Internet and DNS connectivity;

•	Create a VM snapshot after the initial setup;

•	Prepare the environment for future cybersecurity exercises.

## 3.Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Operating System | Kali Linux |
| Network Type | NAT Network |
| Network | `10.0.0.0/24` |
| Kali Linux IP | `10.0.0.2/24` |
| Default Gateway | `10.0.0.1` |
| DNS Server | `8.8.8.8` |
| Network Interface | `eth0` |
| Purpose | Cybersecurity Testing Laboratory |

## 4.Network Architecture

The initial laboratory network follows the structure below:


                    Internet
                        │
                        │
                ┌───────▼────────┐
                │  VirtualBox    │
                │   NAT Network  │
                │  10.0.0.0/24   │
                └───────┬────────┘
                        │
                 Gateway: 10.0.0.1
                        │
                ┌───────▼────────┐
                │   Kali Linux   │
                │    eth0        │
                │  10.0.0.2/24   │
                └────────────────┘

The 10.0.0.0/24 network provides the addressing space for the virtual cybersecurity laboratory.
Kali Linux uses 10.0.0.2 as its static IPv4 address.

## 5. Configuration

## 5.1. VirtualBox

Oracle VirtualBox was used as the virtualization platform for the laboratory.
The virtual environment allows the cybersecurity machines to operate independently from the host operating system while maintaining the required network connectivity.
The Kali Linux virtual machine was imported into VirtualBox and configured to use the laboratory NAT Network.

## 5.2. NAT Network 
A dedicated NAT Network was configured in VirtualBox.

## Network parameters
Network Name: NATNetwork
Network:      10.0.0.0/24
Gateway:      10.0.0.1
Enable DHCP 

The NAT Network provides connectivity between the virtual machines and allows the laboratory to access the Internet.

<img width="959" height="539" alt="step3_NAT" src="https://github.com/user-attachments/assets/5b271693-3f7d-4de4-af1b-0da4eb44b840" />

This network was used by Kali Linux and by additional virtual machines added during future lab exercises.

<img width="586" height="356" alt="conf_NAt_naVM" src="https://github.com/user-attachments/assets/fba3dd27-5955-49fa-a56d-8f48a887b5b4" />


## 5.3. Kali Linux

Kali Linux was selected as the main machine for cybersecurity testing and security-related exercises.
The virtual machine network adapter was connected to the previously created NAT Network.

## Adapter configuration
Adapter:       eth0
Connection:    NAT Network
IPv4 Method:   Manual

<img width="480" height="539" alt="conf_ipKAli" src="https://github.com/user-attachments/assets/6a76854d-1857-441f-9fa8-ecd8ed524fed" />

The static network configuration was selected so that Kali Linux maintains a predictable address within the laboratory.

## 5.4. Network Verification

After configuring the network interface, connectivity was tested at different levels.
<img width="523" height="539" alt="confirmacao_IP_Kali" src="https://github.com/user-attachments/assets/108dc977-064a-4d93-a1e4-1954cd5bd8da" />

The interface was verified as active and configured with: 10.0.0.2/24

## 5.5. Troubleshooting
During the configuration process, network connectivity was temporarily interrupted while testing the network interface.
The interface was brought back online and the network connection was re-established using NetworkManager.
## NetworkManager commands

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"

**Important: Linux connection names are case-sensitive.**
The correct connection name in this configuration is: Wired connection 1
Using a different capitalization can result in an error such as: **Error: unknown connection 'wired connection 1'.**


## Final Verification

| Test                  | Expected Result                   | Status    |
| --------------------- | --------------------------------- | --------- |
| VirtualBox installed  | Virtualization platform available | ✅         |
| NAT Network created   | `10.0.0.0/24`                     | ✅         |
| Kali Linux connected  | Connected to NAT Network          | ✅         |
| Static IP             | `10.0.0.2/24`                     | ✅         |
| Gateway               | `10.0.0.1` reachable              | ✅         |
| Internet connectivity | External IP reachable             | ✅         |
| DNS resolution        | Domain name resolves              | ✅         |
| Network interface     | `eth0` active                     | ✅         |
| Snapshot              | Baseline restore point            | 🔲 Verify |

## Lessons Learned
This laboratory setup provided practical experience with:

Virtual machine deployment using VirtualBox.
NAT Network configuration.
IPv4 addressing and subnetting.
Static IP configuration.
Default gateways and routing.
DNS configuration and verification.
Network connectivity testing using ping.
Basic NetworkManager troubleshooting.
Preparing a controlled environment for cybersecurity exercises.

The troubleshooting process also demonstrated the importance of checking the interface state, routing table, gateway connectivity, and DNS independently rather than assuming that an Internet connection failure has a single cause.

# Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**

<p align="left"> <img src="https://img.shields.io/badge/Skill-Cybersecurity-red?style=flat-square" /> <img src="https://img.shields.io/badge/Ver-VirtualBox%20v7.2-blue?style=flat-square" /> <img src="https://img.shields.io/badge/Kali%20Linux-black?style=flat-square&logo=kalilinux&logoColor=red" /> <img src="https://img.shields.io/badge/v2026.2-orange?style=flat-square" /> <img src="https://img.shields.io/badge/Skill-Linux-black?style=flat-square" /> <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-14B8A6?style=flat-square" /> <img src="https://img.shields.io/badge/Penetration%20Testing-red?style=flat-square" /> <br/> <img src="https://img.shields.io/badge/Skill-Virtualization-red?style=flat-square" /> <img src="https://img.shields.io/badge/GitHub-black?style=flat-square&logo=github&logoColor=white" /> <img src="https://img.shields.io/badge/Kali%20Linux-black?style=flat-square&logo=kalilinux&logoColor=red" /> <img src="https://img.shields.io/badge/XorShield-black?style=flat-square" /> <img src="https://img.shields.io/badge/Ethical%20Hacking-orange?style=flat-square" /> <img src="https://img.shields.io/badge/Danjuma%20Yusuf%20Joseph-red?style=flat-square" /> </p>

---

## Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

## Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install/import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

## Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

> ⚠️ **Important:** This laboratory must only be used on systems you own or have explicit permission to test. Do not use the lab to attack unauthorized systems.

## 🏗️ Lab Architecture
<img width="1345" height="618" alt="1-Screenshot title-image" src="https://github.com/user-attachments/assets/dd26d9d5-75ac-4e79-9322-828fda9d89d8" />
Additional target machines can be added to the same virtual network in future projects.

## ⚙️ Lab Configuration

| 🧩 Component | 🧩 Configuration |
|---|---|
| 💻 Host OS | Windows 11 Pro |
| 🔴 Host RAM | 16 GB |
| ⚡ Processor | Intel Core i7 |
| 📦 Hypervisor | VirtualBox 7.2 |
| 🐉 Security OS | Kali Linux 2026.3 |
| 🔴 Kali RAM | 2048 MB |
| 🌐 Network Address | 10.0.0.0/24 |
| 🐉 Kali IP Address | 10.0.0.2/24 |
| 📮 Default Gateway | 10.0.0.1 |
| 🌍 DNS Server | 8.8.8.8 |
| 🐉 Future VM Range | 10.0.0.3–10.0.0.99 |

## Lab Setup Procedure

### Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

### Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

---

### Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration: Network Name: `NatNetwork` IPv4 Prefix: `10.0.0.0/24` DHCP: Enabled IPv6: Disabled
<img width="1919" height="1034" alt="2-Screenshot network-settings" src="https://github.com/user-attachments/assets/245f75f3-7454-4428-8b8b-43861ec2a3ce" />

A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

---

### Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop (82540EM)
```

The VM was allocated:

```
RAM: 2048 MB
```
<img width="1920" height="955" alt="3-Screenshot-kali-linux" src="https://github.com/user-attachments/assets/df658236-1add-4b1b-9e1c-497dd27154b1" />

A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

---

### Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.
<img width="1920" height="955" alt="4-Screenshot-kali-network-settings" src="https://github.com/user-attachments/assets/9cb5d329-8aec-4f86-ab50-ad167488aaae" />

---

### Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

```
Clean Kali - Network Setup
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

## Lab Verification

| ✅ Test | 🖥️ Command | 🎯 Expected Result |
|---|---|---|
| 🌐 Check IP address | `ip a` | Correct Kali IP displayed |
| 📡 Test gateway | `ping 10.0.0.1` | Successful replies |
| 🌍 Test Internet connectivity | `ping 8.8.8.8` | Successful replies |
| 🔴 Verify Nmap | `nmap -sn 10.0.0.0/24` | Hosts on the network displayed |
| 💾 Verify snapshot | Restore snapshot and run `ip a` | Baseline configuration restored |

### Example Results

```
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```

## Problems Encountered & Solutions

Documenting problems is an important part of the project.

### Problem 1. Internet Connectivity After Static IP Configuration

After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was:

```
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

The network connection was then restarted/rebooted and connectivity was tested again.

> **Important:** Network interface and connection names may differ between systems. Identify your actual connection name before running an `nmcli` command.

### Problem 2. VirtualBox VT-x / Virtualization Error

The VM initially failed to start because hardware virtualization was disabled in the system firmware/BIOS.

The issue was resolved by:

1. Restarting the computer.
2. Entering BIOS/UEFI settings.
3. Enabling Intel VT-x / hardware virtualization.
4. Saving the configuration.
5. Restarting the computer.
6. Starting the Kali VM again.

After enabling virtualization, the VM started successfully.

## What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots

I learned that a clean snapshot should be created **before performing risky or experimental activities**.

This provides a known-good recovery point for future cybersecurity exercises.

### 5. Documentation

I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

## Security & Ethical Use

This laboratory is intended strictly for education purposes only.

## 🔗 Tools & Resources

- **7-Zip:** https://7-zip.org/download.html
- **VirtualBox:** https://virtualbox.org/wiki/Downloads
- **Kali Linux:** https://kali.org/get-kali

## 👤 Author

**Danjuma Yusuf Joseph (XorShield)**

Cybersecurity Professional `B082`

LinkedIn: https://www.linkedin.com/in/xorshield/

## 📌 Project Information

**Program Name:** XorShield Home Lab | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub

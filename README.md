# Homelab – Proxmox + TrueNAS

My home lab setup for secure file storage, learning virtualization, networking, and infrastructure security.

---

## Overview

I built this homelab to:

- Create secure, self-hosted storage with unlimited access to my files without relying on cloud services  
- Learn how virtualization and VM management work in practice  
- Understand networking fundamentals – static IPs, bridges, firewall rules  
- Practice infrastructure security – encryption, access control, SSH hardening  
- Experiment with real systems instead of just reading about them

The main goal was to have **full control over my data** while learning infrastructure and security concepts hands-on.

---

## What's Running

### Hardware
- ThinkCentre M725S
- 1x SSD NVMe 256GB 
- 2x HDD 1TB
- Local network with static IPs

### Software

- **Proxmox VE** – hypervisor running on bare metal  
- **TrueNAS VM** – handles storage with ZFS  
- **Syncthing** – syncs files between my devices

### Current Setup

**TrueNAS VM** running on Proxmox:
- ZFS pool for storage  
- Syncthing for encrypted file synchronization across devices  
- Backup storage for my projects and personal files  
- Full control over my data without cloud dependency

---

## How I Set It Up

### Proxmox Installation
- Installed Proxmox VE on the host machine
- Set up network bridge so VMs can talk to my local network
- Configured static IP for the management interface
- Secured SSH access with key authentication

### TrueNAS VM
- Created a VM and passed through a physical disk for ZFS
- Gave it enough CPU and RAM to run smoothly
- Connected it to my local network with firewall rules

### Storage Configuration
- Created a ZFS pool in TrueNAS
- Set up datasets to organize files
- Enabled compression and checksums (ZFS does this automatically)
- Configured access permissions

### Syncthing
- Installed Syncthing in TrueNAS
- Connected it to my laptop and desktop
- Set up encrypted connections for secure file sync
- Now my files sync automatically between devices without going through third-party servers

---

## What I Learned

- **Proxmox basics** – creating VMs, allocating resources, setting up network bridges  
- **TrueNAS** – configuring ZFS pools, managing storage, using the web interface  
- **Syncthing** – peer-to-peer file sync with encryption, avoiding cloud dependencies  
- **Networking** – static IPs, network bridges, firewall configuration, how VMs connect to the local network  
- **Security** – SSH key authentication, encrypted file transfer, access control  
- **Troubleshooting** – fixed VM boot issues, network connectivity problems, and storage config mistakes  

---

## Problems I Ran Into

**Disk passthrough confusion**  
At first I wasn't sure how to give TrueNAS direct access to a physical disk. Figured out Proxmox has a passthrough feature for this.

**Network setup**  
TrueNAS VM couldn't reach the local network initially. Had to configure the network bridge properly in Proxmox and assign a static IP.

**Syncthing learning curve**  
First time using Syncthing – had to read the docs and test with small files before syncing everything.

---

## What's Next

- Add a Docker host VM to run containerized services  
- Set up automated ZFS snapshots for versioned backups  
- Configure WireGuard VPN for secure remote access from outside my local network  
- Try monitoring with Prometheus/Grafana to see resource usage  
- Experiment with more VMs (development environments, testing Linux distros, etc.)  
- Explore network segmentation and VLANs for better security

---

## Why I Made This

This project helps me understand:

- How to secure my own infrastructure instead of trusting cloud providers  
- Virtualization, storage, and networking hands-on  
- Security fundamentals – encryption, firewalls, SSH hardening, access control  
- How to troubleshoot problems when things break  
- Network concepts used in production environments

It's a learning environment where I have **full control over my data** while experimenting with real technology used in production systems.

---

## Resources I Used

- [Proxmox VE Documentation](https://pve.proxmox.com/pve-docs/)  
- [TrueNAS Documentation](https://www.truenas.com/docs/)  
- [Syncthing Documentation](https://docs.syncthing.net/)

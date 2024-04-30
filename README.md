Home Lab 2024
============================================

High Level Overview
--------------------------------------------
Physical Network Layer
All Unifi (Unless otherwise specified) 

Basement:
- UDM Pro
- Switch 8 PoE 60 Watt 
- U6 Lite (Access Point) 

Main Level:
- Office USW 24
- Cloud(Lab) USW 24  
- 10GBE SFP+ USW Aggregation 
- U6 Pro (Access Point)
- MikroTik CRS309 10GBE SFP+ 8 Port 

Upstairs:
- Switch Lite 8 PoE
- Access Point AC Lite




Network Diagram  
![High Level Network Diagram](docs/images/network-highlevel.excalidraw.png)
```
Default                             10.222.1.0/24   VLAN: 1
Core                                10.230.0.0/24   VLAN: 230
Management                          10.33.1.0/24    VLAN: 33
Skyline Classic                     10.220.1.0/24   VLAN: 220
Remote (DMZ)                        10.106.0.0/24   VLAN: 106
V-Cluster (Classic)                 10.107.0.0/24   VLAN: 107
Production SDE                      10.108.0.0/24   VLAN: 108
Test Lab                            10.150.0.0/24   VLAN: 150
InternetOfThings                    192.168.40.0/24 VLAN: 40
--------
```
### Environments/Domains/VLANs

#### Physical Layer
![Pysical Layer Diagram](docs/images/network-compute-layer.excalidraw.png)
#### Default Environment
-------
Subnet: 10.222.1.0/24  
DNS Domain: None  
Compute: 1 or 2 PIs for DNS

This subnet consist of newtworking equipment and makes up the "backbone" of the network. Will also have 1 - 2 DNS Appliances (PIs)

#### Default Environment
-------
Subnet: 10.222.1.0/24  
DNS Domain: *.infra.ernal.wallyworld.lan  
Compute: None

This subnet consist of the backbone networking equipment

#### Core Domain
-------
Subnet: 10.230.0.0/24  
DNS Domain: *.core.skyline-lab.com  
Compute: 
- 3 Node Proxmox HA Cluster (Low Power - Dell Micro)
- NAS - All Flash UGreen (Need Stand in till end of June)

Power: Always On

Virtual Compute:
- Docker Host (docker.core.skyline-lab.com)
- DNS2 (dns2.core.skyline-lab.com)
- Rancher (rancher.core.skyline-lab.com)
- Proxmox Backup Server (pbs.core.skyline-lab.com)

This subnet consist of services that are critical and shared for all environments. These are:
- Internal DNS (Source of Truth)
- User Auth (LDAP)
- Shared File Services 
- Outgoing Email
- Homepage
- Root CA (ACME)
- Password Manager
- SSL Reverse Proxy
- Cloud Storage (Sync) 
- Proxmox Backup Server (On NAS)

Cluster Notes:  
Use 3 Dell Optiplex Micro 7050 (64GB, 1TB NVMe - 2TB Data). Single NIC. Ceph Cluster (Maybe)



#### Production Software Development Env (SDE) Lab Domain
-------
Subnet: 10.108.0.0/24  
DNS Domain: *.sde.skyline-lab.com  
Compute: 
- Single Proxmox Node 
    - Minisforum MS-01 
    - CPU: i9-13900H 14c/20t
    - RAM: 64GB
    - Boot/Data: 1TB NVMe
- NAS

Power: Always On  
This is production quality Software Development Environment. Described [PBI Lab](docs/lab-pbi/lab-pbi.md)


#### Test Lab Domain
-------
Subnet: 10.150.0.0/24  
DNS Domain: *.test.skyline-lab.com  
Compute: 
- 2 Proxmox Node Cluster
    - Dell T7920
    - Dell T7910
- NAS

Power: On Demand (Wake on LAN)

#### Remote/DMZ
-------
Subnet: 10.106.0.0/24  
DNS Domain: *.cloud.skyline-lab.com  
Compute: 
- ZimaBoard
- NAS

#### IOT Environment
-------
Subnet: 192.168.40.0/24 
DNS Domain: *.iot.wallyworld.lan  
Compute: None

This subnet consist of untrusted internet enabled devices.

#### Management Subnet
-------
Subnet: 10.33.1.0/24 
DNS Domain: *.mgmt.wallyworld.lan  
Compute: None

This subnet consist of Device Management Interfaces, KVMs, Lights out Management (iDRAC)

#### Internal Environment
-------
Subnet: 10.220.1.0/24  
DNS Domain: *.internal.wallyworld.lan  
Compute: None

This subnet consist of User's client devices. For example my laptop and other various workstations
### Backup Strategy
--------------------------------------------
Will use a NAS device to keep onsite backups. Most workloads will be running on Proxmox, there for VM Level backups will be performed via Proxmox Backup Server. I have a old QNAP NAS that cannot run VMs but can be a NFS server. Will use that plus a front end server to run Proxmx Backup Server. 

For file level backups - will use Restic https://restic.net

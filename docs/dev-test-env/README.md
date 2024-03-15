Local Developement and Test Environment
============================================

This section of the documentation describes my local dev and test environment

Virtual Proxmox Lab
--------------------------------------------
I have a nested virtualized Proxmox lab running on a single Dell Workstation. The main purpose of this setup is to test a clusterized Proxmox system and deployment automation

Virtual Lab Host
--------------------------------------------
Hostname: pve-lab.cloud.skyline.lan  
IP: 10.107.0.13  
OS: Proxmox VE  
Hardware: Dell Precision T7920 Workstation  
CPU: Dual Xeon Silver 4114 (10c/20t). Total 40threads  
GPU: Nvidia P2000  
RAM: 64GB (4x16GB) [HMA82GR7CJR8N - VK 2Rx8 PC4-2666V] - 24 DIMM Slots  
Boot Disk: 256GB NVMe (dell) [Flex Module]   
Data Disk 1: 1TB NVMe (dell) [Flex Module]  
Data Disk 2: Empty [Flex Module]    
Data Disk 3: Empty [Flex Module]  

Will Add another 64GB Soon      
    

Virtual Host Layer
--------------------------------------------
Virtual Workstation 
- PopOS
    - DHCP
    - 4 vCPU
    - 8 GB RAM
    - 50 GB Disk

Virtual Proxmox Cluster
- proxmox1.cloud.skyline.lan
    - 10.107.0.51
    - 8 vCPU
    - 4 GB RAM
    - 32 GB Boot
    - 100 GB Ceph Disk

- proxmox2.cloud.skyline.lan
    - 10.107.0.52
    - 8 vCPU
    - 4 GB RAM
    - 32 GB Boot
    - 100 GB Ceph Disk
- proxmox3.cloud.skyline.lan
    - 10.107.0.53
    - 8 vCPU
    - 4 GB RAM
    - 32 GB Boot
    - 100 GB Ceph Disk
    
Shared Storage
    - TBD
Backup Server
- proxmox-backup.cloud.skyline.lan
    - 10.107.0.54
    - 2 vCPU
    - 8 GB RAM
    - 32 GB Boot
    - NFS Mounted Data Disk



TEST-LAB
============================================
Current (8/1/2024) Setup
pve-proto.cloud.skyline.lan (10.107.0.20) --> pve1.test.skyline-lab.com 10.107.0.21
- Dell T7910 E5-2690 V4 (qty 2 28-cores/56-threads) 192GB RAM

pve2.test.skyline-lab.com (10.107.0.20) --> pve2.test.skyline-lab.com 10.107.0.22
- Dell T7920 Intel Silver 4114 (qty 2 20-cores/40-threads) 96GB RAM
- Disks
-- Boot 256 NVMe
-- Fast Data 1TB NVMe
-- Slow Data 1TB SSD


nas.rhel.lab
- ASUStor AS6510T Intel Atom 4 core 32GB RAM

Virtual Proxmox Cluster (old 7050 test)
--------------------------------------------
proxmox 1: proxmox1.cloud.skyline.lan 10.107.0.51  
proxmox 2: proxmox2.cloud.skyline.lan 10.107.0.52  
proxmox 3: proxmox3.cloud.skyline.lan 10.107.0.53


Virtual Proxmox Cluster
--------------------------------------------
proxmox 1: proxmox1.cloud.skyline.lan 10.107.0.51  
proxmox 2: proxmox2.cloud.skyline.lan 10.107.0.52  
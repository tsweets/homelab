Test Environment (OLE)
============================================

Overview
--------------------------------------------
The purpose of this environment is to have an Ops Like Environment (OLE) for final Integration Testing before deployment to a AWS Acceptance Test environment. It will match as close as possible to the AWS OPS enviornment and will consist mostly of a managed Kubernetes Cluster. 

Physical 
--------------------------------------------
### Virtual Host

|||
|--------------------|--------------------|
| Hostname: | pve2.test.skyline-lab.com |
|IP: | 10.107.0.22 |  
|OS: | Proxmox VE |  
|Hardware: | Dell Precision T7920 Workstation |  
|CPU: | Dual Xeon Silver 4114 (10c/20t) Total 40threads |  
|GPU: | Nvidia P2000 |  
|RAM: | 96GB (6x16GB) [HMA82GR7CJR8N - VK 2Rx8 PC4-2666V] - 24 DIMM Slots |
|Boot Disk: | 256GB NVMe (dell) [Flex Module] |  
|Data Disk 1: | 1TB NVMe (dell) [Flex Module] FAST-DATA | 
|Data Disk 2: | 1TB SSD [Flex Module]  SLOW-DATA|   
|Data Disk 3: | Empty [Flex Module] |  

### Virtual Machines
|||
|--------------------|--------------------|
|kube-vip (IP Only)|10.100.0.40|
|k3s-control-01|10.100.0.41|
|k3s-control-02|10.100.0.42|
|k3s-control-03|10.100.0.43|
|k3s-node-01|10.100.0.45|
|k3s-node-02|10.100.0.46|
|k3s-node-03|10.100.0.47|
|Public Pool|10.100.0.50-59|

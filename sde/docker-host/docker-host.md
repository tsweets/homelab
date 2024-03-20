Docker Host ====================================================
``` 
Hostname: docker.pbi.skyline.lan   
IP: xxx.xxx.xxx.xxx 
```

Overview
----------------------------------------------------
The SDE will contain a docker host that will run all of the docker based workloads. Portainer will be used as a front end gui to view/manage containers

Dependencies
----------------------------------------------------
- VM to Run Docker
- Ansible
- Debian 12 Server 

Design
----------------------------------------------------
The docker host will need the following installed:
- docker
- docker compose
- portainer

#### VM
Debian will be the base OS. This VM will alot of resources. 
- 4 CPU
- 16GB RAM
- 32GB OS Disk
- NFS Mounted Data Dir (Maybe)

#### Docker
Using real docker, not podman. Latest


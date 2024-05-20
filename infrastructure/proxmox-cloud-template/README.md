Proxmox VM Setup
============================================


Ubuntu Cloud Images
--------------------------------------------
These docs will be using 23.10 Mantic Minotaur

https://cloud-images.ubuntu.com/mantic/current/

Proxmox needs the QCOW2 .img file
https://cloud-images.ubuntu.com/mantic/current/mantic-server-cloudimg-amd64.img

#### Create Template VM (Inside Cluster)
- qm create 9000 --memory 2048 --core 2 --name ubuntu-cloud-23-10 --net0 virtio,bridge=vmbr0
- cd /var/lib/vz/template/iso/  or /mnt/pve/cephfs/template/iso or /mnt/pve/ISO-SMB
- qm importdisk 9000 mantic-server-cloudimg-amd64.img ceph-pool
- qm set 9000 --scsihw virtio-scsi-pci --scsi0 YOUR STORAGE HERE:vm-9000-disk-0
- qm set 9000 --ide2 YOUR STORAGE HERE:cloudinit
- qm set 9000 --boot c --bootdisk scsi0
- qm set 9000 --serial0 socket --vga serial0

#### Update Cloud Init
- user = tsweets
- password set
- ssh key = my public key
- network change to dhcp

Custom Cloud Init Info
https://github.com/chris2k20/proxmox-cloud-init?tab=readme-ov-file

#### Convert to template   
Do this now before start

VM Templates
--------------------------------------------
With the template, clone to create a new VM. Use a "full clone"


#### Proxmox LXC Helper Scripts
https://helper-scripts.com/scripts
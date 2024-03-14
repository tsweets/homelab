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
- cd /var/lib/vz/template/iso/  or /mnt/pve/cephfs/template/iso
- qm importdisk 9000 mantic-server-cloudimg-amd64.img cephfs
- qm set 5000 --scsihw virtio-scsi-pci --scsi0 <YOUR STORAGE HERE>:vm-5000-disk-0
- qm set 5000 --ide2 <YOUR STORAGE HERE>:cloudinit
- qm set 5000 --boot c --bootdisk scsi0
- qm set 5000 --serial0 socket --vga serial0


VM Templates
--------------------------------------------

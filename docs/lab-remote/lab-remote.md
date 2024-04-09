Remote Test Lab
====================================================

Overview
----------------------------------------------------
This lab is for remote access testing. It consists of an isolated network and acts as a co-location site within the same location as the main network.


Proof of Concept
----------------------------------------------------
Using an SBC (ZimaBoard with dual NICs), will install OpnSense. This will act as a gateway. On the LAN side, a Server will be directly connected.   
Features:  
1. Wireguard VPN
2. Proxmox Server
3. Remote Desktop (Virtual)
4. Cloudflare Tunnel for Hosted Services


Production
----------------------------------------------------
1. Replace SBC with Unifi Cloud GW Ultra
2. Add Wifi

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
Default             10.222.1.0/24   VLAN: 1
Management          10.33.1.0/24    VLAN: 33
Skyline Classic     10.220.1.0/24   VLAN: 220
Cloud               10.107.0.0/24   VLAN: 107
InternetOfThings    192.168.40.0/24 VLAN: 40
--------
Need to Add
PBI                 x.x.x.x/x       VLAN: x
PBI SAN             x.x.x.x/x       VLAN: x   
```

#### PBI Lab Domain
This is production quality Software Development Environment. Described [PBI Lab](docs/lab-pbi/lab-pbi.md)
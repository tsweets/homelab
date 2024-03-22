dns
====================================================
``` 
Hostname: ns1.pbi.skyline.lan   
IP: 10.150.0.2 
```

Overview
----------------------------------------------------
The SDE will have its own internal DNS for the the domain of pbi.skyline.lan and skyline-lab.com

Dependencies
----------------------------------------------------
- VM to run DNS
- Ansible
- Ubuntu 23.10 Server
- DNS Entry
- APT Mirror 

Design
----------------------------------------------------
Need to decide on software - contenders:
- bind
- dnsmasq
- unbound
- Technitium


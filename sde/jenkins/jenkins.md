Jenkins CI/CD System
====================================================
``` 
Hostname: jenkins.pbi.skyline.lan   
IP: xxx.xxx.xxx.xxx 
```

Overview
----------------------------------------------------
The Continuous Integration/Continuous Deployment system used is classic [Jenkins](https://jenkins-ci.org).
Jenkins uses a model where there is a single master node controlling 1 or more build/worker nodes. 

Dependencies
----------------------------------------------------
- Docker Host
- Git Server
- DNS
- LDAP
- SSO
- SSL (Reverse Proxy)

Design (Master)
----------------------------------------------------
The master node will run via Docker Compose on a docker host, with the config stored in Git. 

#### Browser Access
Traffic to Jenkins will be encrypted via TLS and will use standard port (443)

#### Authentication
- Local Admin
- Centralized LDAP
- SSO

#### Backup
Jenkins data/config will be backed up daily
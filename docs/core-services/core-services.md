Core Services
====================================================
The entire home lab needs a set of always on core services. 
These include:
- Internal DNS
- LDAP User Auth
- Outgoing Email
- Homepage
- Root CA (ACME)
- Password Manager
- SSL Reverse Proxy
- Cloud Storage (Sync) 
- Rancher


These live in the core domain *.core.skyline-lab.com

Internal DNS
----------------------------------------------------
Deployment: Dedicated VM

Currently PiHole is the DNS implementation in use. Others to keep an eye are:
- Bind
- Technitum

Core will contain the source of truth DNS data however a dedicated Raspberry PI on the default network will be the main server for the environment. A third server maybe in a remote location.


LDAP User Auth
----------------------------------------------------
Deployment: Docker Host 

GLAuth https://glauth.github.io is a simple LDAP server that can run in a Docker container. 

connection  
ldap://docker.core.skyline-lab.com:389

Search DB  
dc=skyline,dc=lan

Bind DN  
cn=tsweets,dc=skyline,dc=lan

LDAP Class  
posixAccount

testing
```
 ldapsearch -LLL -H ldap://docker.core.skyline-lab.com:389 -D cn=devops,dc=skyline,dc=lan -W  -x -bdc=skyline,dc=lan cn=devops
```




Outgoing Email
----------------------------------------------------
Deployment: Docker Host (smtp-relay.skyline.lan old )
smtp-relay.core.skyline-lab.com NEW 11/17/24
email should be from - tony@skyline-lab.com (Domain is important)
Server: msmtp https://marlam.de/msmtp/
Docker Container: https://github.com/crazy-max/docker-msmtpd




Lab Homepage
----------------------------------------------------
Deployment: Docker Host

https://github.com/gethomepage/homepage/

Internal Root CA (Optional)
----------------------------------------------------
Deployment: Docker Host

SmallStep CA Server (step-ca) https://github.com/smallstep/certificates

Will act as an internal ACME server

Docker Container https://hub.docker.com/r/smallstep/step-ca

Password Manager
----------------------------------------------------
Deployment: Docker Host

Bitwarden/Vaultwarden


SSL Reverse Proxy
----------------------------------------------------
Deployment: Docker Host

Traefik 


Cloud Sync
----------------------------------------------------
Deployment: Docker Host

NextCloud

Rancher
----------------------------------------------------
Deployment: Single Node k3s cluster

Rancher is a management plane for K8S clusters. Ideally this should be deployed on its own cluster. Probably will do a single node k3s cluster
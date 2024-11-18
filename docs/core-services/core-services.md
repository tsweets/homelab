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
Deployment: Docker Host

Currently have an outgoing email relay. It uses exim4-daemon-light  
But take a look at msmtp https://marlam.de/msmtp/
That runs on the PI 10.222.1.5
AWS Help --> https://stackoverflow.com/questions/16756305/how-to-configure-msmtp-with-amazon-ses

Docker Container https://github.com/crazy-max/docker-msmtpd

Cheap Mail Service  https://purelymail.com  $10/yr
Sendgrid $0 for 100 per day
MailJet $0 for 200 per day

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
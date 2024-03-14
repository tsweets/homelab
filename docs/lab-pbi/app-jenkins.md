Jenkins
====================================================
Resources
----------------------------------------------------
|Host |Hostname |IP|
|----------|----------|----------|
|Jenkins Master |jenkins.pbi.skyline.lan |10.150.0.x|
|Jenkins Node 1 |jenkins-build1.pbi.skyline.lan |10.150.0.x|
|Jenkins Node 2 |jenkins-build2.pbi.skyline.lan |10.150.0.x|

Authentication
----------------------------------------------------
Local Administrator: xxxxxxx/creds in Bitwarden
Users: LDAP
Service Account: jenkins - Need SSH Key

Docker Run
----------------------------------------------------
```
docker run --rm --name jenkins -p 8080:8080 -p 50000:50000 -v /opt/jenkins:/var/lib/jenkins jenkins/jenkins:2.440.1-lts
```
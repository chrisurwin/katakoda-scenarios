Render port 80: https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/
# Install Rancher

The first step is installing the Rancher Server. 

In this instance we are going to run a Rancher Server and create a single node child cluster.

- Host 1 will function as server

First, we will start the Rancher Server container.

`docker run -d -p 80:80 -p 443:443 rancher/rancher:stable`{{execute HOST1}}

Render port 443: https://[[HOST_SUBDOMAIN]]-[[KATACODA_HOST]].environments.katacoda.com/


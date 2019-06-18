
# Install Rancher

The first step is installing the Rancher Server. 

In this instance we are going to run a Rancher Server and create a single node child cluster.

- Host 1 will function as server

First, we will start the Rancher Server container.

`systemctl restart docker;docker run -d -p 80:80 -p 443:443 rancher/rancher:master`{{execute HOST1}}

Wait for a minute and then try to access the host on the following URL:
https://[[HOST_SUBDOMAIN]]-443-[[KATACODA_HOST]].environments.katacoda.com/

After this set the password and accept the Rancher Server URL.


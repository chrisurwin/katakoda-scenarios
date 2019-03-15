#Install Rancher Server

First we need to add the helm repo that contains the Rancher chart
`helm repo add rancher-latest https://releases.rancher.com/server-charts/latest`

Next we are going to install cert-manager
`helm install stable/cert-manager \
  --name cert-manager \
  --namespace kube-system \
  --version v0.5.2`{{execute HOST1}}

And finally we are going to install the Rancher Server into the cluster
  `helm install rancher-latest/rancher \
  --name rancher \
  --namespace cattle-system \
  --set hostname=[[HOST_SUBDOMAIN]]-443-[[KATACODA_HOST]].environments.katacoda.com`{{execute HOST1}}

Wait for a minute and then try to access the host on the following URL:
https://[[HOST_SUBDOMAIN]]-443-[[KATACODA_HOST]].environments.katacoda.com/

When the UI is available you will need to set a password and the server-URL (just accept the prepopulated address)

Congratulations you have just installed Rancher with Helm!

As an additional step you can now add a child cluster to the Rancher Server by doing the following

* In the Rancher UI, click `Add Cluster`
* Click `custom` and give it a name and click `create`

* Check the `etcd` and `control plane` checkboxes and copy the `docker run` command at the bottom of the page and execute it on Host 2, then click `Done`

* Go back to the Rancher UI and you should see the cluster available in the Rancher Server UI
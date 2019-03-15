
# Install Kubernetes cluster

The first step is to set up a Kubernetes cluster for us to install Rancher Server in to.

In this example we are just going to set up a single node Kubernetes cluster using the Rancher RKE tool.

First we need to download this tool and make it executable:

`curl -sfL https://github.com/rancher/rke/releases/download/v0.1.17/rke -o rke && chmod +x ./rke`{{execute HOST1}}

We are then going to take advantage of an RKE setting that allows us to spin up a cluster on the local machine without creating any additional config. For further information and examples on using RKE to set up a production installation of Kubernetes please visit https://rancher.com/docs/rke/v0.1.x/en/installation/

`./rke up --local`{{execute HOST1}}

This will produce a `kube_config_cluster.yml` file in the local directory , we are going to copy this to `/root/.kube/config` so that we can use it to connect to the cluster via `kubectl`

`mkdir -p /root/.kube && cp kube_config_cluster.yml ~/.kube/config `{{execute HOST1}}

Now we can check the status of our cluster with `kubectl`

`kubectl get nodes`{{execute HOST1}}

Next we are going to install Helm
# Install Helm and Tiller

First we are going to install helm
`curl https://raw.githubusercontent.com/helm/helm/master/scripts/get | bash`{{execute HOST1}}


Next we need to create the tiller service account in the cluster

`kubectl -n kube-system create serviceaccount tiller`{{execute HOST1}}

You should see `serviceaccount/tiller created`

Next we will create the cluster role bingin for tiller
`kubectl create clusterrolebinding tiller \
  --clusterrole=cluster-admin \
  --serviceaccount=kube-system:tiller`{{execute HOST1}}

You should see `clusterrolebinding.rbac.authorization.k8s.io/tiller created`

Then initialise helm
`helm init --service-account tiller`{{execute HOST1}}

Next we are going to install Rancher Server
# Install Helm and Tiller

First we need to create the tiller service account in the cluster

`kubectl -n kube-system create serviceaccount tiller`{{execute HOST1}}

You should see `serviceaccount/tiller created`

Next we will create the cluster role bingin for tiller
`kubectl create clusterrolebinding tiller \
  --clusterrole=cluster-admin \
  --serviceaccount=kube-system:tiller`{{execute HOST1}}
You should see `clusterrolebinding.rbac.authorization.k8s.io/tiller created`

Next we are going to install helm
`curl https://raw.githubusercontent.com/helm/helm/master/scripts/get | bash`{{execute HOST1}}

Next we will create the cluster role binding
`kubectl create clusterrolebinding tiller --clusterrole=cluster-admin --serviceaccount=kube-system:tiller`{{execute HOST1}}

Then initialise helm
`helm init --service-account tiller`{{execute HOST1}}
You should see
`Creating /root/.helm`
`Creating /root/.helm/repository`
`Creating /root/.helm/repository/cache`
`Creating /root/.helm/repository/local`
`Creating /root/.helm/plugins`
`Creating /root/.helm/starters`
`Creating /root/.helm/cache/archive`
`Creating /root/.helm/repository/repositories.yaml`
`Adding stable repo with URL: https://kubernetes-charts.storage.googleapis.com`
`Adding local repo with URL: http://127.0.0.1:8879/charts`
`$HELM_HOME has been configured at /root/.helm.`

`Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.`

`Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.`
`To prevent this, run `helm init` with the --tiller-tls-verify flag.`
`For more information on securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation`
`Happy Helming!`


Next we are going to install Rancher Server
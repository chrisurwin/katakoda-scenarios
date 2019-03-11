# Install k3s

* Download and install k3s on Node-01
`curl -sfL https://get.k3s.io | sh -`{{execute HOST2}}

*  You can run the following command to check if the node is in Ready state (you might need to run the command a couple of times, can take up to 30 seconds for the node to register):
`k3s kubectl get node`{{execute HOST2}}
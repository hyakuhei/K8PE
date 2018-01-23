This readme describes the steps required to deploy wordpress as our first workload for testing with k8pe.

Note, this expects kubectl to be pointed at a valid kubernetes deployment.

This README is just a shortened version of the [collabnix blog on kubernetes with docker](http://collabnix.com/a-first-look-at-kubernetes-integrated-docker-for-mac-platform/)

It expects local-volmes.yaml to be present in this directory.

Create our PVs
```
kubectl create -f local-volumes.yaml
```

Verify the PVs
```
kubectl get pv
```

Create a secret for mysql
```
kubectl create secret generic mysql-pass --from-literal=password=k8pesecretpw
```

Verify the secret
```
kubectl get secrets
```

Deploy MySQL (which uses the PV and secrets we setup)
```
kubectl create -f mysql-deployment.yaml
```

Verify the MySQL pod:
```
kubectl get pods
```

Deploy wordpress - note the :type: Nodeport - this will be setup to receive traffic from outside the cluster. (Be careful around your kube/docker settings)
```
kubectl create -f wordpress-deployment.yaml
```

Verify the deployment by looking at the pods:
```
kubectl get pods
```

You should now be able to access the localhost install of WP on http://localhost -

# For Local Development Only

### When your test environment needs a ClusterDeployment set to "Installed" but you're tired of curling and setting the status manually.
This operator only does one thing, sets ClusterDeployment status. That's it.

Don't forget to install the service account, role, and rolebindings
```
kubectl create -f deploy/service_account.yaml
kubectl create -f deploy/role.yaml
kubectl create -f deploy/role_binding.yaml
```

### How do you run this?
Use 'operator-sdk up local' from within this operator's directory.

Alternatively, use it as part of your minikube cluster:
```
minikube start
kubectl config use-context minikube
cd $GOPATH/src/github.com/c-e-brumm/false-hive
oc create -f ./deploy
```

### Building the latest image
```
docker build -f build/Dockerfile . -t quay.io/openshift-sre/false-hive:latest
docker push quay.io/openshift-sre/false-hive:latest
```

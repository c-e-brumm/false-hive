# For Local Development Only

### When your test environment needs a ClusterDeployment set to "Installed" but you're tired of curling and setting the status manually.
This operator only does one thing, sets ClusterDeployment status. That's it.

Don't forget to install the service account, role, and rolebindings
```
kubectl create -f deploy/service_account.yaml
kubectl create -f deploy/role.yaml
kubectl create -f deploy/role_binding.yaml
```

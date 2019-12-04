## Kubernetes Training

### Notes
#### Kubernetes
- Node = Bare metal machine
- Add `context.namespace` in kube config to override default namespace
- `kubectly apply` should be used always (create / update)
- Use `-w` flag to watch the change in the resources

#### Pods
- Each pod have their own ip
- Pods communicated without NAT
- One node can have pods across NS

#### Replica Set
- Maintain a set of pod in a stable state
- Specify a number of pods, on deletion of a pod another pod automatically comes up

#### Deployment
- Useful for rolling deployements
  - If we want to move to a newer version of the app
- If we don't want rolling update for some reason, we can use `Recreate` strategy in `spec.strategy.type: Recreate`

### Example yaml for Pod
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
    containers:
    - name: myc
      image: nginx:alpine
```

### Commands
```sh
# Create pod from yaml (on default namespace)
kubectl create -f pod.yaml

# Create a namespace
kubectl create namespace mmayank

# Create pod on a given namespace
kubectl create -f pod.yaml -n mmayank

# Get list of pods on a NS
kubectl get pods -n mmayank

# Get list of pods with node, IP info
kubectl get pods -n mmayank -o wide

# Describe pod on a NS
kubectl describe pods -n mmayank

# Delete a pod
kubectl delete pod <pod-name>

# Create a replicaset
kubectl apply -f yaml/replicatset.yaml

# Delete a replicaset
kubectl delete rs <replicaset-name>

# Scale on the fly
kubectl scale deploy/nginx-deploy --replicas=2
```

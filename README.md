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
- Create pod from yaml (on default namespace)
```sh
kubectl create -f pod.yaml
```
- Create a namespace
```sh
kubectl create namespace mmayank
```

- Create pod on a given namespace
```sh
kubectl create -f pod.yaml -n mmayank
```
- Get list of pods on a NS
```sh
kubectl get pods -n mmayank
```
- Get list of pods with node, IP info
```sh
kubectl get pods -n mmayank -o wide
```
- Describe pod on a NS
```sh
kubectl describe pods -n mmayank
```
- Delete a pod
```sh
kubectl delete pod <pod-name>
```
- Create a replicaset
```sh
kubectl apply -f yaml/replicatset.yaml
```
- Delete a replicaset
```sh
kubectl delete rs <replicaset-name>
```

## Kubernetes Training

### Notes
- Node = Bare metal machine
- Each pod have their own ip
- Pods communicated without NAT
- One node can have pods across NS
- Add `context.namespace` in kube config to override default namespace

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

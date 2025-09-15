## Kubernetes

### Prerequisites
- A Kubernetes cluster and `kubectl` configured
- Container image for the app pushed to a registry (update `k8s_deployment_service.yaml` image field)

### Deploy
1. Edit `k8s_deployment_service.yaml` and replace `image: replace` with your image, for example `image: yourrepo/numeric:0.0.1`.
2. Apply manifests:
```bash
kubectl apply -f k8s_deployment_service.yaml
```
3. Get the Service details:
```bash
kubectl get svc devsecops-svc
```
If Service type is `NodePort`, use node IP and node port to access `http://<node-ip>:<node-port>/`.

### Optional: Security Scanning
- Run Kubesec scan against the manifest:
```bash
bash kubesec-scan.sh
```
- Deploy kube-scan for cluster risk analysis:
```bash
kubectl apply -f kube-scan.yaml
kubectl -n kube-scan get svc kube-scan-ui
```



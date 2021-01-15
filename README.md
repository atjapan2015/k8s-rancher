# k8s-rancher

install cert-manager,helm3,rancher
```
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.1.0/cert-manager.yaml
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest
helm repo update
kubectl create namespace cattle-system
helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=<your-domain-name>
```

modify deploy cattle-cluster-agent
```
kubectl edit deploy cattle-cluster-agent -n cattle-system
```

add
```
hostNetwork: true
```

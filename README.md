# sample-web-app

Sample web app based on nginx

```sh
k3d cluster create kube-lab --api-port 6550 -p "8080:80@loadbalancer" --agents 3

# k3d kubeconfig
export KUBECONFIG="$(k3d kubeconfig write kube-lab)"

#ArgoCD cluster -
k3d cluster create argocd-cluster --api-port 6551 -p "9090:443@loadbalancer" --agents 1

kubectl create ns argocd
kubectl -n argocd apply -f install.yaml

replace ghcr.io/dexidp/dex:v2.41.1 to docker.io/dexidp/dex:v2.41.1

kubectl port-forward svc/argocd-server -n argocd 8080:443

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
admin/argocdadmin
```

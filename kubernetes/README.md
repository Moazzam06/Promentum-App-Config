kubectl apply -k overlays/development

kubectl apply -k overlays/production

======================================================================================


# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

kubectl -n argocd get secret argocd-initial-admin-secret -o yaml
# you can change and delete init password

echo VDFxazdlTGpaTk5pSjVHLQ== | base64 --decode
T1qk7eLjZNNiJ5G-
==========================================================================================
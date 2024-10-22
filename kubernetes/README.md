kubectl apply -k overlays/development

# run ArgoCD on server
kubectl apply -f application.yaml

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

echo MnNnMXg0cXo1cnhCSE9mbQ== | base64 --decode
2sg1x4qz5rxBHOfm
==========================================================================================
doctl apps update 00337ea7-165c-4410-8881-39f4e4ee2bfa --spec ./webapp-spec.yml || doctl apps create --spec ./webapp-spec.yml  
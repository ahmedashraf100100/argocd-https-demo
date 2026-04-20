# argocd-https-demo
=============================================
# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
=============================================
# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 5050:443 -n argocd
=============================================
# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
# you can change and delete init password
=============================================
git config --global --add safe.directory /home/azureuser/Downloads/argocd-https-demo
sudo chown -R azureuser:azureuser /home/azureuser/Downloads/argocd-https-demo

git status
git add . 
git commit
git push 
kubectl apply -f application.yaml
=============================================
kubectl edit deployment -n myapp
# change the number of replicas 

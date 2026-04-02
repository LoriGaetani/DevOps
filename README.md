```
kubectl create namespace argocd
kubectl apply -n argocd --server-side --force-conflicts -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
```k get pods -n argocd```
Per accedere alla UI bisogna fare port forwarding del server: ``` kubectl port-forward -n argocd svc/argocd-s
erver 8080:443```
Per accedere alla dashboard lo username è admin e la passowrd viene automaticamente generata e salvanta in un k8s secret -> ```k get secret argocd-initial-admin-secret -n argocd -o yaml``` e poi fare ```echo password | base64 --decode```

A questo punto bisogna definire il file di configurazione di ArgoCD.

Poi applicare il file ```kubectl apply -f argocd.yaml```
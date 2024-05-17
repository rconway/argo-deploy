# EOEPCA ArgoCD App-of-apps

Login to argocd...

```
argocd login argocd.guide.svc.rconway.uk
  Username: admin
  Password: <admin-password>
```

Create `eoepca` argocd project...

```
argocd proj create PROJECT -f https://raw.githubusercontent.com/rconway/argo-deploy/develop/argocd/project.yaml
```

Create app-of-apps...

```
argocd app create eoepca \
  --project eoepca \
  --dest-namespace argocd \
  --dest-server https://kubernetes.default.svc \
  --repo https://github.com/rconway/argo-deploy \
  --path argocd \
  --revision develop \
  --sync-policy automated \
  --auto-prune \
  --self-heal
```

# openshift-configs

Dépôt GitOps des configmaps Openshift, source de vérité pour argo. Il contient les manifestes kube qui définissent l'état désiré du cluster.

## Contenu du dossier

- **`namespace.yaml`** : Définit le namespace `aisecops`.
- **`configmaps/`** : Configurations des serveurs. **Ce sont les seuls fichiers que l'agent IA est autorisé à modifier.**
- **`deployments/`** : Déploiements et services Kubernetes (chaque serveur y monte ses ConfigMaps comme volumes).
- **`argocd/`** : Configuration de l'application ArgoCD (exclue de la synchronisation automatique).

## Commandes utiles

Recréer l'application ArgoCD manuellement :

```bash
kubectl apply -f openshift-configs/argocd/application.yaml
```

Accès UI :

```
kubectl port-forward svc/argocd-server -n argocd 8888:443
```

Chaque serveur a un Deployment qui monte ses configmaps comme volumes 

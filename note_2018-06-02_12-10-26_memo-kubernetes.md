# Mémo Kubernetes

## Commandes utiles

Changer de contexte:     

	$ kubectl config set-context --current --namespace=<name-of-namespace>



## Désactiver le swap est indispensable

Si les composants maitres ne sont pas gérés:     


	$ sudo vim /etc/fstab

	--> Commenter la ligne swap


## Supprimer des ressources kustomize

	$ kustomize build overlays/ava-staging | kubectl delete -f -



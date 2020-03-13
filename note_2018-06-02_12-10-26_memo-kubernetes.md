# Mémo Kubernetes

## Désactiver le swap est indispensable

	$ sudo vim /etc/fstab

	--> Commenter la ligne swap


## Supprimer des ressources kustomize

	$ kustomize build overlays/ava-staging | kubectl delete -f -



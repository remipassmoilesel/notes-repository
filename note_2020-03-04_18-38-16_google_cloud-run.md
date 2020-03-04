# KNative vs Kubernetes

## Cloud run VS Kubernetes

**+ Cloud run**:
- Facilité de déploiement mono conteneur
- Export KNative

**- Cloud run**:
- Contraintes sur les conteneurs: 2 GB RAM, temps de calcul limité à une requête, etc ... (voir contrat conteneur)
- Tâches de calcul asynchrone: semble lié à d'autres services Google (Cloud Tasks), ce qui augmente l'adhérence au provider de cloud
- API propriétaire: le changement de fournisseur Cloud demande du temps de développement (mais exportaton open source KNative)

**+ Kubernetes**:
- Gestion des états: disque persistent, configurations, etc ...
- Contraintes sur les conteneurs personnalisables
- Communication interconteneur facilitée
- API open source: changement de fournisseur Cloud avec peu de développement

**- Kubernetes**:
- Courbe d'apprentissage


## Ressources

- Contrat de conteneur Cloud Run: https://cloud.google.com/run/docs/reference/container-contract




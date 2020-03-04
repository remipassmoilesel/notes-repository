# Google Cloud Run

Plateforme propriétaire de déploiement serverless.

## Déploiement hello world

	$ gcloud builds submit --tag gcr.io/PROJECT_ID/helloworld --project PROJECT_ID
	$ gcloud run deploy --image gcr.io/PROJECT_ID/helloworld --platform managed --project PROJECT_ID


## Ressources

- Contrat de conteneur: https://cloud.google.com/run/docs/reference/container-contract


## Cloud run VS Kubernetes

**+ cloud run**:
- Facilité de déploiement mono conteneur

**- Cloud run**:
- Contraintes sur les conteneurs: 2 GB RAM, temps de calcul limité à une requête, etc ... (voir contrat conteneur)
- Tâches de calcul asynchrone: semble lié à d'autres services Google (Cloud Tasks), ce qui augmente l'adhérence au provider de cloud
- API propriétaire: le changement de fournisseur Cloud demande du temps de développement (bien qu'utilisable une version open source, KNative)

**+ Kubernetes**:
- Souplesse d'utilisation
- Contraintes sur les conteneurs personnalisables
- Communication inter conteneur facilitée
- API open source: changement de fournisseur Cloud avec peu de développement

**- Kubernetes**:
- Courbe d'apprentissage


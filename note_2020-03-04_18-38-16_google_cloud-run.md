# Google Cloud Run

Plateforme propriétaire de déploiement serverless.

Limites: https://cloud.google.com/run/docs/reference/container-contract


## Déploiement hello world

	$ gcloud builds submit --tag gcr.io/PROJECT_ID/helloworld --project PROJECT_ID
	$ gcloud run deploy --image gcr.io/PROJECT_ID/helloworld --platform managed --project PROJECT_ID



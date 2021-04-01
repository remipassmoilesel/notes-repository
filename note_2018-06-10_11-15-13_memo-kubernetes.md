# Mémo Kubernetes

## Kubectl

### Commandes générales

Lister tous les types de ressources et leur raccourcis:

	$ kubectl config set-context --current --namespace=<name-of-namespace>

    $ kubectl get events
    $ kubectl api-resources
    $ kubectl get all --all-namespaces
    $ kubectl get pods
    $ kubectl get pod podname -o yaml

	$ kubectl port-forward pod-name 8080
	$ kubectl port-forward svc/name 8080

    $ kubectl apply -f https://...
    $ kubectl apply -f path/to/local

    $ kubectl logs -f podname     
    $ kubectl logs -f -l label=value      

    $ kubectl config view
    $ kubectl config get-contexts
    $ kubectl config use-context context-name


### Pods

Afficher les pods:

	$ kubectl get pods

Obtenir un shell:

	$ kubectl exec -ti podname bash

Inspecter un pod:

	$ kubectl get pods podname -o json 

Obtenir les logs d'un pod:

	$ kubectl logs podname  


### Deployments

Scaler un deployment

    $ kubectl scale deployment --replicas 3 kubernetes-dashboard -n kube-system     


### Services

Afficher et décrire un service:

    $ kubectl get services
    $ kubectl describe service servicename

Créer un service:

    $ kubectl expose 

Afficher un déploiement:

    $ kubectl describe deployment kubernetes-dashboard -n kube-system


## Prune des pods evicted

    $  kubectl get pods --all-namespaces -ojson | jq -r '.items[] | select(.status.reason!=null) | select(.status.reason | contains("Evicted")) | .metadata.name + " " + .metadata.namespace' | xargs -n2 -l bash -c 'kubectl delete pods $0 --namespace=$1'


### Configuration

Afficher la configuration courante:
 
    $ kubectl config view

            
### Proxy et port forward

#### Proxy 

Créer un proxy vers l'API Kubernetes:

    $ kubectl proxy --port=8080 &    
    
    $ curl http://localhost:8080/api/
    {
      "versions": [
        "v1"
      ]
    }
 
On peut utiliser ensuite le dashboard à l'addresse: http://127.0.0.1:8001/ui/


#### Forward

Forward de port vers un pod:

    # /!\ Très sensible au namespace

    $ kubectl port-forward -n $namespace $pod_name_or_service $host_port:$target_port 
    $ kubectl port-forward -n spring-k8s-demo gateway-release1-spring-k8s-demo-5ccb7d9f5d-cqg77 8080:8080 

Le port hôte peut être omis, un port au hasard sera choisi:

    $ kubectl port-forward $podname :80


## Helm 2

### Commandes générales

    $ helm init
    $ helm reset


### Initialisation et destruction

Créer un déploiement tiller sur un cluster:

    $ helm init

Prendre la main sur un pod existant:

    $ helm init --client-only

Détruire un déploiement tiller:

    $ helm reset


Attendre qu'un déploiement soit prêt:

    $ helm upgrade --wait --timeout 500 ...


## Kustomize

Supprimer toutes les ressources:     

	$ kustomize build overlays/ava-staging | kubectl delete -f -


## Recommendations pour installer Kubernetes

Désactiver le swap est indispensable si les composants maitres ne sont pas gérés:     

	$ sudo vim /etc/fstab

	--> Commenter la ligne swap



# TP Kubernetes - Minikube

## Objectif
Déployer une application Docker sur Kubernetes (Minikube), exposer le service et tester via navigateur.


## Image Docker
lakshan814/myservice:1


## Commandes utilisées


- Vérifier le cluster
kubectl get nodes

- Créer le deployment
kubectl create deployment myservice --image=lakshan814/myservice:1

- Voir les pods
kubectl get pods

- Détails d’un pod
kubectl describe pod <pod-name>

- Accès au container
kubectl exec -it <pod-name> -- /bin/bash

- Exposer le service
kubectl expose deployment myservice --type=NodePort --port=8080

- Voir les services
kubectl get svc

- Accéder à l’application
minikube service myservice --url
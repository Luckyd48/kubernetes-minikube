# TP Kubernetes - Minikube

## Objectif
Déployer une application Docker sur Kubernetes (Minikube), exposer le service et tester via navigateur.

## Image Docker
lakshan814/myservice:1

## Commandes utilisées

Vérifier le cluster -- kubectl get nodes  
Créer le deployment -- kubectl create deployment myservice --image=lakshan814/myservice:1  
Voir les pods -- kubectl get pods  
Détails d’un pod -- kubectl describe pod  
Accès au container -- kubectl exec -it myservice -- /bin/bash  
Exposer le service -- kubectl expose deployment myservice --type=NodePort --port=8080  
Voir les services -- kubectl get svc  
Accéder à l’application -- minikube service myservice --url  

Scaling et Load Balancing  
Vérifier les deployments -- kubectl get deployments  
Voir les pods actifs -- kubectl get pods  
Scaler l’application -- kubectl scale --replicas=2 deployment/myservice  
Vérifier le scaling -- kubectl get deployments  
kubectl get pods  

Rolling Updates  
Mettre à jour l’image -- kubectl set image deployments/myservice myservice=lakshan814/myservice:1  
Suivre le déploiement -- kubectl rollout status deployment/myservice  
Rollback -- kubectl rollout undo deployment/myservice  

Création avec fichiers YAML  
Appliquer le deployment -- kubectl apply -f myservice-deployment.yml  
Appliquer le service NodePort -- kubectl apply -f myservice-service.yml  
OU service LoadBalancer -- kubectl apply -f myservice-loadbalancing-service.yml  
Vérifier les ressources -- kubectl get all  

Ingress  
Activer ingress -- minikube addons enable ingress  
Vérifier ingress controller -- kubectl get pods -n ingress-nginx  
Appliquer ingress -- kubectl apply -f ingress.yml  
Récupérer l’adresse ingress -- kubectl get ingress  
Modifier le fichier hosts -- 127.0.0.1 myservice.info  
Accéder à l’application -- http://myservice.info  

Nettoyage  
Supprimer le service -- kubectl delete service myservice  
Supprimer le deployment -- kubectl delete deployment myservice  
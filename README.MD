# Sample nodejs based web app
Simple NodeJS based web app to play around.

## Build docker image
docker build -t weebeetester/sample-node-web-app:latest .

## Push to image repository
docker image push --all-tags weebeetester/sample-node-web-app



## Create deployment 
kubectl create deployment samplenodewebapp --image weebeetester/sample-node-web-app

## Create Service 
kubectl expose deployment samplenodewebapp --type NodePort --port 8080

## Get IP[Minikube] and open/curl the app in browser OR on cmd line
minikube ip
http://${IP}:${NODEPORT}/

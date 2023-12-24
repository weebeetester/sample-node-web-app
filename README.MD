# Sample nodejs based web app
Simple NodeJS based web app to play around.

## Build docker image
>docker build -t weebeetester/sample-node-web-app:latest .

## Run docker image
>docker run -p 8080:8080 weebeetester/sample-node-web-app

## Push to image repository
>docker image push --all-tags weebeetester/sample-node-web-app

## Create deployment imperatively
>kubectl create deployment samplenodewebapp --image weebeetester/sample-node-web-app

## Create Service imperatively
>kubectl expose deployment samplenodewebapp --type NodePort --port 8080

## OR create deployment and service declaratively (see devops folder)
>kubectl apply -f k8s-deployment.yml

>kubeclt apply -f k8s-service.yml

## Get IP[Minikube] and open/curl the app in browser OR on cmd line
minikube ip
http://${IP}:${NODEPORT}/

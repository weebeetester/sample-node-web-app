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

## Open the app in browser OR on cmd line
minikube ip
http://192.168.64.4:31035/

sample-node-web-app   main ● ?  curl 192.168.64.4:31035                                                      ✘
Hello World from nodejs based web app%
 sample-node-web-app   main ● ? 

sample-node-web-app   main ● ?  kubectl exec -it samplenodewebapp-7794c4559f-m9dj8 -- bash
root@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app# curl localhost:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app# curl http://localhost:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app# cat /etc/hosts
# Kubernetes-managed hosts file.
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
fe00::0	ip6-mcastprefix
fe00::1	ip6-allnodes
fe00::2	ip6-allrouters
10.244.0.9	samplenodewebapp-7794c4559f-m9dj8
root@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app#
root@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app# curl samplenodewebapp:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app#
root@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app# curl 10.108.218.183:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-m9dj8:/usr/src/app#




 sample-node-web-app   main ● ?  kubectl create deployment samplenodewebapp --image weebeetester/sample-node-web-app
deployment.apps/samplenodewebapp created
 sample-node-web-app   main ● ?  kubectl expose deployment samplenodewebapp --port 8080
service/samplenodewebapp exposed
 sample-node-web-app   main ● ?  kubectl get all
NAME                                    READY   STATUS    RESTARTS   AGE
pod/samplenodewebapp-7794c4559f-vsn5b   1/1     Running   0          24s

NAME                       TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
service/kubernetes         ClusterIP   10.96.0.1        <none>        443/TCP    9h
service/samplenodewebapp   ClusterIP   10.106.169.245   <none>        8080/TCP   5s

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/samplenodewebapp   1/1     1            1           24s

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/samplenodewebapp-7794c4559f   1         1         1       24s
 sample-node-web-app   main ● ?  kubectl exec -it samplenodewebapp-7794c4559f-vsn5b -- bash
root@samplenodewebapp-7794c4559f-vsn5b:/usr/src/app# curl localhost:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-vsn5b:/usr/src/app# curl samplenodewebapp:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-vsn5b:/usr/src/app# curl 10.106.169.245:8080
Hello World from nodejs based web approot@samplenodewebapp-7794c4559f-vsn5b:/usr/src/app#
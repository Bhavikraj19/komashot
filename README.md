# komashot

AWS

sudo apt update
sudo apt-get install docker.io
sudo apt install git 
sudo apt install nano
git clone link
cd aws 
nano Dockerfile:
FROM nginx:alpine
COPY . /usr/share/nginx/html
sudo docker build -t mywebapp .
sudo docker run -d -p 80:80 mywebapp

-------------------------------------------------------------------------------------------

scaling of a container named mysql through kubernetes

step 1 : open docker ON the kubernetes
step 2 : open powershell 
1. minikube start
2. kubectl create deployment mynginx --image=nginx
if failed try (kubectl delete deployment mynginx)
4. then try step 2
5. kubectl get deployments
6. kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80
7. if failed try (kubectl get deployments)
8. (kubectl get pods)
9. (kubectl get svc)
10. (kubectl delete svc mynginx)
11. (kubectl delete deployment mynginx)
12. (kubectl create deployment mynginx --image=nginx)
13. (kubectl get deployments)
14. (kubectl get pods)
15.  kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80
16.  kubectl scale deployment mynginx --replicas=4
17.  (kubectl get deployments)
18.  (kubectl get pods)
19.  kubectl port-forward svc/mynginx 8081:80
20.  running on localhost:8081

 -------------------------------------------------------------------------------------

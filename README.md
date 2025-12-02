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


 Illustrate the monitoring of a project through nagios

step 1 : open docker ON the kubernetes
step 2 : open powershell 
then 
1. docker pull jasonrivers/nagios:latest

2. docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest

3. open local host 8888
4. username nagiosadmin
5. password nagios

6. open another powershell 
1. docker ps 
2. docker stop nagiosdemo
3. docker rm nagiosdemo(delete from the system)
4. to delete docker image (docker image)
(docker rmi paste the path )

----------------------------------------------------------------------------------------------------------------

create and configure a jenkins freestyle project to build ajava application using maven

step 1 open jenkins 
step 2 open new item on the left side
step 3 Enter an item name : SampleMavenProject_build
step 4 click on freestyle project
step 5 click on ok
step 6 Source code management 
Click on git (Give the repository URL For it from github)
Credentials none or u can give for it 
step 7 Branches to build ( */main)
step 8 Build step under the ADD build steps (Select INvoke top-level maven targets)
(maven version = MAVEN_HOME)
(Goals = clean)
ADD build steps (Invoke top - level maven targets)
(MAVEN version = MAVEN_HOME)
(Goals = install)
step 9 POST BUILD ACTION under that add post build action 
(archive the artifacts)
(file to archive = **/*)
ADD POST BUILD ACTION 
(build other projects)
(Projects to build = SampleMavenProject_test
(Select Trigger only if build is stable)
step 10THEN CLICK ON APPLY AND SAVE 
step 11 click on dashboard click on new item 

step 1ENter an item name = SampleMavenProject_test
step 2 click on Freestyle project 
step 3 Build Environment (Delete workspace before build starts)
step 4 Click on Build Steps under that Add build step
(copy artifacts from another project)
(project name = SampleMavenProject_build)
(Click on stable build only)
(Artifacts to copy = **/*)
step 5 Click on add build step
(invoke top-level maven targets)
(Maven version = MAVEN_HOME)
(Goals = test)
Step 6 Post build Actions under that Add post build action
(Archive the artifacts)
(Files to archive = **/*)
Step 7 CLICK ON APPLY AND SAVE
step 8 go to the dash board 


Click on the + button there 
New View Name = SampleMavenProject_pipeline
TYpe = Build Pipeline view
Step 1 Click on create
step 2 pipeline flow 
Select initialJob = SampleMavenProject_build
step 3 CLICK ON APPLY AND OK


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

BUILDING THE CI/CD  FREESTYLE PIPELINE USING JENKINS FOR MAVEN WEB PROJECT 

step 1 open jenkins 
step 2 open new item on the left side
step 3 Enter an item name : SampleMavenWebProject_build
step 4 click on freestyle project
step 5 click on ok
step 6 Source code management 
Click on git (Give the repository URL For it from github)
Credentials none or u can give for it 
step 7 Branches to build ( */main)
step build triggers (Poll SCM)
(schedule * * * * *)
step 8  Build steps ( Invoke top-level Maven Targets)
(maven version = MAven_Home)
(Goals = clean)
AGAIN CLICK ON ADD BUILD STEP ( Invoke top-level Maven Targets)
(maven version = MAven_Home)
(Goals = install)
step 9 Post build actions ( Archive the artifacts)
(Files to archive = **/*)
ADD POST BUILD ACTION (build other projects)
(Projects to build = SampleMavenWebProject_test)



step 1ENter an item name = SampleMavenWebProject_test
step 2 click on Freestyle project 
step 3 click on OK
step 4 Build Environment (Delete workspace before build starts)
step 5 Click on Build Steps under that Add build step
(copy artifacts from another project)
(project name = SampleMavenWebProject_build)
(Which build = Click on stable Build)
(Artifacts to copy = **/*)
Step 6 Click on add Build step (invoke top-level Maven Targets)
(maven version = MAVEN_HOME)
(Goals = test)
step 7 POST BUILD ACTION ( Archive the artifacts)
(Files to archive = **/*)
Click on add post build action ( Build other projects)
(Projects to build = SampleMavenWebProject_deploy)
step 8 click on apply nd save 



step 1ENter an item name = SampleMavenWebProject_deploy
step 2 click on Freestyle project 
step 3 click on OK
step 4 Build Environment (Delete workspace before build starts)
step 5 Click on Build Steps under that Add build step
(copy artifacts from another project)
(project name = SampleMavenWebProject_test)
(Which build = Click on stable Build)
(Artifacts to copy = **/*)
Step 6 Click on add Build step (deploy war/ear to a container)
(WAR/EAR files = **/*.war)
(context path = samplewebprojectmaven)
Step 7 add container Tomcat 9
Credentials add open the eclippse then on tomcat you will be finding the admin adn password 
enter that username and password in that
give tomcat url (Localhost tomcat 8083)
Step 8 CLICK ON APPLLY AND SAVE


Click on the + button there 
New View Name = SamplewebProject_pipeline
TYpe = Build Pipeline view
PIPEline flow = Samplemavenwebproject_build
click on apply and ok

# komashot
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


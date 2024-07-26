CloudService#@884
# EC2 

sudo -i
apt update && apt upgrade -y
snap install docker

docker pull cyrdominicytos/science-api:latest

docker pull cyrdominicytos/science-mysql:latest
![[Pasted image 20240323235127.png]]



docker run -d -p 443:8080 --name api_container cyrdominicytos/science-api

docker run -p 80:3306 -e MYSQL_ROOT_PASSWORD=root cyrdominicytos/science-mysql

Arret et suppression des conteneurs
docker rmi $(docker images -a -q)

0159068339

# Docker hub



Event  (descritption, longgitude , latiutude)

# Donner accès via IP à mon pc 
netsh advfirewall firewall add rule name="Open Port 8080" dir=in action=allow protocol=TCP localport=8080

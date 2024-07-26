 
# Supprimer toutes les images docker de votre système
docker rmi -f $(docker images -q)

![[Pasted image 20240321050506.png]]


pousser une image sur docker hub

avoir les meme nom en local ou creer un tag sur le nom local vers celui de  docker hub
 docker tag mysql cyrdominicytos/science-mysql-container  
 pousser
 docker push cyrdominicytos/science-mysql-container

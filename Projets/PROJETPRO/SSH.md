### Vérification du port SSH configuré

manuel
sudo vi /etc/ssh/sshd_config
#Port 22

auto cmd

sudo systemctl restart ssh

### Vérification des connexions SSH

Pour vérifier que le serveur SSH écoute sur le port configuré, vous pouvez utiliser `netstat` ou `ss`
sudo netstat -tuln | grep ssh
# ou
	sudo ss -tuln | grep ssh

### Configuration du pare-feu

Assurez-vous que le port SSH est autorisé dans le pare-feu. Par exemple, si vous utilisez `ufw` :

sudo ufw allow 2222/tcp
sudo ufw reload

Redemarrer ssh

sudo systemctl restart ssh


sudo systemctl restart ssh

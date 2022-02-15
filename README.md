# Personal Cloud

```sh
	# Setup Server
	adduser $USER
	usermod -aG sudo $USER
	# Install Docker
	sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
	sudo apt-get update
	sudo apt-get install docker-ce
	# Add user to Docker Group
	sudo groupadd docker
	sudo usermod -aG docker $USER
	newgrp docker
	# Install Docker Compose
	sudo curl -L https://github.com/docker/compose/releases/download/1.23.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
	sudo chmod +x /usr/local/bin/docker-compose
	# Setup docker Directory
	mkdir ~/docker
	sudo setfacl -Rdm g:docker:rwx ~/docker
	sudo chmod -R 775 ~/docker
	touch ~/docker/.env
	touch ~/docker/docker-compose.yml
	mkdir ~/docker/secrets
	# Set up for Traefik 2
	touch ~/docker/secrets/httpassword
	# Use HTTP Password Generator (htpasswd file) and fill ^
	mkdir ~/docker/appdata
	mkdir ~/docker/appdata/traefik2
	mkdir ~/docker/appdata/traefik2/acme
	touch ~/docker/appdata/traefik2/acme/acme.json
	chmod 600 ~/docker/appdata/traefik2/acme/acme.json
	touch ~/docker/appdata/traefik2/traefik.log
```

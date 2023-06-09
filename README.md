# Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
```

# Add Docker’s official GPG key:
```
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

# Use the following command to set up the repository:
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

# Update the apt package index:
```
sudo apt-get update
```

# List the available versions:
```
apt-cache madison docker-ce | awk '{ print $3 }'
```

# Select the desired version and install:
```
VERSION_STRING=5:23.0.1-1~ubuntu.18.04~bionic
sudo apt-get install docker-ce=$VERSION_STRING docker-ce-cli=$VERSION_STRING containerd.io docker-buildx-plugin docker-compose-plugin
```

# Manage Docker as a non-root user
## Create the docker group.
```
sudo groupadd docker
```

## Add your user to the docker group
```
sudo usermod -aG docker $USER
```

## Log out and log back in so that your group membership is re-evaluated.
(maybe it's necessary to restart)
```
newgrp docker
```

## To remove the following error
```
WARNING: Error loading config file: /home/user/.docker/config.json -
stat /home/user/.docker/config.json: permission denied
```
Execute:
```
sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
sudo chmod g+rwx "$HOME/.docker" -R
```

# Configure Docker to start on boot with systemd
## Enable
```
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

## Disable
```
sudo systemctl disable docker.service
sudo systemctl disable containerd.service
```

# Documentação oficial:
- https://docs.docker.com/engine/install/ubuntu/
- https://docs.docker.com/engine/install/linux-postinstall/

# Versão do Ubuntu WSL2
```
lsb_release -a
```

- No LSB modules are available.
- Distributor ID: Ubuntu
- Description:    Ubuntu 18.04.6 LTS
- Release:        18.04
- Codename:       bionic

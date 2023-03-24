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

Documentação oficial:
https://docs.docker.com/engine/install/ubuntu/

# Versão do Ubuntu WSL2
```
lsb_release -a
```

- No LSB modules are available.
- Distributor ID: Ubuntu
- Description:    Ubuntu 18.04.6 LTS
- Release:        18.04
- Codename:       bionic

# 5ire Chain Node Guide

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Recommended system requirements: 
- 16 CPU
- 32 Gb RAM
- 100 GB SSD
- OS: Ubuntu 20.04
- ports 30333

---
1. Update & upgrade
```bash
sudo apt update && sudo apt upgrade

sudo apt install -y curl git jq lz4 build-essential unzip
```
2. Installing docker and docker compose:
```bash
sudo apt install -y ca-certificates curl gnupg lsb-release 

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io

sudo usermod -aG docker $USER

newgrp docker
```

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```
3. Download the docker image
```bash
docker pull 5irechain/5ire-thunder-node:0.12
```
4. Running the docker container
```bash
docker run -d -p 30333:30333 5irechain/5ire-thunder-node:0.12 --port 30333 --no-telemetry --name my-5ire-validator  --chain /5ire/thunder-chain-spec.json  --bootnodes /ip4/3.128.99.18/tcp/30333/p2p/12D3KooWSTawLxMkCoRMyzALFegVwp7YsNVJqh8D2p7pVJDqQLhm --pruning archive --validator
```
---
Logs:
```bash
docker container ls

docker container logs <CONTAINED_ID>
```
<CONTAINED_ID> - Your container name.

Fill out the form - https://docs.google.com/forms/d/e/1FAIpQLSd3ooW-aTKpH8BV4XB5rMptg7nZySxwv95fYOrF3Et6CHAO9w/viewform

# Elixir Protocol Node Guide

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Recommended system requirements: 
- 2 CPU
- 4 Gb RAM
- 40 GB SSD
- OS: Ubuntu 20.04


---

Installing docker:
```bash
. <(wget -qO- https://raw.githubusercontent.com/SecorD0/utils/main/installers/docker.sh)
```
Download Dockerfile:
```bash
wget https://testnet-1-files.elixir.finance/Dockerfile
```
Edit Dockerfile:
```bash
nano Dockerfile
```
Enter the metamask wallet address in ENV ADDRESS and the private key in ENV PRIVATE_KEY.

Build validator:
```bash
docker build . -f Dockerfile -t elixir-validator
```
Run node:
```bash
docker run -d --restart unless-stopped --name ev elixir-validator
```

You can check the functionality of the node on the website - https://metrics.elixir.finance/
-
Logs:
```bash
docker container ls
```
docker container logs <CONTAINED_ID>
<CONTAINED_ID> - Your container name.

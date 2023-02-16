# Elixir Protocol Node Guide

Recommended system requirements: 
- 2 CPU
- 4 Gb RAM
- 40 GB SSD
- OS: Ubuntu 20.04


Installing docker:

. <(wget -qO- https://raw.githubusercontent.com/SecorD0/utils/main/installers/docker.sh)

Download Dockerfile:
wget https://testnet-1-files.elixir.finance/Dockerfile

Edit Dockerfile:
nano Dockerfile

Enter the metamask wallet address in ENV ADDRESS and the private key in ENV PRIVATE_KEY.

Build validator:
docker build . -f Dockerfile -t elixir-validator

Run node:
docker run -d --restart unless-stopped --name ev elixir-validator


You can check the functionality of the node on the website - https://metrics.elixir.finance/

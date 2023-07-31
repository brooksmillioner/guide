# SHARDEUM NODE GUIDE

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Recommended system requirements: 
- 2 CPU
- 4 Gb RAM
- 40 GB SSD
- OS: Ubuntu 20.04

---
1. Install the necessary packages:
```
apt update && apt upgrade -y

sudo apt install make clang git pkg-config libssl-dev build-essential git gcc chrony curl jq ncdu bsdmainutils htop net-tools lsof fail2ban wget -y
```
2. Install docker and docker-compose:
```bash
sudo apt install docker.io -y

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```
3. Install node:
```bash
curl -O https://gitlab.com/shardeum/validator/dashboard/-/raw/main/installer.sh && chmod +x installer.sh && ./installer.sh
```
4. Run operator-cli and node:
```bash
cd ~/.shardeum
./shell.sh
operator-cli gui start
operator-cli start
```


5. Instead of <privatekey>, change it to your own:
```bash
echo -e <privatekey> | operator-cli stake 10
```
6. Instead of <adress>, change it to your own:
```bash
operator-cli stake_info <adress>
```

---
Delete node:
```bash
cd ~/.shardeum
./cleanup.sh
cd ~/
rm -rf .shardeum
rm installer.sh
```



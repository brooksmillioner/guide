# SHARDEUM NODE GUIDE

Last update Atomium 1.16.3 in 11.01.2025
Last update guide 13.01.2025

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Post incentivized testnet - https://x.com/shardeum/status/1841142290397741295


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
4. Web interface - https://your_node_ip:8080/
![image](https://github.com/user-attachments/assets/98da7bd0-de4a-4911-bdbb-6cbbca2ea6f3)

---
5.  Go to Discord - https://discord.gg/shardeum and request tokens for Metamask
![image](https://github.com/brooksmillioner/guide/assets/52867637/e61bb29c-b43e-40e9-88a9-aa9f052a810d)
---
6. Go to the site, connect your wallet, click Start Node, steak at least 10 $SHM - https://shardeum.org/incentivized-testnet/
![image](https://github.com/user-attachments/assets/2bd87ded-ac05-42af-a718-11b8a65a766e)
7. Confirm task completion
![image](https://github.com/user-attachments/assets/0ba0a378-20e6-4ea7-af9f-bae5ff6a0ea7)


---
Password change:
```bash
operator-cli gui set password <type_new_password__here>
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



# FARCASTER NODE GUIDE

Last update 1.16.2 in 29.10.2024
Last update guide in 13.01.2025

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Recommended system requirements: 
- 4 CPU
- 16 Gb RAM
- 200 GB SSD
- OS: Ubuntu 20.04

---
1. Install the necessary packages:
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install git-all -y && sudo apt full-upgrade -y

sudo apt install -y make clang git pkg-config libssl-dev build-essential git gcc chrony curl jq ncdu bsdmainutils htop net-tools lsof fail2ban wget

sudo apt install -y screen git zip unzip mc nano htop cron libyaml-dev iptables-persistent && dpkg -L iptables-persistent
```
2. Open ports
```
sudo mkdir -p /etc/iptables
sudo iptables-save | sudo tee /etc/iptables/rules.v4

sudo iptables -A INPUT -p tcp --dport 2281 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 2282 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 2283 -j ACCEPT
sudo iptables-save > /etc/iptables/rules.v4
sudo iptables -L -v -n

sudo ufw allow 2283/tcp
sudo ufw allow 2282/tcp
sudo ufw allow 2282/udp
sudo ufw allow 2283/udp
sudo ufw allow 3000/udp
sudo ufw allow 3000/tcp
```
3. Create screen session
```
screen -S Hubble
```
4. Install and start Farcaster mainnet node
```
curl -sSL https://download.thehubble.xyz/bootstrap.sh | bash
```
The system will ask following:

ETH_MAINNET_RPC_URL=your-ETH-mainnet-RPC-URL (you can take from https://www.alchemy.com) 
OPTIMISM_L2_RPC_URL=your-L2-optimism-RPC-URL (you can take from https://www.alchemy.com) 
HUB_OPERATOR_FID=your-fid (you can take from WarpCast - https://warpcast.com/~/invite-page/342012?id=107e8bb7 ) 

5. Check your node
Open your browser and insert you link with ip ``` http://123.123.123.123:3000 ```











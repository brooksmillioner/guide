# FARCASTER NODE GUIDE

Last update 1.10.3 in 13.01.2025

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

# CASCADIA NODE GUIDE

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Recommended system requirements: 
- 2 CPU
- 4 Gb RAM
- 40 GB SSD
- OS: Ubuntu 20.04

---
1. Install the necessary packages and update the "data":
```bash
apt update && apt upgrade -y 
apt install curl iptables build-essential git wget jq make gcc nano tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev -y
```
2. Install Go with the latest version:
```bash
ver="1.20.3" && \ 
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \ 
sudo rm -rf /usr/local/go && \ 
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \ 
rm "go$ver.linux-amd64.tar.gz" && \ 
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \ 
source $HOME/.bash_profile && \ 
go version
```
3. Install a node:
```bash
git clone https://github.com/cascadiafoundation/cascadia && cd cascadia 
git checkout v0.1.1 
make install
```
4. Download the genesis file:
```bash
wget -O $HOME/.cascadiad/config/genesis.json "https://anode.team/Cascadia/test/genesis.json"
```
5. Adding piers:
```bash
peers="893b6d4be8b527b0eb1ab4c1b2f0128945f5b241@185.213.27.91:36656"
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$peers\"/" $HOME/.cascadiad/config/config.toml
```
6. Configure StateSync:
```bash
SNAP_RPC=185.213.27.91:36657

LATEST_HEIGHT=$(curl -s $SNAP_RPC/block | jq -r .result.block.header.height); \ 
BLOCK_HEIGHT=$((LATEST_HEIGHT - 1000)); \ 
TRUST_HASH=$(curl -s "$SNAP_RPC/block?height=$BLOCK_HEIGHT" | jq -r .result.block_id.hash) 

echo $LATEST_HEIGHT $BLOCK_HEIGHT $TRUST_HASH 
sed -i.bak -E "s|^(enable[[:space:]]+=[[:space:]]+).*$|\1true| ; \ 
s|^(rpc_servers[[:space:]]+=[[:space:]]+).*$|\1\"$SNAP_RPC,$SNAP_RPC\"| ; \ 
s|^(trust_height[[:space:]]+=[[:space:]]+).*$|\1$BLOCK_HEIGHT| ; \ 
s|^(trust_hash[[:space:]]+=[[:space:]]+).*$|\1\"$TRUST_HASH\"| ; \ 
s|^(seeds[[:space:]]+=[[:space:]]+).*$|\1\"\"|" $HOME/.cascadiad/config/config.toml
```
7. Create a service file:
```bash
tee /etc/systemd/system/cascadiad.service > /dev/null <<EOF 
[Unit] 
Description=cascadiad 
After=network-online.target 

[Service] 
User=$USER 
ExecStart=$(which cascadiad) start 
Restart=on-failure 
RestartSec=3 
LimitNOFILE=65535 

[Install] 
WantedBy=multi-user.target 
EOF
```
8. Launch the node:
```bash
systemctl daemon-reload 
systemctl enable cascadiad 
systemctl restart cascadiad 
```
9. Checking the logs:
```bash
journalctl -fu cascadiad -o cat
```                                                            

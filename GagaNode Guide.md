# Gaga Node guide

Buy server - https://github.com/brooksmillioner/guide/blob/main/servers.md

Register - https://dashboard.gaganode.com/register?referral_code=kqzlupqhbf

# Further actions on the server

1. Update & upgrade
```bash
sudo apt-get update -y && sudo apt-get -y install curl tar ca-certificates
```
2. Download & install
```bash
curl -o app-linux-amd64.tar.gz https://assets.coreservice.io/public/package/22/app/1.0.3/app-1_0_3.tar.gz && tar -zxf app-linux-amd64.tar.gz && rm -f app-linux-amd64.tar.gz && cd ./app-linux-amd64 && sudo ./app service install
```
3. Start service
```bash
sudo ./app service start
```
4. Check app status
```bash
./app status
```
check gaganode status is RUNNING

5. Set token - Enter your token from the site, section Install & Run
```bash
sudo ./apps/gaganode/gaganode config set --token="YOURTOKEN"
```
6. Restart app
```bash
./app restart
```
Check https://dashboard.gaganode.com/user_node in a few minutes.
![image](https://github.com/brooksmillioner/guide/assets/52867637/8e599d86-83d8-405d-9c5e-9634b5e69d4c)

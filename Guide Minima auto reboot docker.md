# Guide Minima auto reboot docker

1. Go to user
```bash
su - minima
```
2. Going into the container
```bash
crontab -e
```
3. 
```bash
1 + enter 
```
4. After you have entered the container - Down to the bottom so that the input field was from a clean line 

5.
```bash
 * */12 * * * docker restart minima9001
```
 ctrl+х ( Y + Enter)

6. After checking again by entering the container with the command above under number 2

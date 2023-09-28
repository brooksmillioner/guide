# guide

Run PowerShell as an administrator on your PC and enter the following commands:
```bash
Set-ExecutionPolicy RemoteSigned
```
press y > enter
```
powershell -command "& { iwr https://raw.githubusercontent.com/brooksmillioner/nodes/main/subspacev2.ps1 -OutFile subspacev2.ps1 }"
```
install
```bash
. .\subspace.ps1
```

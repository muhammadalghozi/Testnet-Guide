# EXORDE TESTNET MANUAL

 * Explorer : https://explorer.exorde.network/
 * Discord  : https://discord.gg/SV22kgMCnr

#### Update First
```bash
apt update && apt upgrade -y
```
#### Install docker
```bash
apt install docker.io
```
#### Clone Directory Official
```bash
git clone https://github.com/exorde-labs/ExordeModuleCLI.git
```
```bash
cd ExordeModuleCLI
docker build -t exorde-cli .
```
#### Run Node
```bash
docker run -it --name Exorde exorde-cli -m YOUR_MAIN_ADDRESS -l 2
```
 1. For EXAMPLE : ``docker run -it --name Exorde exorde-cli -m 0x199d5ed7f45f4ee35960cf22eade2076e95b253f -l 2``
 2. After running like in the picture, please press the keyword CTRL + C
![image](https://user-images.githubusercontent.com/116246591/201244372-9b4bf3e6-2705-47d6-817c-c76235d74e97.png)

### Other Command
#### Check Logs
```bash
docker logs Exorde
```
#### Check logs constantly
```bash
docker logs --follow Exorde
```
#### Restart Docker
```bash
docker restart Exorde
```
#### Stop Docker
```bash
docker stop Exorde
```
### Delete Your Node
```bash
sudo  docker stop Exorde &&  sudo  docker  rm Exorde
sudo  rm -rf ExordeModuleCLI
```

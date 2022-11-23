# MiNIMA TESTNET NODE MANUAL

## Hardware Requirements
| Recommended | Specifications |
|----------|-------------------|
|CPU|2 Cores|
|RAM|4 GB DDR4 RAM|
|Storage|80 GB NVMe SSD|
|Bandwith|1 Tb|


#### Open Port
```bash
ufw allow ssh
ufw allow 9001,9002,9003,9004
ufw enable
```
#### Update
```bash
apt update && apt upgrade -y
```
#### Install Node
```bash
wget -O minimad.sh https://raw.githubusercontent.com/Megumiiiiii/minima-docker/main/minimad.sh && chmod +x minimad.sh && ./minimad.sh
```
![image](https://user-images.githubusercontent.com/116246591/203445745-4ba198a0-fa90-46b4-84f9-d62ef89b381c.png)

``Submit new password, click Enter, Y , Enter``
#### Run Node
```bash
docker run -d -e minima_mdspassword=123 -e minima_server=true -v ~/minimadocker9001:/home/minima/data -p 9001-9004:9001-9004 --restart unless-stopped --name minima9001 minimaglobal/minima:latest
```
#### Run Auto Updater
```bash
docker run -d --restart unless-stopped --name watchtower -e WATCHTOWER_CLEANUP=true -e WATCHTOWER_TIMEOUT=60s -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower
```
#### Open dAPP Using Your IP
``https://YourIPVPS:9003/``
![image](https://user-images.githubusercontent.com/116246591/203446071-14e9680e-8643-40d6-8c7f-be1e29ea41a8.png)

 * ``Enter Password and click Login : 123``
 * ``Choice Menu Incentive programs``
 
![image](https://user-images.githubusercontent.com/116246591/203446387-c72fcbe6-c234-4e94-91a1-970b1e6c0e16.png)

If don't work using [Click Here](https://incentive.minima.global/account/register?inviteCode=BLEVICKP)

#### Check Logs
```bash
docker logs -f minima9001
```

![image](https://user-images.githubusercontent.com/116246591/203446822-3118e653-686e-4999-9c39-b1b896183ffc.png)







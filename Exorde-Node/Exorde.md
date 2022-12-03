# EXORDE TESTNET MANUAL

 * Explorer : [Click Here](https://explorer.exorde.network/)
 * Discord  : [Click Here](https://discord.gg/SV22kgMCnr)

#### Update First
```bash
apt update && apt upgrade -y
```

#### Install docker
```bash
apt install docker.io
```

#### Run Node
```bash
docker run \
-d \
--restart unless-stopped \
--pull always \
--name exorde-cli3 \
exordelabs/exorde-cli \
-m 0xC4f072CE413D6f13EFEdb7473bA9E746F1E5407f \
-l 2
```

### Other Command
#### Check Logs
```bash
docker logs Exorde
```

#### Check logs constantly
```bash
docker logs -f exorde-cli3
```

#### Restart Docker
```bash
docker restart exorde-cli3
```

#### Stop Docker
```bash
docker stop exorde-cli3
```

### Delete Your Node
```bash
sudo  docker stop exorde-cli3 &&  sudo  docker  rm exorde-cli3
```

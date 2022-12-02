# DUSK TESTNET NODE MANUAL
The Dusk testnet will run for 6 weeks, 2 weeks (15-30 November) for the grace period (node ​​preparation etc) and 4 weeks (1 month from 1-31 December) for the actual testnet. Participants who successfully run the node for 1 month will get prizes of a total of 100K $DUSK

## Hardware Requirements
| Hardware | Specifications |
|---------|----------------|
|CPU|2 Cores|
|RAM|4 GB DDR4 RAM|
|Storage|50 GB HDD|

## Software Operating System Requirements
| Software Specifications |
|-------------------------|
|Recommendation Using ``Ubuntu 22.04 or higher``|

## Reference
[Official Doc](https://dusk.network/pages/incentivized-testnet)

[Explorer](https://explorer.dusk.network/charts/)

[Form Registration testnet](https://forms.gle/3h4wDbab9f6bZ68L8)

[Discord server](https://discord.gg/dusknetwork)

### Setup
```bash
sudo -i
```
### Open Port
```bash
ufw allow ssh
ufw allow 9000:9005/udp
ufw allow 8585
ufw enable
```
#### Update Dependencies
```bash
apt update && apt upgrade -y
```

#### Download libssl.so.1.1
```bash
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1l-1ubuntu1.6_amd64.deb
```
```bash
sudo dpkg -i libssl1.1_1.1.1l-1ubuntu1.6_amd64.deb
```

#### Download & Setup "rusk-wallet"
```bash
wget https://github.com/dusk-network/wallet-cli/releases/download/v0.13.0/ruskwallet0.13.0-linux-x64-libssl3.tar.gz
```

#### Extract File
```bash
tar -xvf ruskwallet0.13.0-linux-x64-libssl3.tar.gz
rm ruskwallet0.13.0-linux-x64-libssl3.tar.gz
cd ruskwallet0.13.0-linux-x64-libssl3.tar.gz
```

#### Create Wallet
```bash
./rusk-wallet --state http://127.0.0.1:8585
```

* Select `Create a new wallet`
* Enter password (free)
* Repeat the password
* Copy and save mnemonics
* After that, select the wallet that was created earlier
* Select ``Export provisioner key-pair``

#### Save key-pair
Make sure that the key-pair has been exported
```bash
cd $HOME
ls .dusk/rusk-wallet
```
* If the key-pair has been exported there will be files with `.key` and `.cpk` extensions
* The next step is to copy the `.key` and `.cpk` files to your Computer


#### Faucet registration and claim
 * After everything is set, fill in [this](https://forms.gle/3h4wDbab9f6bZ68L8) and upload the `.cpk` file earlier

#### Download and run `rusk-node`
```bash
curl --proto '=https' --tlsv1.2 -sSf https://dusk-infra.ams3.digitaloceanspaces.com/rusk/itn-installer.sh | sh
```

#### Move the `.key` file to the `/opt/dusk/conf` folder
```bash
cp .dusk/rusk-wallet/$(ls -a .dusk/rusk-wallet | grep .key) /opt/dusk/conf/consensus.keys
```

#### Set password `consensus.keys`
```bash
echo 'DUSK_CONSENSUS_KEYS_PASS=<INPUT_YOUR_PASSWORD>' > /opt/dusk/services/dusk.conf
```
 * For Example : echo 'DUSK_CONSENSUS_KEYS_PASS=ultramen123' > /opt/dusk/services/dusk.conf

#### Run Node
```bash
service rusk start
service dusk start
```

#### Stake Dusk
```bash
cd $HOME
cd rusk-wallet0.13.0-linux-x64-libssl3
./rusk-wallet --state http://127.0.0.1:8585
```

#### Then follow the step below

* Select `Access your wallet`
* Enter your password
* Choose your address
* Check if the balance has been sent admin
* If so, Select `Stake Dusk`
* Enter the amount of Dusk you want to stake (Minimum 1000 Dusk and 2 Dusk fee)
* Fill the gas limit with `2000000000`
* For gas prices can be left default
* Then type `y` to confirm the transaction
* Save tx hash (Just in case if needed)

* If you find writing like in this image, then wait until the block is fully synchronized
* ``status: Unimplemented, message: "", details: [], metadata: MetadataMap { headers: {"content-type": "application/grpc", "server": "envoy", "date": "Sat, 26 Nov 2022 15:50:13 GMT"} }``

![image](https://user-images.githubusercontent.com/116246591/204097355-be9d00e0-6e0d-4bc6-9fee-991e22173182.png)

## Other Command
#### Run Service
```bash
service rusk start
service dusk start
```

#### Stop Service
```bash
service rusk stop
service dusk stop
```

#### Check Logs Rusk
```bash
tail -f /var/log/rusk.log
```

#### Check Logs Dusk
```bash
tail -f /var/log/dusk.log
```

`Note: please read in detail and in detail so that no errors occur when running node`

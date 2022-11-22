# ALEO TESTNET NODE MANUAL

 * Discord : [Click Here](https://discord.gg/8z7HKu86D2)
 * Github Aleo : [Click Here](https://github.com/AleoHQ/snarkOS)
 * Doc Official Aleo : [Click Here](https://developer.aleo.org/testnet/getting_started/installation/)
 * Check Leader Board : [Click Here](https://www.aleo123.io/leaderBoard)

## Hardware Requirements

| Minimum | Specifications |
|---------|----------------|
|CPU|16 Cores|
|RAM|16 GB DDR4 RAM|
|Storage|128 GB HDD|
|Networking|10Mbit/s port|

| Recommended | Specifications |
|----------|-------------------|
|CPU|32 Cores|
|RAM|32 GB DDR4 RAM|
|Storage|2 x 1 TB NVMe SSD|
|Networking|1 Gbit/s port|

#### Update
```bash
apt update && apt upgrade -y
```
#### Install Tmux
```bash
apt install tmux -y
```
``after installation done, using command tmux new -s node``

#### Open Port
```bash
ufw allow ssh
ufw allow 4133/tcp
ufw allow 3033/tcp
ufw enable
```

#### Install Rustup
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
```bash
source "$HOME/.cargo/env"
```

#### Clone Repository
```bash
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
```

#### Build
```bash
cd snarkOS
./build_ubuntu.sh
```

#### Cargo Install Path
```bash
cargo install --path .
```

#### Create Account Aleo Prover
```bash
snarkos account new
```
``Save your Output Private Key, View Key, Address``

#### Run Prover
```bash
./run-prover.sh
```
 * Input Your Private Keys, paste
 * Using Command on your keyboard ``CTRL B D`` for exit
 
 #### Check Your Node
 ```bash
 tmux attach -t node
 ```
 
### Remove Node
```bash
rustup self uninstall
rm -rf prover.sh
rm -rf snarkOS
```

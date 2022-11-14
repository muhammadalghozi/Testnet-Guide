# ALEO TESTNET NODE MANUAL

 * Discord : https://discord.gg/8z7HKu86D2
 * Explorer : Soon
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

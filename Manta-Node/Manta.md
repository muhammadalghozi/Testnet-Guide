# MANTA NODE CONTRIBUTION

### Register Your Account
```bash
sudo -i
```
```bash
source ~/.profile
```
```bash
curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/Manta-Network/manta-rs/main/tools/install.sh | sh
```
```bash
manta-trusted-setup register
```
<p align="center">
  <img src="[https://user-images.githubusercontent.com/65535542/204483961-992f1e39-ae50-4c03-b528-ee32a2563640.jpg](https://user-images.githubusercontent.com/65535542/204484297-ba3881a3-7af9-40fe-89c4-ba44c0af7119.png
)">
</p>


![manta2](https://user-images.githubusercontent.com/65535542/204484297-ba3881a3-7af9-40fe-89c4-ba44c0af7119.png)

Save your Pharse and fill in the form on the link that is displayed.

* How to get Calamari's address
* Go to https://polkadot.js.org/apps/#/settings/metadata
* Replace the chain in the drop-down menu on the left, look for the Calamari chain and then switch
* Go to the settings menu and continue to update the metadata
* Go back to the polka dot wallet, click point 3 and then change the chain to Calamari Parachain
* Done, get the address of Calamary before 'dm'


#### Update Depedencies & Run Contributor
```bash
apt update && apt upgrade -y
```
```bash
sudo apt install pkg-config build-essential libssl-dev curl jq
```

#### Install Rust & Setting Path
```bash
curl https://sh.rustup.rs/ -sSf | sh -s -- -y
```
```bash
source $HOME/.cargo/env
```

#### Clone Repositori Manta-RS
```bash
git clone https://github.com/Manta-Network/manta-rs.git
```

#### Run Node & Using Tmux
```bash
tmux new -s manta
```
```bash
cd manta-rs
```
```bash
cargo run --release --all-features --bin groth16_phase2_client contribute
```
* Enter the Pharse at the time of registration
* Wait until it's finished running
* Done
``when finished then press CTRL + B D``

## Other Command Tools
##### Check Your Screen
```bash
tmux attach -t manta
```
##### Remove Your Node
```bash
rm -rf manta-rs
```

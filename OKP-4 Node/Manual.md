# OKP-4 TESTNET NODE

 * Explorer : https://okp4.explorers.guru/
 * Source : https://nodes.guru/okp4/setup-guide/en
 * Discord : https://discord.gg/2dQ9PTD9ZR

#### Open Port
```bash
ufw allow ssh
ufw allow 26657,26656
ufw enable
```
#### Check Port
``https://www.yougetsignal.com/tools/open-ports/``

#### Update Ubuntu
```bash
apt update && apt upgrade -y
```

#### Install Screen
```bash
apt install screen -y
```

#### Install Node
```bash
wget -q -O okp4.sh https://api.nodes.guru/okp4.sh && chmod +x okp4.sh && sudo /bin/bash okp4.sh
source $HOME/.bash_profile
```
#### Add Wallet
```bash
okp4d keys add wallet --recover
```
 * ``Enter Phrase 
keyring = password wallet``
 * ``you can change the name of the wallet you want, and you can import the pharse via keplr wallet``

``Waiting For sync block first if true please waiting after false``

#### Check Sync Block
```bash
curl -s localhost:26657/status | jq .result.sync_info.catching_up
```

#### Check Balance
```bash
okp4d q bank balances nodeaddress
```
 * ``you can change the name "nodeaddress" with the address that has been recovered previously``
 * ``For Example : okp4d q bank balances okp41u9eceyx2q2dupau0njz4am..``
 
#### Get Address Valoper
```bash
okp4d keys show wallet --bech val -a
```
``If You See Output, Please Save Output``

#### Create Validator ( after false status )
```bash
okp4d tx staking create-validator \
--amount=1000000uknow \
--pubkey=$(okp4d tendermint show-validator) \
--moniker="$OKP4_NODENAME" \
--chain-id=okp4-nemeton \
--commission-rate="0.01" \
--commission-max-rate="0.10" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1000000" \
--fees=1000uknow \
--from=wallet \
-y
```
 * ``For Example : okp4d tx staking create-validator \
--amount=1000000uknow \
--pubkey=$(okp4d tendermint show-validator) \
--moniker="POWERRENJES" \
--chain-id=okp4-nemeton \
--commission-rate="0.01" \
--commission-max-rate="0.10" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1000000" \
--fees=1000uknow \
--from=okp41u9eceyx2q2dupau0njz4am.. \
-y
``

#### For Faster Use This (OPTIONAL)
```bash
sudo systemctl stop okp4d

cp $HOME/.okp4d/data/priv_validator_state.json $HOME/.okp4d/priv_validator_state.json.backup
okp4d tendermint unsafe-reset-all --home $HOME/.okp4d --keep-addr-book

rm -rf $HOME/.okp4d/data 
rm -rf $HOME/.okp4d/wasm

SNAP_NAME=$(curl -s https://snapshots2-testnet.nodejumper.io/okp4-testnet/ | egrep -o ">okp4-nemeton.*\.tar.lz4" | tr -d ">")
curl https://snapshots2-testnet.nodejumper.io/okp4-testnet/${SNAP_NAME} | lz4 -dc - | tar -xf - -C $HOME/.okp4d

mv $HOME/.okp4d/priv_validator_state.json.backup $HOME/.okp4d/data/priv_validator_state.json

sudo systemctl restart okp4d
sudo journalctl -u okp4d -f --no-hostname -o cat
```
``If your status " false " Go to here for create validator``
#### Command to see list validator inactive :
```bash
okp4d query staking validators --limit 2000 -o json | jq -r '.validators[] | select(.status=="BOND_STATUS_UNBONDED") | [.operator_address, .status, (.tokens|tonumber / pow(10; 6)), .description.moniker] | @csv' | column -t -s"," | sort -k3 -n -r
```

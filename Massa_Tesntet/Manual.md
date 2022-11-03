# MASSA TESTNET EPISODE 16

 * Explorer Massa : https://test.massa.net/v1/#explorer
 * Discord Massa : https://discord.gg/massa
 * Telegram Global : https://t.me/massanetwork
 * Telegram Indonesia : https://t.me/massa_indonesia
 * Website : https://massa.net/

### Update Ubuntu
```bash
apt update && apt upgrade -y
```
### Install Screen
```bash
apt install screen -y
```
### Buat Sesi Screen Pertama
```bash
screen -S node
```
### Download File
```bash
wget https://github.com/massalabs/massa/releases/download/TEST.16.0/massa_TEST.16.0_release_linux.tar.gz
```
### Ekstrak File
```bash
tar -xvf massa_TEST.16.0_release_linux.tar.gz
```
### Buat Routable
```bash
sudo nano massa/massa-node/config/config.toml
```
Paste
```bash
[network]
routable_ip = "isidengan ipmu"
```
`Jika sudah Tekan CTRL + X terus Y`
Kemudian tekan `cd` balik ke direktori awal

### NEXT Jalankan `Massa-node`
```bash
cd massa/massa-node
./massa-node -p 1
```
Jika Sudah Jalan dan tidak terjadi Error 
`Tekan CTRL + d`

### Buat Sesi Kedua
```bash
screen -S client
```
### Jalankan `Massa-client`
```bash
cd massa/massa-client
./massa-client -p 1
```

 * Untuk pengguna baru silahkan generate wallet terlebih dahulu dengan command
`wallet_generate_secret_key`
 * Kemudian Cek Wallet Addres untuk mengambil faucet di discord
`wallet_info`

 * Untuk Pengguna Lama Silahkan langsung recover wallet lama dengan command
`wallet_add_secret_keys` masukkan secret keys yg telah disimpan
 * Kemudian Cek Wallet Addres untuk mengambil faucet di discord
`wallet_info`
Jika Sudah Mendapatkan Faucet Ikuti Langkah berikutnya
#### Add Staking Keys
```bash
node_add_staking_secret_keys
```
Contoh :`node_add_staking_secret_keys S1Lu1pMy215AHhdrr7mg5fBNinDC3iYtn`

#### Buy Rolls
```bash
buy_rolls ISIDENGAN WALLET ADDRES KALIAN 1 0
```
Contoh: `buy_rolls A16Uo1DPkTKWd3isuzHFK92z4MKYngY8yo3w7K 1 0`

#### Add Testner Reward Program
```bash
node_testnet_rewards_program_ownership_proof
```
Contoh : `node_testnet_rewards_program_ownership_proof A16Uo1DPkTKWd3isuzHFK92z4MKYngY8yo3w7K 444109910003941376` <id discord kemudian enter
 * Jika Sudah Tekan CTRL + d
                                                                                                                      
                                                                                                                      
                                                                                                                      
                                                                                                    


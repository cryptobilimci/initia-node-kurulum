# İnitia Node Kurulumu - Testnet

## ***8 hafta sürecek testnet aşamaları için node ve public testnetine katılarak katkı puanları elde edeceğiz.***

### VPS Sitem Gereksinimi
> 4 CPU - 16 GB - 400 SSD

### Kurulum

**Ekran Oturumu Oluştur (Opsiyonel ama Tavsiye Edilir)
Komutun bir süre çalışacağı için bir screen oturumu oluşturmanızı şiddetle tavsiye ederim.**

`apt install screen`
`screen -S initia`


#### Aynı oturuma bağlanmak için aşağıdaki komutu çalıştırmalısınız

`screen -r -d initia`


### Sistem Güncellenmesi

`sudo apt update && sudo apt upgrade -y
sudo apt install curl git wget htop tmux build-essential jq make lz4 gcc unzip -y`


### Script Kurulum

`curl -OJL https://raw.githubusercontent.com/bdehri/initia-guide/main/initia_installer.sh
chmod +x initia_installer.sh
./initia_installer.sh <moniker>`

### Cüzdan Oluşturma ve Faucet

**<> olan kısıma cüzdan isminizi yazın**

`source .bashrc
initiad keys add <anahtar-adı>`

**Bu komuttan sonra size cüzdan seed'i verecek onu kaydedin.**

Tokenları [faucet](https://faucet.testnet.initia.xyz/) adresinden alabilirsiniz.

### Validator Kurulumu

`initiad tx mstaking create-validator \
    --amount="1000000uinit" \
    --pubkey=$(initiad tendermint show-validator) \
    --moniker="<moniker>" \
    --chain-id="initiation-1" \
    --from="<anahtar_adı>" \
    --commission-rate="0.10" \
    --commission-max-rate="0.20" \
    --commission-max-change-rate="0.01" \
    --fees 30000uinit`

***Moniker adınızı belirleyin. Örneğin : cryptobilimci**
**From= anahtar adınızıza bir önceki cüzdan kurulumda verdiğiniz adı yazın**

**Validator kurulumdan sonra TXID verecek onu [blok tarayıcısından](https://scan.testnet.initia.xyz/initiation-1) aratıp validatorunuzu bulabilirsiniz.

**Son olarak validator [formunu](https://docs.google.com/forms/d/e/1FAIpQLSc09Kl6mXyZHOL12n_6IUA8MCcL6OqzTqsoZn9N8gpptoeU_Q) doldurup oracle görevine geçebilirsiniz.

**Validator kurulumu sırasında blokların eşleşmesi gerekiyor bunun için bir süre bekleyebilirsiniz.**


<h1 align="center"> Tanssi dance baby

![image](https://github.com/molla202/Tanssi/assets/91562185/209da5fb-efe6-4170-a7ba-90511307e0f7)



> Uygulama dağıtım süresini aylardan bir saatin altına dönüştürerek Tanssi, blockchain alanında büyük bir değişime yol açarak benzersiz verimlilik ve ölçeklenebilirliğin kilidini açıyor.

 [Topluluk kanalımız](https://t.me/corenodechat)<br>
 [Topluluk Twitter](https://twitter.com/corenodeHQ)<br>
 [Tanssi Website](https://www.tanssi.network/)<br>
 [Discord](https://discord.gg/WMxTM2fQkr)<br>
 [Twitter](https://twitter.com/TanssiNetwork)<br>
 [Doc](https://docs.tanssi.network/node-operators/validators/onboarding/register-in-symbiotic/#__tabbed_7_2)<br>
 [Explorer](https://polkadot.js.org/apps/?rpc=wss://dancelight.tanssi-api.network#/extrinsics)<br>
 [Telemetry](https://telemetry.polkadot.io/#/0x983a1a72503d6cc3636776747ec627172b51272bf45e50a355348facb67a820a)<br>

</h1>

## 💻 Sistem Gereksinimleri
| Bileşenler | Minimum Gereksinimler | 
| ------------ | ------------ |
| CPU |	2+|
| RAM	| 4+ GB |
| Storage	| 160+ GB SSD |

### form var en son
https://www.tanssi.network/node-operators-application


```
wget https://github.com/moondance-labs/tanssi/releases/download/v0.12.0/tanssi-relay && \
wget https://github.com/moondance-labs/tanssi/releases/download/v0.12.0/tanssi-relay-execute-worker && \
wget https://github.com/moondance-labs/tanssi/releases/download/v0.12.0/tanssi-relay-prepare-worker && \
chmod +x ./tanssi-relay*

sudo mkdir /root/tanssi-data/

cd /root/tanssi-data/

mv /root/tanssi-relay* /root/tanssi-data
```
```
sudo ln -s $HOME/tanssi-data/tanssi-relay /usr/local/bin/tanssi-relay -f
```
```
tanssi-relay key generate-node-key --file $HOME/tanssi-data/node-key
```
NOT: molla202 yazan yerleri kendi adınızla değiştirin
```
sudo tee /etc/systemd/system/tanssid.service > /dev/null <<'EOF'
[Unit]
Description="Tanssi systemd service"
After=network.target
StartLimitIntervalSec=0

[Service]
Type=simple
Restart=on-failure
RestartSec=10
User=root
SyslogIdentifier=tanssi
SyslogFacility=local7
KillSignal=SIGHUP
ExecStart=$HOME/tanssi-data/tanssi-relay --chain=dancelight \
  --base-path=$HOME/tanssi-data/ \
  --node-key-file $HOME/tanssi-data/node-key \
  --database=paritydb \
  --rpc-port=9944 \
  --prometheus-port=9615 \
  --prometheus-external \
  --name=molla202 \
  --listen-addr=/ip4/0.0.0.0/tcp/30333 \
  --public-addr=/ip4/$(wget -qO- eth0.me)/tcp/30333 \
  --state-pruning=archive \
  --blocks-pruning=archive \
  --rpc-cors=all \
  --rpc-methods=safe \
  --unsafe-rpc-external \
  --rpc-max-connections=100 \
  --telemetry-url='wss://telemetry.polkadot.io/submit/ 0' \
  --validator

[Install]
WantedBy=multi-user.target
EOF
```
```
sudo systemctl daemon-reload
sudo systemctl enable tanssid.service
sudo systemctl restart tanssid.service
```
```
journalctl -u tanssid -fo cat
```


## Key olusturalım.
```
curl http://127.0.0.1:9944 -H \
"Content-Type:application/json;charset=utf-8" -d \
  '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"author_rotateKeys",
    "params": []
  }'
```
## KEyi kaydedelim
note : bu kısım en son Symbiotic register yapacağız sonra opt in yapaağız ondan sonra en son sezon key alıp işlemleri yapıyoruz.
* Linke gidelim.

https://polkadot.js.org/apps/?rpc=wss://dancelight.tanssi-api.network#/extrinsics

![image](https://github.com/user-attachments/assets/0f0b8f02-751d-4c1f-8101-91cca4ea4646)

![image](https://github.com/user-attachments/assets/ee5cab7d-10bf-444a-a33f-931e6239523e)











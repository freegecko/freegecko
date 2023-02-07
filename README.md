#測試機器 ubuntu22.04, 2023/02/06
## 使用机场: https://freegecko.com
## 下載
wget https://github.com/Dreamacro/clash/releases/download/v1.13.0/clash-linux-amd64-v3-v1.13.0.gz

gunzip clash-linux-amd64-v3-v1.13.0.gz
chmod +x clash-linux-amd64-v3-v1.13.0
sudo cp clash-linux-amd64-v3-v1.13.0 /usr/local/bin/clash

./clash-linux-amd64-v3-v1.13.0
## 此時會下載一些資料, 預設在 ~/.config/clash/

cd ~/.config/clash/
wget -O config.yaml https://freegecko.com/api/v1/client/subscribe\?token\=xxxxxxxx\&flag\=clash
## 此處換成你的訂閱地址



## systemd file
# vim /etc/systemd/system/clash.service
[Unit]
Description=Clash daemon, A rule-based proxy in Go.
After=network.target

[Service]
Type=simple
Restart=always
#ExecStart=/usr/local/bin/clash 
ExecStart=/usr/local/bin/clash -d /home/ives/.config/clash

[Install]
WantedBy=multi-user.target
#測 

systemctl start clash

# 然後用  https://clash.razord.top/#/proxies  
# 這網站輸入 127.0.0.1 9090 去檢驗自己剛才導入的節點

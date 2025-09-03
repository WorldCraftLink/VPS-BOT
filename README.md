# Install
```sh
git clone https://github.com/WorldCraftLink/VPS-BOT
pip install -r requirements.txt
sudo nano /etc/systemd/system/worldcraftlink-bot.service
```
# Unit
```sh
Description=WorldCraftLink VPS Bot
After=network.target docker.service
Requires=docker.service

# Service
Type=simple
User=root
WorkingDirectory=/root
ExecStart=/usr/bin/python3 /root/bot.py
Restart=always
RestartSec=30
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
Environment="DOCKER_HOST=unix:///var/run/docker.sock"

# Install
WantedBy=multi-user.target
```

```sh
sudo useradd -r -s /bin/false worldcraftlink
sudo usermod -aG docker worldcraftlink
```
# Reload systemd
```sh
sudo systemctl daemon-reload
```
# Enable service to start on boot
```sh
sudo systemctl enable worldcraftlink-bot.service
```
# Start the service now
```sh
sudo systemctl start worldcraftlink-bot.service
```
# Check status
```sh
sudo systemctl status worldcraftlink-bot.service
```
# View logs
```sh
sudo journalctl -u worldcraftlink-bot.service -f

```


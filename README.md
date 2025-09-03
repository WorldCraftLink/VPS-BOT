# Install
```sh
pip install -r requirements.txt
'sudo nano /etc/systemd/system/unixnodes-bot.service
```
[Unit]
Description=UnixNodes VPS Bot
After=network.target docker.service
Requires=docker.service

# Service
```sh
Type=simple
User=root
WorkingDirectory=/root
ExecStart=/usr/bin/python3 /root/bot.py
Restart=always
RestartSec=30
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
Environment="DOCKER_HOST=unix:///var/run/docker.sock"
```

# Install
```sh
WantedBy=multi-user.target
```
```sh
sudo useradd -r -s /bin/false unixnodes
sudo usermod -aG docker unixnodes
```
# Reload systemd
```sh
sudo systemctl daemon-reload
```
# Enable service to start on boot
```sh
sudo systemctl enable unixnodes-bot.service
```
# Start the service now
```sh
sudo systemctl start unixnodes-bot.service
```
# Check status
```sh
sudo systemctl status unixnodes-bot.service
```
# View logs
```sh
sudo journalctl -u unixnodes-bot.service -f
```


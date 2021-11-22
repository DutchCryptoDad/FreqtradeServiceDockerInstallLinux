To run the Docker container as a service, do the following:

Create a file in the directory ``/etc/systemd/system`` with the name ``freqtrade_docker.service``.

```
sudo nano /etc/systemd/system/freqtrade_docker.service
```

Open the file and put the following in the file:

```
[Unit]
Description=Freqtrade Docker container
Requires=docker.service
After=docker.service
Type=notify
NotifyAccess=all
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=freqtrade_docker
User=dcd
Group=dcd

[Service]
Type=oneshot
RemainAfterExit=yes
Restart=always
WorkingDirectory=/home/dcd/ft_userdata/docker-compose.yml
ExecStart=/usr/local/bin/docker-compose up -d
ExecStop=/usr/local/bin/docker-compose down
TimeoutStartSec=0

[Install]
WantedBy=multi-user.target
```


After each service config change:

```
sudo systemctl daemon-reload
```

To start the service at system boot, enter:

```
systemctl enable freqtrade_docker.service
```

Start the service:

```
sudo systemctl start freqtrade_docker.service
```

Check the service status:

```
sudo systemctl status freqtrade_docker.service
```

Stop the service:

```
sudo systemctl stop freqtrade_docker.service
```

Disable the service at system startup (no start at boot):

```
sudo systemctl disable freqtrade_docker.service
```

Show activity:

```
sudo tail -f /var/log/syslog
```



[Unit]
Description=Freqtrade bot
[Service]
WorkingDirectory=/home/dcd/freqtrade
ExecStart=/home/dcd/freqtrade/.env/bin/freqtrade trade --config /home/dcd/freqtrade/config.json
Restart=always
RestartSec=10
Type=notify
NotifyAccess=all
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=freqtrade
User=root
Group=root
Environment=NODE_ENV=production
[Install]
WantedBy=multi-user.target

To run the Docker container as a service, do the following:

Create a file in the directory ``/etc/systemd/system`` with the name ``freqtrade_docker.service``.

```
sudo nano /etc/systemd/system/freqtrade_docker.service
```

Open the file and put the following in the file:

```
[Unit]
Description=%i service with docker compose
Requires=docker.service
After=docker.service

[Service]
Type=oneshot
RemainAfterExit=true
WorkingDirectory=/home/dcd/ft_userdata/%i
ExecStart=/usr/local/bin/docker-compose up -d --remove-orphans
ExecStop=/usr/local/bin/docker-compose down

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

Start the service manually:

```
sudo systemctl start freqtrade_docker.service
```

Check the service status:

```
sudo systemctl status freqtrade_docker.service
```

And to check if the docker container is working:

```
docker ps

docker container logs <container id>
```

Stop the service:

```
sudo systemctl stop freqtrade_docker.service
```

Disable the service at system startup (no start at boot):

```
sudo systemctl disable freqtrade_docker.service
```

Show freqtrade activity:

```
tail -f user_data/logs/freqtrade.log
```



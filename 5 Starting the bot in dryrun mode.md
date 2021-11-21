## Edit the docker-compose file

To start the bot in dry run mode with Docker, first we have to edit the compose.yml file in the ft_userdata directory

```
cd ..
nano docker-compose.yml
```

You can specify the configuration, strategy and all other freqtrade command line parameters under the "command" section:

```
command: >
      trade
      --logfile /freqtrade/user_data/logs/freqtrade.log
      --db-url sqlite:////freqtrade/user_data/tradesv3.sqlite
      --config /freqtrade/user_data/config.json
      --strategy SampleStrategy
```

In our case it is practically the same as the command entered on the command line in the previous section.

## Starting the Docker container

To start dry run trading with the freqtrade bot, just use the command:

```
docker-compose up -d
```

This reads the compose file with the commands and other parameters and runs the container as a daemon.

## Checking the log file

To see if Freqtrade is working, use the next commands:

The Docker processes running:

```
docker ps
```

The Docker container logs:

```
docker container logs 97ec7
```

The Freqtrade log:

```
tail -f user_data/logs/freqtrade.log
```

## Stopping the container

To stop the container with the running freqtrade bot, use the following commands:

Determine the Docker process number or container name of Freqtrade:

```
docker ps

CONTAINER ID   IMAGE                           COMMAND                  CREATED          STATUS          PORTS                      NAMES
97ec7f2352e7   freqtradeorg/freqtrade:stable   "freqtrade trade --l…"   20 minutes ago   Up 20 minutes   127.0.0.1:8080->8080/tcp   freqtrade
```


Once figured out, use it in the command to stop the bot. You do not have to specify the complete container ID, the first 4 or 5 characters will do as well:

```
docker container stop 97ec7
```

Check if the instance is stopped:

```
docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```



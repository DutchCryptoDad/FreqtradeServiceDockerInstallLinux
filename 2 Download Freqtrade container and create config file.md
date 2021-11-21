This file contains instructions on how to install a Freqtrade Docker container on Linux Mint 20.2

## Create Freqtrade user data drectory

This directory will contain all files that are manually made and regularly changed, like config files, strategy files, databases and candle data.

These instructions come straight from the Freqtrade website: https://www.freqtrade.io/en/stable/docker_quickstart/#docker-quick-start


```
# Create the directory
mkdir ft_userdata
cd ft_userdata/
```

## Downloading the Docker compose file

```
# Download the docker-compose file from the repository
curl https://raw.githubusercontent.com/freqtrade/freqtrade/stable/docker-compose.yml -o docker-compose.yml
```

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration. See: https://docs.docker.com/compose/

```
# Pull the freqtrade image
sudo docker-compose pull
```

## Creating a user directory for freqtrade

```
# Create user directory structure with the necessary freqtrade directories and files
sudo docker-compose run --rm freqtrade create-userdir --userdir user_data
```

## Make the config.json file


```
# Create configuration - Requires answering interactive questions
sudo docker-compose run --rm freqtrade new-config --config user_data/config.json
```

## More

See the Freqtrade website for more information:



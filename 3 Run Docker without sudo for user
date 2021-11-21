Up until now I had to use the sudo command to compose the Docker container for freqtrade.

You can configure your 'normal' user account to run Docker without the sudo command.

WARNING: BY USING THIS PROCEDURE YOU CAN CREATE SECURITY HOLES ON YOUR ENVIRONMENT!!!! 
IF YOU ARE IN DOUBT, JUST KEEP USING SUDO TO ACTIVATE THE CONTAINER.
USE THE PROCEDURE BELOW AT YOUR OWN RISK!

Create a docker group and add the current user (that should run Docker)

```
sudo groupadd docker
sudo usermod -aG docker $USER
```

Log out and back in with that user to reactivate group membership

```
newgrp docker
```

Now verify that you can run Docker without sudo

```
docker ps
```

Check if you can make a new config file without sudo


```
cd ft_userdata/
docker-compose run --rm freqtrade new-config --config user_data/config.json
```

That's it.

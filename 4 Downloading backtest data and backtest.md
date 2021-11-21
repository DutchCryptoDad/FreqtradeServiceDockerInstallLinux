## Take ownership of the user_data directory

Before we even continue further, lets not forget that the original installation of the Docker container was done with the root user (sudo)
Therefore we first have to take ownership of the freqtrade user_data directory.

```
sudo chown -R dcd.dcd user_data
```

## Edit the config.json file

To be able to downloading backtest data, first edit the config.json file to add a trading pair.
Also change Pairlist from VolumePairList to StaticPairList otherwise backtesting will give an error.

```
cd user_data/
nano config.json
```

These sections: 

```
       "pair_whitelist": [
        "BTC/USDT"
```

```
    "pairlists": [
        {
            "method": "StaticPairList",
```

If you want, you can use a higher hartbeat interval while testing stuff out:

```
    "heartbeat_interval": 5,
```

3. Use the following command to download backtest data

```
docker-compose run --rm freqtrade download-data --config user_data/config.json  --days 30 -t 5m
```

The --rm switch will remove the container after completion otherwise you'll end up with many closed containers.

4. Use the following command to backtest a strategy

```
docker-compose run --rm freqtrade backtesting --config user_data/config.json --strategy SampleStrategy 
```


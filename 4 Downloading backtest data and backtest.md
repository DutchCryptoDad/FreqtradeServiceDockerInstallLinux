## 1 Take ownership of the user_data directory

Before we even continue further, lets not forget that the original installation of the Docker container was done with the root user (sudo)
Therefore we first have to take ownership of the freqtrade user_data directory.

```
sudo chown -R dcd.dcd user_data
```

## 2 Edit the config.json file

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


Use the following command to 

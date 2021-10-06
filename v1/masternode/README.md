This is for running the master-node™. ***Keys are hard coded to keep things simple, please do not use these keys and/or anything form here.***

Init the execution layer Geth,

```
$ /home/ubuntu/go/bin/geth --datadir=/datadrive/hacknet/v1 init genesis.json
```

override it's node key to have a stable identity,

```
$ echo 1040e96855a25a723dbee32a6b5f6eb44a401640a5018876360275c6b30d79d5 > /datadrive/hacknet/v1/geth/nodekey
```

start it up and let it ethash mine until the terminal difficulty,

```
$ /home/ubuntu/go/bin/geth --datadir=/datadrive/hacknet/v1 --ethash.dagdir=/datadrive/hacknet/v1/ethash --catalyst --mine --miner.threads=1 --miner.etherbase=0x0000000000000000000000000000000000000001
```

then stop it and restart it without mining (dafuq, yay hack code) and with APIs exposed for the consensus client:

```
$ /home/ubuntu/go/bin/geth --datadir=/datadrive/hacknet/v1 --catalyst --http --http.api "engine,eth"
```

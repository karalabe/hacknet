This is for running the master-node™. ***Keys are hard coded to keep things simple, please do not use these keys and/or anything form here.***

Init the execution layer Geth,

```
$ /home/ubuntu/go/bin/geth --datadir=/datadrive/hacknet/v2 init genesis.json
```

override it's node key to have a stable identity,

```
$ echo 634e6439fdaee1d633092934b08d842fa141f0d5aa31d1dd91cf5e50b932c824 > /datadrive/hacknet/v2/geth/nodekey
```

start it up and let it ethash mine until the terminal difficulty,

```
$ /home/ubuntu/go/bin/geth --datadir=/datadrive/hacknet/v2 --ethash.dagdir=/datadrive/hacknet/v2/ethash --catalyst --mine --miner.threads=1 --miner.etherbase=0xfb969eb20eca70c2800103bbb0d3757bc60f918a
```

then stop it and restart it without mining (dafuq, yay hack code) and with APIs exposed for the consensus client:

```
$ nohup /home/ubuntu/go/bin/geth --datadir=/datadrive/hacknet/v2 --networkid=1337002 --catalyst --http --http.api "engine,eth" --maxpeers=250 --light.serve=100 --light.maxpeers=50 > /home/ubuntu/geth &
```

Init the consensus layer Lighthouse,

```
$ lcli --spec minimal new-testnet \
	--genesis-time $(echo "$(date +%s) - $(echo "$(date +%s) % 3600" | bc)" | bc) \
	--altair-fork-epoch 1 --merge-fork-epoch 2 \
	--interop-genesis-state \
	--validator-count 8 --min-genesis-active-validator-count 8 \
	--testnet-dir ./beaconspec \
	--deposit-contract-address 0x0000000000000000000000000000000000000000 \
	--deposit-contract-deploy-block 0 \
	--eth1-block-hash 0xf7e06ffae1e05087298f15ff6673e6280fad4162ba3bc7cd6c013016f435c8bd
```

init the validator keys for Lighthouse,

```
$ lcli insecure-validators --spec minimal \
	--base-dir ./keystore \
	--count 8 --node-count 1
```

start the Lighthouse consensus node,

```
$ nohup /home/ubuntu/.cargo/bin/lighthouse --spec minimal \
	--testnet-dir ./beaconspec \
	--debug-level info \
	beacon_node \
	--datadir ./beacondir \
	--dummy-eth1 \
	--http \
	--boot-nodes="enr:-Iq4QKuNB_wHmWon7hv5HntHiSsyE1a6cUTK1aT7xDSU_hNTLW3R4mowUboCsqYoh1kN9v3ZoSu_WuvW9Aw0tQ0Dxv6GAXxQ7Nv5gmlkgnY0gmlwhLKAlv6Jc2VjcDI1NmsxoQK6S-Cii_KmfFdUJL2TANL3ksaKUnNXvTCv1tLwXs0QgIN1ZHCCIyk" \
	--http-allow-sync-stalled \
	--metrics \
	--merge \
	--execution-endpoints http://localhost:8545 \
	--terminal-total-difficulty-override 10 > /home/ubuntu/beacon &
```

and start the Lighthouse validator node:

```
$ nohup /home/ubuntu/.cargo/bin/lighthouse --debug-level info --datadir ./keystore/node_1 \
	vc \
	--testnet-dir ./beaconspec \
	--init-slashing-protection \
	--beacon-nodes http://localhost:5052 > /home/ubuntu/validtor &
```

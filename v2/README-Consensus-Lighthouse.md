This guide deploys a Lighthouse consensus client and connects it to the hacknet. You'll need an execution client below.

Clone and build Lighthouse's merge interop PR:

```
$ git clone git@github.com:sigp/lighthouse.git
$ cd lighthouse
$ make

# Ensure `~/.cargo/bin/lighthouse` is available in you $PATH
```

Run the consensus Lighthouse and connect it to the masternode Lighthouse

```
$ lighthouse \
	--spec minimal \
	--testnet-dir ./beaconspec \
	--debug-level info \
	beacon_node \
	--datadir ./hacknet.v2.lighthouse \
	--dummy-eth1 \
	--http \
	--http-allow-sync-stalled \
	--metrics \
	--merge \
	--execution-endpoints http://127.0.0.1:8545 \
	--terminal-total-difficulty-override 10 \
	--libp2p-addresses /ip4/35.178.114.73/tcp/9000
```

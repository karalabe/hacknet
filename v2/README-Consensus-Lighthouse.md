This guide deploys a Lighthouse consensus client and connects it to the hacknet. You'll need an execution client below.

Clone and build Lighthouse's merge interop PR:

```
$ git clone git@github.com:sigp/lighthouse.git
$ cd lighthouse
$ git checkout merge-f2f
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
        --libp2p-addresses /ip4/35.178.114.73/tcp/9000/p2p/16Uiu2HAkz6oRBK6aKRA2uv9vxJEPhc2Rmznd5D1DqE4DoCYNqnf3 \
        --boot-nodes="enr:-Iq4QKuNB_wHmWon7hv5HntHiSsyE1a6cUTK1aT7xDSU_hNTLW3R4mowUboCsqYoh1kN9v3ZoSu_WuvW9Aw0tQ0Dxv6GAXxQ7Nv5gmlkgnY0gmlwhLKAlv6Jc2VjcDI1NmsxoQK6S-Cii_KmfFdUJL2TANL3ksaKUnNXvTCv1tLwXs0QgIN1ZHCCIyk"
```

This guide deploys a Geth execution client and connects it to the hacknet. You'll need a consensus client above.

Clone and build Geth's merge interop PR:

```
$ git clone git@github.com:MariusVanDerWijden/go-ethereum.git
$ cd go-ethereum
$ git checkout merge-interop-spec
$ make

# Ensure `build/bin/geth` is available in you $PATH
```

Initialize the hacknet chain for the execution layer

```
$ geth --datadir=./hacknet.v1.geth init genesis.json
```

Run the execution Geth and connect it to the masternode Geth

```
$ geth --datadir=./hacknet.v1.geth --catalyst --http -http.api "engine,eth" --allow-insecure-unlock --bootnodes enode://ead4b0e2afd49a70ca57a017a59611675ca4464c9d551396711020cea09d6ce974072c7ec0766cc38f4817a33fafcc7f8cbd070feb1ea84e798ee92dfee24675@35.178.114.73:30303 console
```

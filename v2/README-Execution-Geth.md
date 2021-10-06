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
$ geth --datadir=./hacknet.v2.geth init genesis.json
```

Run the execution Geth and connect it to the masternode Geth

```
$ geth --datadir=./hacknet.v2.geth --networkid=1337002 --catalyst --http -http.api "engine,eth" --allow-insecure-unlock --bootnodes enode://e95870e55cf62fd3d7091d7e0254d10ead007a1ac64ea071296a603d94694b8d92b49f9a3d3851d9aa95ee1452de8b854e0d5e095ef58cc25e7291e7588f4dfc@35.178.114.73:30303 console
```

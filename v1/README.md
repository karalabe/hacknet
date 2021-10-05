# Hacknet v1

This is an Ethereum *merge interop* testnet to check if various consensus/execution client combos can interop with each other and sync to a common chain.

In this specific version validation is done by the master-node, which is a Lighthouse consensus client backed by a Geth execution client. You should be able to connect to it via your favorite client combo and check that you can both connect to it, sync it and transact on it.

Specs:

- Execution layer genesis specs (Geth style): [`genesis.json`](./genesis.json)
- Execution layer bootnode: `enode://ead4b0e2afd49a70ca57a017a59611675ca4464c9d551396711020cea09d6ce974072c7ec0766cc38f4817a33fafcc7f8cbd070feb1ea84e798ee92dfee24675@35.178.114.73:30303`
- Consensus layer genesis spec (Lighthouse style): [beaconspec](./beaconspec)
- Consensus layer bootnode: `/ip4/35.178.114.73/tcp/9000/p2p/16Uiu2HAkz6oRBK6aKRA2uv9vxJEPhc2Rmznd5D1DqE4DoCYNqnf3`
- Consensus layer bootnode ENR: `enr:-K24QLK6c3kEq68gLIOutNuZsHKBIvR48JaAoQVrVbHK7bBJRqRX72f2feV4vEOiROQYyDNJC9z1gXeH8JsQ0U9IbTsch2F0dG5ldHOIAAAAAAAAAACEZXRoMpC_4NP0AgAAAf__________gmlkgnY0iXNlY3AyNTZrMaECRXTPHtP7GldWzvT2G_minRQbPWeGeaOW04upqcGUxeKIc3luY25ldHMAg3RjcIIjKA`

Howtos:

- Configure a [Geth execution client](./README-Execution-Geth.md)
- Configure a [Lighthouse consensus client](./README-Consensus-Lighthouse.md)

# Hacknet v2

This is an Ethereum *merge interop* testnet to check if various consensus/execution client combos can interop with each other and sync to a common chain.

In this specific version validation is done by the master-node, which is a Lighthouse consensus client backed by a Geth execution client. You should be able to connect to it via your favorite client combo and check that you can both connect to it, sync it and transact on it.

Execution layer specs:

- Genesis specs (Geth style): [`genesis.json`](./genesis.json)
- Genesis hash: `0xf7e06ffae1e05087298f15ff6673e6280fad4162ba3bc7cd6c013016f435c8bd`
- Bootnode devp2p endpoint: `enode://e95870e55cf62fd3d7091d7e0254d10ead007a1ac64ea071296a603d94694b8d92b49f9a3d3851d9aa95ee1452de8b854e0d5e095ef58cc25e7291e7588f4dfc@35.178.114.73:30303`
- Network ID: `1337002`

Consensus layer specs:

- Genesis spec (Lighthouse style): [beaconspec](./beaconspec)
- Bootnode libp2p endpoint: `/ip4/35.178.114.73/tcp/9000/p2p/16Uiu2HAmLzmg7WXGtXwZrfLZAbBn8rdY3MWWfvoN4FfeYR4vrQpV`
- Bootnode ENR: `enr:-K24QJ7fj53ZVzBvfJvVMyFeW3yzn9cb30LqdkdbhZShHn71ApVXv_auGba8uhVICD2bTQvQoiB3SkmAfTz-8NMMHY0Bh2F0dG5ldHOIAAAAAAAAAACEZXRoMpC_4NP0AgAAAf__________gmlkgnY0iXNlY3AyNTZrMaEDe-7HhtJ_OuFY2feuHsXuMsPVoHzn7tU9QHqFRIzo7FaIc3luY25ldHMAg3RjcIIjKA`

Howtos:

- Configure a [Geth execution client](./README-Execution-Geth.md)
- Configure a [Lighthouse consensus client](./README-Consensus-Lighthouse.md)

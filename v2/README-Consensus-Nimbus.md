This guide deploys a Nimbus consensus client and connects it to the hacknet. You'll need an execution client.

Clone and build Nimbus's merge interop PR:

```
$ git clone https://github.com/status-im/nimbus-eth2.git
$ cd nimbus-eth2
$ git checkout amphora-merge-interop
$ make update -j4
$ make NIMFLAGS="-d:const_preset=minimal" LOG_LEVEL=DEBUG nimbus_beacon_node -j4
```

Run the consensus Nimbus and connect it to consensus and execution:

```
$ build/nimbus_beacon_node \
  --data-dir=hacknet.v2.nimbus \
  --network=../hacknet/v2/beaconspec \
  --log-level=DEBUG \
  -b:enr:-Ly4QEflyLLzPZujoYotdzLYZqzO39EES1bAxFqmL5C_zN3JGZ82_1k4hlUUQFDvW_LPibgdoSTxKo8lTzD9_FJ9sTwrh2F0dG5ldHOIAAAAAAAAAACEZXRoMpC_4NP0AgAAAf__________gmlkgnY0gmlwhCOyckmJc2VjcDI1NmsxoQN77seG0n864VjZ964exe4yw9WgfOfu1T1AeoVEjOjsVohzeW5jbmV0cwCDdGNwgiMog3VkcIIjKA \
  --web3-url=ws://127.0.0.1:8546/
```

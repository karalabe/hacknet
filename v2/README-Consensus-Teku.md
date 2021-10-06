This guide deploys a Teku consensus client and connects it to the hacknet. You'll need an execution client.

Clone and build Teku's merge interop PR:

```bash
git clone -b merge-interop https://github.com/ConsenSys/teku.git
cd teku
./gradlew installDist

```

Run the consensus Teku and connect it to consensus and execution:

```bash
./build/install/teku/bin/teku \
  --network "https://github.com/karalabe/hacknet/raw/main/v2/beaconspec/config.yaml" \
  --eth1-endpoints "http://127.0.0.1:8545" \
  --rest-api-enabled \
  --p2p-discovery-bootnodes "enr:-Iq4QKuNB_wHmWon7hv5HntHiSsyE1a6cUTK1aT7xDSU_hNTLW3R4mowUboCsqYoh1kN9v3ZoSu_WuvW9Aw0tQ0Dxv6GAXxQ7Nv5gmlkgnY0gmlwhLKAlv6Jc2VjcDI1NmsxoQK6S-Cii_KmfFdUJL2TANL3ksaKUnNXvTCv1tLwXs0QgIN1ZHCCIyk" \
      "enr:-Ly4QEflyLLzPZujoYotdzLYZqzO39EES1bAxFqmL5C_zN3JGZ82_1k4hlUUQFDvW_LPibgdoSTxKo8lTzD9_FJ9sTwrh2F0dG5ldHOIAAAAAAAAAACEZXRoMpC_4NP0AgAAAf__________gmlkgnY0gmlwhCOyckmJc2VjcDI1NmsxoQN77seG0n864VjZ964exe4yw9WgfOfu1T1AeoVEjOjsVohzeW5jbmV0cwCDdGNwgiMog3VkcIIjKA" \
  --p2p-static-peers "/ip4/35.178.114.73/tcp/9000/p2p/16Uiu2HAmLzmg7WXGtXwZrfLZAbBn8rdY3MWWfvoN4FfeYR4vrQpV" \
  --initial-state "https://github.com/karalabe/hacknet/raw/main/v2/beaconspec/genesis.ssz" \
  --Xnetwork-merge-total-terminal-difficulty 16 \
  --Xp2p-multipeer-sync-enabled false
```

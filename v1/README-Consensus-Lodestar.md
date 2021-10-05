This guide deploys a Lodestar consensus client and connects it to the hacknet. You'll need an execution client below.

```
# Clone
git clone -b merge-interop --depth 1 http://github.com/chainsafe/lodestar
cd lodestar

# Build
yarn && yarn build

# Download the genesis state
curl "https://raw.githubusercontent.com/ChainSafe/hacknet/main/v1/beaconspec/genesis.ssz" -o amphora/v1/genesis.ssz

# Make sure execution client is running on localhost:8545

# Finally, run lodestar
amphora/v1/run.sh
```

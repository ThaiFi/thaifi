# ThaiChain

ThaiFi is a blockchain service that allows developers to build their own DeFi  using smart contract. ThaiFi also compatible with the Ethereum Virtual Machine (EVM), which means it’s capable of running dapps ported over from Ethereum.

## Steps to Run a ThaiFi Fullnode
```bash
$ https://github.com/ThaiFi/thaifi.git
# Enter the folder thaifi was cloned into
cd thaifi
# Write genesis state locally
$ docker run -it --rm  -v $PWD:/tfi -w /tfi ethereum/client-go --datadir /tfi/node init genesis.json
# Start your fullnode
$ docker run -it --rm -p 30333:30333 --name tfi-node -v $PWD:/tfi -w /tfi ethereum/client-go --datadir /tfi/node --nousb --config ./config.toml  -cache 4096 --port 30333

```

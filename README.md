# ThaiChain

ThaiFi is a blockchain service that allows developers to build their own DeFi  using smart contract. ThaiFi also compatible with the Ethereum Virtual Machine (EVM), which means it’s capable of running dapps ported over from Ethereum.

## How to Run A Fullnode on ThaiFi
### Fullnodes Functions
- Stores the full blockchain history on disk and can answer the data request from the network.
- Receives and validates the new blocks and transactions.
- Verifies the states of every accounts.

## Minimum Requirements
The hardware must meet certain requirements to run a full node.
- VPS running recent versions of Mac OS X or Linux.
- 500 GB of free disk space
- 4 cores of CPU and 8 gigabytes of memory (RAM).
- A broadband Internet connection with upload/download speeds of at least 1 megabyte per second

## Settings
### Sync Mode
#### Fast Sync
The default sync mode. Synchronizes a full node doing a fast synchronization by downloading the entire state database, requesting the headers first, and filling in block bodies and receipts afterward. Once the fast sync reaches the best block of the Ethereum network, it switches to full sync mode.

#### Full Sync
Synchronizes a full node starting at genesis, verifying all blocks and executing all transactions. This mode is a bit slower than the fast sync mode but comes with increased security.

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
## Start your fullnode or a validator node
```bash
$ https://github.com/ThaiFi/thaifi.git
## Enter the folder thaifi was cloned into
cd thaifi
## Write genesis state locally
$ docker run -it --rm  -v $PWD:/tfi -w /tfi ethereum/client-go --datadir /tfi/node init genesis.json
## generate  password
$ echo "[Your Password]" > password.txt
## create new account
$ docker run -it --rm -v -v $PWD:/tfi -w /tfi ethereum/client-go --datadir /tfi --password password.txt account new
## Start your fullnode
$ docker run -itd --restart=always -p 30003:30333 --name tfi-node -v $PWD:/tfi -w /tfi ethereum/client-go --datadir /tfi/node --networkid 17 -cache 4096 --port 30333 --mine --unlock [account] --password password.txt  --syncmode=full --gcmode=archive --nousb

```

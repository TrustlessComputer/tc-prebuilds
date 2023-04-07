## Trustless Computer

The module is run on top of bitcoin, which provide an Ethereum-like virtual machine

## Documentation 📝

For more information about BVM Architecture,
please check out the **[Documentation](https://docs.trustless.computer)**.

## Docker prebuild
Available for:
* linux/amd64
* linux/arm/v6
* linux/arm/v7

try now with docker-compose

```yaml
version: "3.9"

services:
  trustless_node_public:
    image: ghcr.io/trustlesscomputer/tc:latest
    pull_policy: always
    restart: always
    stop_grace_period: 5m
    container_name: "trustless_node_public"
    command: [
      "/app/tc",
      "-g",
      "-u", "${BITCOIND_RPC_USERNAME}",
      "-p", "${BITCOIND_RPC_PASSWORD}",
      "-e", "${BITCOIND_RPC_ENDPOINT}",
      "--btc-wallet", "${TC_BTC_WALLET_NAME}"
    ]
    volumes:
      - ./tc-node-data:/app/tcdata
    ports:
      - 11002:10002
```

with env
```dotenv
BITCOIND_RPC_USERNAME=trustless
BITCOIND_RPC_PASSWORD=notrespassing
BITCOIND_RPC_ENDPOINT=172.17.0.1:8332
TC_BTC_WALLET_NAME=wallet-name
```

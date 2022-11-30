<div align="center">

  <h1><code>Mukiza Network</code></h1>

  <strong>A NPoS network for distributed computing. The network supports wasm smart contracts, multi-asset transactions <a href="https://github.com/paritytech/substrate">Substrate</a>.</strong>

  <h3>
    <a href="https://substrate.io/">Docs</a>
    <span> | </span>
    <a href="mailto:tumukundearnold@gmail.com">Email</a>
  </h3>

</div>

## Features

* Consensus related pallets: Babe & GRANDPA
* WASM Smart contract support
* NPoS
* Onchain governance
* Multi-asset support

**Notes:** The code is un-audited and not production ready, use it at your own risk.

## Getting Started

Follow the steps below to get started.

### Rust Setup

First, complete the [Dev Docs Installation](https://docs.substrate.io/v3/getting-started/installation/).

### Build and Run

Use the following command to build the node and run it after build successfully:

```sh
cargo build --release
./target/release/mukiza --dev
```

## Run public testnet

* Modify the genesis config in chain_spec.rs
* Build spec, `./target/release/mukiza build-spec --chain staging > mukiza-staging.json`
* Change original spec to encoded raw spec, `./target/release/mukiza build-spec --chain=mukiza-staging.json --raw > mukiza-staging-raw.json`
* Start your bootnodes, node key can be generate with command `./target/release/mukiza key generate-node-key`.
  ```shell
  ./target/release/mukiza \
       --node-key <your-node-key> \
       --base-path /tmp/bootnode1 \
       --chain mukiza-staging-raw.json \
       --name bootnode1
  ```
* Start your initial validators,
  ```shell
  ./target/release/mukiza \
      --base-path  /tmp/validator1 \
      --chain   mukiza-staging-raw.json \
      --bootnodes  /ip4/<your-bootnode-ip>/tcp/30333/p2p/<your-bootnode-peerid> \
	    --port 30336 \
	    --ws-port 9947 \
	    --rpc-port 9936 \
      --name  validator1 \
      --validator
  ```


---
layout: default
title: Node
rank: 1
---

# Node

How to setup a validator node.  If you are interested in setting up a validator node, send us a message in Github.

### Setup

**Ubuntu 22.04**

```shell
$ git clone https://github.com/hgminerva/humidefi-node.git
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
$ source $HOME/.cargo/env
$ rustc --version
$ rustup default stable
$ rustup update
$ rustup update nightly
$ rustup target add wasm32-unknown-unknown --toolchain nightly
$ rustup show
$ rustup +nightly show
```

### Build

```shell
$ cd  humidefi-node
$ cargo b -r
```

### Run Dev Node

```shell
$ ./substrate-dev-run.sh
```

### Purge Node

If you are purging the bootnode (node01). Purge the database then the keystore.

```shell
$ ./target/release/node-template purge-chain --base-path /tmp/node01
$ rm -rf /tmp/node01/chains/local_testnet/keystore
```

### Generate Aura (SR25519) and Grandpa (ED25519) keys

Make sure you install Subkey utility first.

```shell
$ subkey generate --scheme sr25519
$ subkey inspect --scheme ed25519 "<generated_secret_phrase>"
```
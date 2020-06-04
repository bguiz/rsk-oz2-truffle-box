# RSK + OpenZeppelin 2 Truffle Box

This scaffolds an empty Truffle project,
which is pre-configured to work with the RSK network.

## Set up

Ensure that you have RSKj Regtest running locally.
See [RSK quick start](https://developers.rsk.co/quick-start/step1-install-rsk-local-node/)
for more details.

```shell
mkdir my-rsk-oz2-project
cd my-rsk-oz2-project
truffle unbox bguiz/rsk-oz2-truffle-box
```

If the command was successful,
you should see `Unbox successful, sweet!` output,
followed by a list of truffle commands.

## Usage

After unboxing, use Truffle as you normally would.
For each relevant truffle subcommand,
e.g. `truffle migrate`, `truffle test`, `truffle console`,
you will need to specify the network through the use of
the `--network` flag.

The `truffle-config.js` file comes with definitions for five
possible choices for network:

- `--network regtest`
- `--network testnet`
- `--network localtestnet`
- `--network mainnet`
- `--network localmainnet`

## Networks

- RSK Regtest:
  - This is a `localhost`-only version of the RSK network,
    where no consensus is required,
    and the RSK node running on your computer will be
    the only node on the network.
  - The native currency used in this network has no value,
    and accounts are pre-loaded when the network is initialised.
    available at `faucet.testnet.rsk.co`.
  - Regtest is recommended when faster feedback cycles
    are required during development.
  - `--network regtest`
    - This requires you to set up RSKj on your computer,
      and started with the `--regtest` flag,
      and listening on port `4444`.
    - See [RSK quick start](https://developers.rsk.co/quick-start/step1-install-rsk-local-node/)
      for more details.
- RSK Testnet
  - This a full global deployment of the RSK network,
    where consensus is indeed required.
  - The native currency used in this network has no value,
    and may be acquired from a faucet
    available at `faucet.testnet.rsk.co`.
  - Testnet is recommended when feedback on a
    full global deployment is required during development.
    Think of this as analogous to a staging deployment.
  - `--network testnet`
    - You have the option of connecting through the public node
      available at `public-node.testnet.rsk.co`,
      which does not require you to set up anything locally.
    - See [RSK public nodes](https://developers.rsk.co/rsk/public-nodes/)
      for more details.
  - `--network localtestnet`
    - You also have the option of connecting through a `localhost` node.
      This is recommended, and in line with the
      bitcoiners' maxim: **Don't trust. Verify.**
    - This option requires you to set up RSKj on your computer,
      and started with the `--testnet` flag,
      and listening on port `7777`.
- RSK Mainnet
  - This is a full global deployment of the RSK network,
    where consensus is required.
  - The native currency used in this network has value,
    and may be acquired through mining or a 2-way peg with bitcoin.
  - Mainnet is not recommended during development,
    and is intended for use in a "real" deployment.
    Think of this as analogous to a production deployment.
  - `--network mainnet`
    - You have the option of connecting through the public node
      available at `public-node.rsk.co`,
      which does not require you to set up anything locally.
    - See [RSK public nodes](https://developers.rsk.co/rsk/public-nodes/)
      for more details.
  - `--network localmainnet`
    - You also have the option of connecting through a `localhost` node.
      This is recommended, and in line with the
      bitcoiners' maxim: **Don't trust. Verify.**
    - This option requires you to set up RSKj on your computer,
      and started with the `--mainnet` flag,
      and listening on port `8888`.

## Troubleshooting

### `node-gyp`

`node-gyp` related compile **warnings** are aplenty,
and you may ignore them without issue.

`node-gyp` related compile **errors**, however, may also happen,
and prevent a successful `truffle unbox`.
This issue has nothing to do with this particular Truffle box,
but is related to how `node-gyp` is set up on your system.

```shell
python --version
```

Ensure that you have Python 2.x.
If you have Python 3.x, `node-gyp` tends to balk.

Next, you will need to clean up the cached NodeJs dependencies.

```shell
npm cache clean --force
```

Finally, cross your fingers, and re-run the set up script.

### Re-running the set up

You can re-run the set up script for this Truffle box at any time:

```shell
scripts/setup.sh
```

If you wish to remove all files created byt he setup process:

```shell
scripts/clean.sh
```

## Licence

GPL-3.0

## Author

[Brendan Graetz](http://bguiz.com/)

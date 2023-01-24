# Accounts for testing

You can use existing accounts for testing by including them in the genesis file for a private network. Hyperledger edeXa also provides predefined accounts for use in development mode.

## Development mode

When you start edeXa with the `--network=dev` command line option, edeXa uses the `dev.json` genesis file by default.

The `dev.json` genesis file defines the following accounts used for testing.

\--8<-- "global/test\_accounts.md"

## Genesis file

To use existing test accounts, specify the accounts and balances in a genesis file for your test network. For an example of how to define accounts in the genesis file, see [`dev.json`](https://github.com/hyperledger/besu/blob/750580dcca349d22d024cc14a8171b2fa74b505a/config/src/main/resources/dev.json).

To start edeXa with the genesis file defining the existing accounts, use the `--genesis-file` command line option .

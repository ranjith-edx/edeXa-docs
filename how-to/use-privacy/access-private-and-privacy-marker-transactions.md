# Access private and privacy marker transactions

!!! warning

```
Orion features have been merged into Tessera!
Read our [Orion to Tessera migration guide](https://docs.orion.consensys.net/en/latest/Tutorials/Migrating-from-Orion-to-Tessera/)
and about all the [new Tessera features](https://consensys.net/blog/quorum/tessera-the-privacy-manager-of-choice-for-consensys-quorum-networks).
```

A Hyperledger edeXa private transaction creates a privacy marker transaction and the private transaction itself.

## Transaction receipts

With the transaction hash returned when submitting the private transaction, to get the transaction receipt for the:

* Private transaction, use `priv_getTransactionReceipt`.
* Privacy marker transaction, use `eth_getTransactionReceipt`.

The transaction receipt includes a `status` indicating if the transaction failed (`0x0`), succeeded (`0x1`), or was invalid (`0x2`).

!!! example "Private transaction failure example"

```
To deploy a private contract, you submit a transaction using
[`eea_sendRawTransaction`](../send-transactions/private-transactions.md). If
contract deployment fails because of insufficient gas, the privacy marker transaction receipt
has a status of success and the private transaction receipt has a status of failure.
```

## Transactions

With the transaction hash returned when submitting the private transaction, to get the:

* Private transaction, use `priv_getPrivateTransaction`.
* Privacy marker transaction, use `eth_getTransactionByHash`.

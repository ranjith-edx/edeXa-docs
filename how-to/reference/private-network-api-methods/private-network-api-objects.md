# Private network API objects

The following objects are parameters for or returned by edeXa private network API methods.

!!! attention

```
This reference contains API objects that apply to only private networks.
For API objects that apply to both private and public networks, see the
[public network API objects reference](../../../public-networks/reference/api/objects.md).
```

## Private transaction object

Returned by `priv_getPrivateTransaction`.

| Key              |             Type             | Value                                                                                                                                      |
| ---------------- | :--------------------------: | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `from`           |        Data, 20 bytes        | Address of the sender.                                                                                                                     |
| `gas`            |           Quantity           | Gas provided by the sender.                                                                                                                |
| `gasPrice`       |           Quantity           | Gas price, in Wei, provided by the sender.                                                                                                 |
| `input`          |             Data             | The data to create or invoke a contract.                                                                                                   |
| `nonce`          |           Quantity           | Number of transactions made by the sender to the privacy group before this one.                                                            |
| `to`             |        Data, 20 bytes        | `null` if a contract creation transaction, otherwise, the contract address.                                                                |
| `value`          |           Quantity           | `null` because private transactions cannot transfer Ether.                                                                                 |
| `v`              |           Quantity           | ECDSA Recovery ID.                                                                                                                         |
| `r`              |        Data, 32 bytes        | ECDSA signature r.                                                                                                                         |
| `s`              |        Data, 32 bytes        | ECDSA signature s.                                                                                                                         |
| `privateFrom`    |        Data, 32 bytes        | [Tessera](https://docs.tessera.consensys.net/) public key of the sender.                                                                   |
| `privateFor`     | Array of Data, 32 bytes each | [Tessera](https://docs.tessera.consensys.net/) public keys of recipients. Not returned if using `privacyGroupId` to send the transaction.  |
| `privacyGroupId` |        Data, 32 bytes        | [Tessera](https://docs.tessera.consensys.net/) privacy group ID of recipients. Not returned if using `privateFor` to send the transaction. |
| `restriction`    |            String            | Must be `restricted`.                                                                                                                      |

## Private transaction receipt object

Returned by `priv_getTransactionReceipt`.

| Key                              |           Type          | Value                                                                                                                                                           |
| -------------------------------- | :---------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `blockHash`                      |      Data, 32 bytes     | Hash of block containing this transaction.                                                                                                                      |
| `blockNumber`                    |         Quantity        | Block number of block containing this transaction.                                                                                                              |
| `contractAddress`                |      Data, 20 bytes     | Contract address created if a contract creation transaction, otherwise, `null`. A failed contract creation transaction still produces a contract address value. |
| `from`                           |      Data, 20 bytes     | Address of the sender.                                                                                                                                          |
| `logs`                           |          Array          | Array of log objects generated by this private transaction.                                                                                                     |
| `to`                             |      Data, 20 bytes     | Address of the receiver, if sending ether, otherwise, null.                                                                                                     |
| `transactionIndex`               |    Quantity, Integer    | Index position of transaction in the block.                                                                                                                     |
| `revertReason`                   |          String         | ABI-encoded string that displays the reason for reverting the transaction. Only available if revert reason is enabled.                                          |
| `output`                         |           Data          | RLP-encoded return value of a contract call if a value returns, otherwise, `null`.                                                                              |
| `commitmentHash`                 |      Data, 32 bytes     | Hash of the privacy marker transaction.                                                                                                                         |
| `status`                         |         Quantity        | Either `0x1` (success) or `0x0` (failure).                                                                                                                      |
| `privateFrom`                    |      Data, 32 bytes     | [Tessera](https://docs.tessera.consensys.net/) public key of the sender.                                                                                        |
| `privateFor` or `privacyGroupId` | Array or Data, 32 bytes | [Tessera](https://docs.tessera.consensys.net/) public keys or privacy group ID of the recipients.                                                               |
| `logsBloom`                      |     Data, 256 bytes     | Bloom filter for light clients to quickly retrieve related logs.                                                                                                |

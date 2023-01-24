# edeXa API objects

The following objects are parameters for or returned by Besu API methods.

!!! attention

```
This reference contains API objects that apply to both public and private networks.
For private-network-specific API objects, see the
[private network API object reference](../../../private-networks/reference/api/objects.md).
```

## Block object

Returned by `eth_getBlockByHash` and `eth_getBlockByNumber`.

| Key                |         Type        | Value                                                                                                                                                                                    |
| ------------------ | :-----------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `number`           | _Quantity_, Integer | Block number. `null` when block is pending.                                                                                                                                              |
| `hash`             |   _Data_, 32 bytes  | Hash of the block. `null` when block is pending.                                                                                                                                         |
| `parentHash`       |   _Data_, 32 bytes  | Hash of the parent block.                                                                                                                                                                |
| `nonce`            |   _Data_, 8 bytes   | Hash of the generated proof of work. `null` when block is pending.                                                                                                                       |
| `sha3Uncles`       |   _Data_, 32 bytes  | SHA3 of the uncle's data in the block.                                                                                                                                                   |
| `logsBloom`        |  _Data_, 256 bytes  | Bloom filter for the block logs. `null` when block is pending.                                                                                                                           |
| `transactionsRoot` |   _Data_, 32 bytes  | Root of the transaction trie for the block.                                                                                                                                              |
| `stateRoot`        |    Data, 32 bytes   | Root of the final state trie for the block.                                                                                                                                              |
| `receiptsRoot`     |    Data, 32 bytes   | Root of the receipts trie for the block.                                                                                                                                                 |
| `miner`            |    Data, 20 bytes   | Address to pay mining rewards to.                                                                                                                                                        |
| `difficulty`       |  Quantity, Integer  | Difficulty for this block.                                                                                                                                                               |
| `totalDifficulty`  |  Quantity, Integer  | Total difficulty of the chain until this block. This value will always be `0` for an uncle block.                                                                                        |
| `extraData`        |         Data        | Extra data field for this block. The first 32 bytes is vanity data you can set using the `--miner-extra-data` command line option. Stores extra data when used with Clique and IBFT.     |
| `size`             |  Quantity, Integer  | Size of block in bytes.                                                                                                                                                                  |
| `gasLimit`         |       Quantity      | Maximum gas allowed in this block.                                                                                                                                                       |
| `gasUsed`          |       Quantity      | Total gas used by all transactions in this block.                                                                                                                                        |
| `timestamp`        |       Quantity      | Unix timestamp for block assembly.                                                                                                                                                       |
| `transactions`     |        Array        | Array of [transaction objects](broken-reference), or 32 byte transaction hashes depending on the specified boolean parameter.                                                            |
| `uncles`           |        Array        | Array of uncle hashes.                                                                                                                                                                   |
| `baseFeePerGas`    |       Quantity      | The block's base fee per gas. This field is empty for blocks created before [EIP-1559](https://github.com/ethereum/EIPs/blob/2d8a95e14e56de27c5465d93747b0006bd8ac47f/EIPS/eip-1559.md). |

## Fee history results object

Returned by `eth_feeHistory` for the requested block range. If blocks in the specified block range are not available, then only the fee history for available blocks is returned.

| Key             |        Type       | Value                                                                                                                                                                                                                                                                                                   |
| --------------- | :---------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `oldestBlock`   | Quantity, Integer | Lowest number block of the returned range.                                                                                                                                                                                                                                                              |
| `baseFeePerGas` |       Array       | Array of block base fees per gas, including an extra block value. The extra value is the next block after the newest block in the returned range. Returns zeroes for blocks created before [EIP-1559](https://github.com/ethereum/EIPs/blob/2d8a95e14e56de27c5465d93747b0006bd8ac47f/EIPS/eip-1559.md). |
| `gasUsedRatio`  |       Array       | Array of block gas used ratios. These are calculated as the ratio of `gasUsed` and `gasLimit`.                                                                                                                                                                                                          |

## Filter options object

Parameter for `eth_newFilter`, `eth_getLogs`, and `priv_getLogs`. Used to `filter logs`.

| Key         |             Type             | Required/Optional | Value                                                                                              |
| ----------- | :--------------------------: | :---------------: | -------------------------------------------------------------------------------------------------- |
| `fromBlock` |        Quantity \| Tag       |      Optional     | Integer block number or `latest`, `pending`, `earliest`. See Block Parameter. Default is `latest`. |
| `toBlock`   |        Quantity \| Tag       |      Optional     | Integer block number or `latest`, `pending`, `earliest`. See Block Parameter. Default is `latest`. |
| `address`   |         Data \| Array        |      Optional     | Contract address or array of addresses from which logs originate.                                  |
| `topics`    | Array of Data, 32 bytes each |      Optional     | Array of topics by which to filter logs.                                                           |

`eth_getLogs` and `priv_getLogs` have an extra key.

| Key         |      Type      | Required/Optional | Value                                                                                                             |
| ----------- | :------------: | :---------------: | ----------------------------------------------------------------------------------------------------------------- |
| `blockHash` | Data, 32 bytes |     Optional.     | Hash of block for which to return logs. If you specify `blockHash`, you cannot specify `fromBlock` and `toBlock`. |

## Log object

Returned by `eth_getFilterChanges` and `priv_getLogs`. [`Transaction receipt objects`](broken-reference) can contain an array of log objects.

| Key                |             Type             | Value                                                                               |
| ------------------ | :--------------------------: | ----------------------------------------------------------------------------------- |
| `removed`          |              Tag             | `true` if log removed because of a chain reorganization. `false` if a valid log.    |
| `logIndex`         |       Quantity, Integer      | Log index position in the block. `null` when log is pending.                        |
| `transactionIndex` |       Quantity, Integer      | Index position of the starting transaction for the log. `null` when log is pending. |
| `transactionHash`  |        Data, 32 bytes        | Hash of the starting transaction for the log. `null` when log is pending.           |
| `blockHash`        |        Data, 32 bytes        | Hash of the block that includes the log. `null` when log is pending.                |
| `blockNumber`      |           Quantity           | Number of block that includes the log. `null` when log is pending.                  |
| `address`          |        Data, 20 bytes        | Address the log originated from.                                                    |
| `data`             |             Data             | Non-indexed arguments of the log.                                                   |
| `topics`           | Array of Data, 32 bytes each | Event signature hash and 0 to 3 indexed log arguments.                              |

## Miner data object

Returned by `eth_getMinerDataByBlockHash` and `eth_getMinerDataByBlockNumber`.

| Key                    |        Type       | Value                                                                                                                              |
| ---------------------- | :---------------: | ---------------------------------------------------------------------------------------------------------------------------------- |
| `netBlockReward`       | Quantity, Integer | The net block reward, in Wei, is `staticBlockReward + transactionFee + uncleInclusionReward`.                                      |
| `staticBlockReward`    | Quantity, Integer | The static block reward, in Wei, is preset on a hard fork.                                                                         |
| `transactionFee`       | Quantity, Integer | The transaction fee, in Wei, is `sum of upfront cost - refund amount for all transactions`.                                        |
| `uncleInclusionReward` | Quantity, Integer | The uncle inclusion reward, in Wei, is `static block reward * number of ommers/32`.                                                |
| `uncleRewards`         |        Map        | Map of uncle block hashes and uncle miner coinbase addresses.                                                                      |
| `coinbase`             |   Data, 20 bytes  | Coinbase address.                                                                                                                  |
| `extraData`            |        Data       | Extra data field for this block. The first 32 bytes is vanity data you can set using the `--miner-extra-data` command line option. |
| `difficulty`           | Quantity, Integer | Difficulty of this block.                                                                                                          |
| `totalDifficulty`      | Quantity, Integer | Total difficulty of the chain until this block.                                                                                    |

## Pending transaction object

Returned by `txpool_besuPendingTransactions`.

| Key                    |        Type       | Value                                                                                                                                                        |
| ---------------------- | :---------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `accessList`           |       Array       | (Optional) List of addresses and storage keys the transaction plans to access. Used in `ACCESS_LIST` transactions and may be used in `EIP1559` transactions. |
| `from`                 |   Data, 20 bytes  | Address of the sender.                                                                                                                                       |
| `gas`                  |      Quantity     | Gas provided by the sender.                                                                                                                                  |
| `gasPrice`             |      Quantity     | (Optional) Gas price, in Wei, provided by the sender. Not used only in `EIP1559` transactions.                                                               |
| `maxPriorityFeePerGas` | Quantity, Integer | (Optional) Maximum fee, in Wei, the sender is willing to pay per gas above the base fee. Used only in `EIP1559` transactions.                                |
| `maxFeePerGas`         | Quantity, Integer | (Optional) Maximum total fee (base fee + priority fee), in Wei, the sender is willing to pay per gas. Used only in `EIP1559` transactions.                   |
| `hash`                 |   Data, 32 bytes  | Hash of the transaction.                                                                                                                                     |
| `input`                |        Data       | Data sent with the transaction to create or invoke a contract.                                                                                               |
| `nonce`                |      Quantity     | Number of transactions made by the sender before this one.                                                                                                   |
| `to`                   |   Data, 20 bytes  | Address of the receiver. `null` if a contract creation transaction.                                                                                          |
| `transactionType`      |       String      | Transaction type.                                                                                                                                            |
| `value`                |      Quantity     | Value transferred, in Wei.                                                                                                                                   |
| `v`                    |      Quantity     | ECDSA Recovery ID.                                                                                                                                           |
| `r`                    |   Data, 32 bytes  | ECDSA signature r.                                                                                                                                           |
| `s`                    |   Data, 32 bytes  | ECDSA signature s.                                                                                                                                           |

## Range object

Returned by `debug_storageRangeAt`.

| Key       |  Type  | Value                                                                      |
| --------- | :----: | -------------------------------------------------------------------------- |
| `storage` | Object | Key hash and value. Pre-image key is `null` if it falls outside the cache. |
| `nextKey` |  Hash  | Hash of next key if further storage in range. Otherwise, not included.     |

### Structured log object

Log information returned as part of the [Trace object](broken-reference).

| Key                      |           Type          | Value                                                                                                                                                                                                                                                                                                                                            |
| ------------------------ | :---------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `pc`                     |         Integer         | Current program counter.                                                                                                                                                                                                                                                                                                                         |
| `op`                     |          String         | Current OpCode.                                                                                                                                                                                                                                                                                                                                  |
| `gas`                    |         Integer         | Gas remaining.                                                                                                                                                                                                                                                                                                                                   |
| `gasCost`                |         Integer         | Cost in wei of each gas unit.                                                                                                                                                                                                                                                                                                                    |
| `depth`                  |         Integer         | Execution depth.                                                                                                                                                                                                                                                                                                                                 |
| `exceptionalHaltReasons` |          Array          | One or more strings representing an error condition causing the EVM execution to terminate. These strings suggest that EVM execution terminated for reasons such as running out of gas or attempting to execute an unknown instruction. Generally a single exceptional halt reason returns but it's possible for more than one to occur at once. |
| `stack`                  | Array of 32 byte arrays | EVM execution stack before executing current operation.                                                                                                                                                                                                                                                                                          |
| `memory`                 | Array of 32 byte arrays | Memory space of the contract before executing current operation.                                                                                                                                                                                                                                                                                 |
| `storage`                |          Object         | Storage entries changed by the current transaction.                                                                                                                                                                                                                                                                                              |

## Trace object

Returned by `debug_traceBlock`, `debug_traceBlockByHash`, `debug_traceBlockByNumber`, and `debug_traceTransaction`.

| Key           |   Type  | Value                                                              |
| ------------- | :-----: | ------------------------------------------------------------------ |
| `gas`         | Integer | Gas used by the transaction.                                       |
| `failed`      | Boolean | True if transaction failed, otherwise, false.                      |
| `returnValue` |  String | Bytes returned from transaction execution (without a `0x` prefix). |
| `structLogs`  |  Array  | Array of structured log objects.                                   |

## Trace filter options object

Parameter for `trace_filter`. All parameters are optional.

| Key           |      Type     | Value                                              |
| ------------- | :-----------: | -------------------------------------------------- |
| `fromBLock`   | String \| Tag | Trace starts at this block.                        |
| `toBlock`     | String \| Tag | Trace stops at this block.                         |
| `fromAddress` |     String    | Include only traces sent from this address.        |
| `toAddress`   |     String    | Include only traces with this destination address. |
| `after`       |    Quantity   | The offset trace number.                           |
| `count`       |    Integer    | Number of traces to display in a batch.            |

## Transaction object

Returned by `eth_getTransactionByHash`, `eth_getTransactionByBlockHashAndIndex`, and `eth_getTransactionByBlockNumberAndIndex`.

| Key                    |        Type       | Value                                                                                                                                                                                  |
| ---------------------- | :---------------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accessList`           |       Array       | (Optional) List of addresses and storage keys the transaction plans to access. Used in `ACCESS_LIST` transactions and may be used in `EIP1559` transactions.                           |
| `blockHash`            |   Data, 32 bytes  | Hash of the block containing this transaction. `null` when transaction is pending.                                                                                                     |
| `blockNumber`          |      Quantity     | Block number of the block containing this transaction. `null` when transaction is pending.                                                                                             |
| `chainId`              |      Quantity     | Chain ID.                                                                                                                                                                              |
| `from`                 |   Data, 20 bytes  | Address of the sender.                                                                                                                                                                 |
| `gas`                  |      Quantity     | Gas provided by the sender.                                                                                                                                                            |
| `gasPrice`             |      Quantity     | (Optional) Gas price, in Wei, provided by the sender. Used only in non-`EIP1559` transactions.                                                                                         |
| `maxPriorityFeePerGas` | Quantity, Integer | (Optional) Maximum fee, in Wei, the sender is willing to pay per gas above the base fee. Used only in `EIP1559` transactions.                                                          |
| `maxFeePerGas`         | Quantity, Integer | (Optional) Maximum total fee (base fee + priority fee), in Wei, the sender is willing to pay per gas. Used only in `EIP1559` transactions.                                             |
| `hash`                 |   Data, 32 bytes  | Hash of the transaction.                                                                                                                                                               |
| `input`                |        Data       | Data sent with the transaction to create or invoke a contract. For private transactions, it's a pointer to the transaction location in [Tessera](https://docs.tessera.consensys.net/). |
| `nonce`                |      Quantity     | Number of transactions made by the sender before this one.                                                                                                                             |
| `to`                   |   Data, 20 bytes  | Address of the receiver. `null` if a contract creation transaction.                                                                                                                    |
| `transactionIndex`     | Quantity, Integer | Index position of the transaction in the block. `null` when transaction is pending.                                                                                                    |
| `transactionType`      |       String      | Transaction type.                                                                                                                                                                      |
| `value`                |      Quantity     | Value transferred, in Wei.                                                                                                                                                             |
| `v`                    |      Quantity     | ECDSA Recovery ID.                                                                                                                                                                     |
| `r`                    |   Data, 32 bytes  | ECDSA signature r.                                                                                                                                                                     |
| `s`                    |   Data, 32 bytes  | ECDSA signature s.                                                                                                                                                                     |

## Transaction call object

Parameter for `eth_call` and `eth_estimateGas`.

All transaction call object parameters are optional.

| Key                    |        Type       | Value                                                                                                                                                                                                                                                                 |
| ---------------------- | :---------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `from`                 |   Data, 20 bytes  | Address of the sender.                                                                                                                                                                                                                                                |
| `to`                   |   Data, 20 bytes  | Address of the action receiver.                                                                                                                                                                                                                                       |
| `gas`                  | Quantity, Integer | Gas provided by the sender. `eth_call` consumes zero gas, but other executions might need this parameter. `eth_estimateGas` ignores this value.                                                                                                                       |
| `gasPrice`             | Quantity, Integer | Gas price, in Wei, provided by the sender. The default is `0`. Used only in non-`EIP1559` transactions.                                                                                                                                                               |
| `maxPriorityFeePerGas` | Quantity, Integer | Maximum fee, in Wei, the sender is willing to pay per gas above the base fee. Can be used only in `EIP1559` transactions. If used, must specify `maxFeePerGas`.                                                                                                       |
| `maxFeePerGas`         | Quantity, Integer | Maximum total fee (base fee + priority fee), in Wei, the sender is willing to pay per gas. Can be used only in `EIP1559` transactions. If used, must specify `maxPriorityFeePerGas`.                                                                                  |
| `value`                | Quantity, Integer | Value transferred, in Wei.                                                                                                                                                                                                                                            |
| `data`                 |        Data       | Hash of the method signature and encoded parameters. For details, see [Ethereum Contract ABI](https://solidity.readthedocs.io/en/develop/abi-spec.html).                                                                                                              |
| `accessList`           |       Array       | List of addresses and storage keys that the transaction plans to access. Used only in non-`FRONTIER` transactions.                                                                                                                                                    |
| `strict`               |        Tag        | If `true`, checks that the `from` account’s ether balance is sufficient to cover the transaction and gas fee. If `false`, the `gasPrice` and `baseFee` are set to zero, in order to simulate a transaction without enforcing a balance check. The default is `false`. |

## Transaction receipt object

Returned by `eth_getTransactionReceipt`.

| Key                 |        Type       | Value                                                                                                                                                          |
| ------------------- | :---------------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `blockHash`         |   Data, 32 bytes  | Hash of block containing this transaction.                                                                                                                     |
| `blockNumber`       |      Quantity     | Block number of block containing this transaction.                                                                                                             |
| `contractAddress`   |   Data, 20 bytes  | Contract address created, if contract creation transaction, otherwise, `null`. A failed contract creation transaction still produces a contract address value. |
| `cumulativeGasUsed` |      Quantity     | Total amount of gas used by previous transactions in the block and this transaction.                                                                           |
| `effectiveGasPrice` |      Quantity     | The actual value per gas deducted from the sender's account.                                                                                                   |
| `from`              |   Data, 20 bytes  | Address of the sender.                                                                                                                                         |
| `gasUsed`           |      Quantity     | Amount of gas used by this specific transaction.                                                                                                               |
| `logs`              |       Array       | Array of [log objects](broken-reference) generated by this transaction.                                                                                        |
| `logsBloom`         |  Data, 256 bytes  | Bloom filter for light clients to quickly retrieve related logs.                                                                                               |
| `status`            |      Quantity     | Either `0x0` (failure), `0x1` (success), or `0x2` (invalid).                                                                                                   |
| `to`                |   Data, 20 bytes  | Address of the receiver, if sending ether, otherwise, null.                                                                                                    |
| `transactionHash`   |   Data, 32 bytes  | Hash of the transaction.                                                                                                                                       |
| `transactionIndex`  | Quantity, Integer | Index position of transaction in the block.                                                                                                                    |
| `transactionType`   |       String      | Transaction type.                                                                                                                                              |
| `revertReason`      |       String      | ABI-encoded string that displays the reason for reverting the transaction. Only available if revert reason is enabled.                                         |
| `type`              |      Quantity     | Transaction type, `0x00` for legacy transactions, `0x01` for access list types, `0x02` for dynamic fees.                                                       |

!!!note

```
For pre-Byzantium transactions, the transaction receipt object includes the following instead
of `status`:
```

| Key    |      Type      | Value                       |
| ------ | :------------: | --------------------------- |
| `root` | Data, 32 bytes | Post-transaction state root |

## Transaction trace object

Returned by `trace_replayBlockTransactions`.

| Key               |      Type      | Value                                                |
| ----------------- | :------------: | ---------------------------------------------------- |
| `output`          |     Boolean    | Transaction result. 1 for success and 0 for failure. |
| `stateDiff`       |     Object     | State changes in the requested block.                |
| `trace`           |      Array     | Ordered list of calls to other contracts.            |
| `vmTrace`         |     Object     | Ordered list of EVM actions.                         |
| `transactionHash` | Data, 32 bytes | Hash of the replayed transaction.                    |

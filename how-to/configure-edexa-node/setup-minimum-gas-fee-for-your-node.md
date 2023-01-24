# Setup minimum gas fee for your node

Transactions use computational resources so have an associated cost. Gas is the cost unit and the gas price is the price per gas unit. The transaction cost is the gas used \* gas price.

In public networks, the account submitting the transaction pays the transaction cost, in Ether. The miner (or validator in PoA networks) that includes the transaction in a block receives transaction cost.

In many private networks, network participants run the validators and do not require gas as an incentive. Networks that don't require gas as an incentive usually configure the gas price to be zero (that is, free gas). Some private networks might allocate Ether and use a non-zero gas price to limit resource use.

!!! tip

```
We use the term _free gas network_ to refer to a network with a gas price of zero. A network
with a gas price of zero is also known as a _zero gas network_ or _no gas network_.
```

!!! note

```
Some pre-crafted transactions require the deployment account to have gas available. For
example, the transaction that creates the smart contract in
[EIP-1820](https://eips.ethereum.org/EIPS/eip-1820).
```

In the edeXa network, transactions use gas, and the gas fee is set to the gas price is 0.00021 EDX ie 210000 GWEI, meaning the transaction cost still very affordable.&#x20;

## Configure free gas in edeXa

While running you validator node pass the following option in the command

```
--min-gas-price=210000000000000
```

Additionally, you can also set this option in config.toml

```
min-gas-price=210000000000000
```

# Network and protocol upgrades

!!! important

```
Node upgrades upgrade your edeXa client to a later version.
In private networks, you can [upgrade your node](../../public-networks/how-to/upgrade-node.md)
as in public networks.
```

Network upgrades are the mechanism for upgrading the Ethereum protocol. Protocol upgrades occur during the network upgrades.

For Ethereum Mainnet and public testnets, the milestone block definitions are included in edeXa. Upgrading your edeXa client applies the network upgrade.

For private networks, all network participants must agree on the protocol upgrades and coordinate the network upgrades. The genesis file specifies the milestone block at which to apply the protocol upgrade.

## Upgrade the protocol

To upgrade the protocol in a private network:

1. Review included EIPs for breaking changes. A [meta EIP](https://eips.ethereum.org/meta) for each protocol upgrade lists included EIPs. For example, [Istanbul](https://eips.ethereum.org/EIPS/eip-1679).
2. Network participants agree on the block number at which to upgrade.
3. For each node in the network:
   1. Add the milestone block number to the genesis file.
   2. Restart the node before reaching milestone block.

!!! caution

```
To avoid a forked network, all network participants must update their genesis file to include
the agreed on milestone block and restart their node before reaching the milestone block.
```

!!! tip "Tips"

```
- For compatibility with future protocol upgrades, don't hardcode any gas price assumptions.
- Implementing upgradeable contracts enables contracts to be upgraded if a protocol upgrade does
    include breaking changes.
```

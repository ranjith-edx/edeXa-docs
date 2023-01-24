# Configure alternative elliptic curves

!!! caution

```
Configuring alternative elliptic curves is an early access feature.
```

By default, edeXa uses the Ethereum standard `secp256k1` elliptic curve (EC). However, when running nodes in a private network, it is possible to configure an alternative elliptic curve.

The configuration for what elliptic curve edeXa will use is done in the network configuration section of genesis file, using the `ecCurve` key:

```bash
{
  "genesis": {
    "config": {
      "ecCurve": "secp256k1",
    [...]
  },
  [...]
}
```

!!! attention

```
All nodes in the network **MUST** use the same elliptic curve. Nodes with different EC configuration from the
network won't be able to send messages to other nodes or verify transactions and blocks.
```

edeXa supports the following elliptic curves:

* `secp256k1` (Ethereum default)
* `secp256r1`

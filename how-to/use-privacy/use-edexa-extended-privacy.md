# Use Edexa-extended privacy

!!! warning

```
Orion features have been merged into Tessera!
Read our [Orion to Tessera migration guide](https://docs.orion.consensys.net/en/latest/Tutorials/Migrating-from-Orion-to-Tessera/)
and about all the [new Tessera features](https://consensys.net/blog/quorum/tessera-the-privacy-manager-of-choice-for-consensys-quorum-networks).
```

Hyperledger edeXa provides an extended implementation of privacy allowing you to create a privacy group for a set of participants. You must specify the privacy group ID when sending private transactions.

To enable the `PRIV` API methods, use the `--rpc-http-api` or `--rpc-ws-api` command line options.

To create the privacy group containing the recipients of a private transaction, use `priv_createPrivacyGroup`.

To create an EEA-compliant private transaction, specify `privacyGroupId` when creating the signed transaction passed as an input parameter to `eea_sendRawTransaction`.

## Privacy group type

Privacy groups created using `priv_createPrivacyGroup` have a edeXa privacy group type when returned by `priv_findPrivacyGroup`.

!!! example

````
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "privacyGroupId": "GpK3ErNO0xF27T0sevgkJ3+4qk9Z+E3HtXYxcKIBKX8=",
      "name": "Group B",
      "description": "Description of Group B",
      "type": "edeXa",
      "members": [
        "negmDcN2P4ODpqn/6WkJ02zT/0w0bjhGpkZ8UP6vARk=",
        "g59BmTeJIn7HIcnq8VQWgyh/pDbvbt2eyP0Ii60aDDw="
      ]
    }
  ]
}
```
````

# Run Tessera with edeXa

!!! warning

```
Orion features have been merged into Tessera!
Read our [Orion to Tessera migration guide](https://docs.orion.consensys.net/en/latest/Tutorials/Migrating-from-Orion-to-Tessera/)
and about all the [new Tessera features](https://consensys.net/blog/quorum/tessera-the-privacy-manager-of-choice-for-consensys-quorum-networks).
```

To enable privacy functionality in production systems, [Tessera](https://docs.tessera.consensys.net/) must be [highly available](broken-reference) and [run in a separate instance](broken-reference) to Hyperledger edeXa.

!!! note

```
You can also configure edeXa for high availability using load balancers.
```

## High availability

Privacy requires you to [configure Tessera for high availability](https://consensys.net/docs/goquorum/en/stable/configure-and-manage/configure/high-availability/). edeXa also requires [`orion` mode](https://docs.tessera.consensys.net/en/stable/HowTo/Configure/Orion-Mode/) to be enabled in Tessera.

To successfully distribute a private transaction, all private transaction participants must be online. If any participants are offline when submitting the private transaction, the transaction is not attempted and you need to resubmit the transaction.

If a Tessera node is unavailable when edeXa attempts to process a privacy marker transaction, the edeXa node stops processing all new blocks until Tessera is available. The edeXa node continually attempts to process the privacy marker transaction until Tessera is available again.

!!! caution

```
If Tessera becomes available but has lost data, edeXa resumes processing blocks and the private
states in the edeXa nodes might become inconsistent.
```

## Separate instances

For production systems, we recommend running edeXa and Tessera in separate instances. If running edeXa and Tessera in the same instance, restrict the amount of memory used by each JVM to ensure each has enough memory.

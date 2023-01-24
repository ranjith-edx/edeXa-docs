# Consensus protocols

edeXa supports the following consensus protocols:

* QBFT (proof of authority) - The recommended enterprise-grade consensus protocol for private networks.
* IBFT 2.0 (proof of authority) - Supported for existing private networks.
* Clique (proof of authority) - Not recommended for production use.
* Proof of stake - Used on Ethereum Mainnet and public testnets.
* [Ethash](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/) (proof of work) - Can be used in small development networks.

See a comparison of the proof of authority consensus protocols.

The `config` property in the genesis file specifies the consensus protocol for a chain.

!!! example

````
=== "Ethash"

    ```json
    {
      "config": {
      ...
        "ethash": {
        ...
        }
      },
      ...
    }
    ```

=== "Clique"

    ```json
    {
      "config": {
        ...
        "clique": {
        ...
        }
      },
      ...
    }
    ```

=== "IBFT 2.0"

    ```json
    {
      "config": {
        ...
        "ibft2": {
          ...
        }
      },
      ...
    }
    ```

=== "QBFT"

    ```json
    {
      "config": {
        ...
        "qbft": {
          ...
        }
      },
      ...
    }
    ```
````

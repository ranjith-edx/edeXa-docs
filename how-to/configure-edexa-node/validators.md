# Validators

## Spinning up the Validator Nodes

As when configuring Nodes:

1. Create the node key pair (that is, the private and public key) before starting the validator.
2. When creating validators in the cloud (for example, AWS or Azure), attempt to assign static IP addresses to them. If your network is:
   * Publicly accessible, assign an elastic IP address.
   * Internal only, specify a private IP address when you create the instance and record this IP address.

## Running the Node

To run the Node make sure you have followed the [pre-requisite](<../../README (1).md>) section.

* Download the edeXa Blockchain by running the following command.

```bash
curl -L -O https://edexa-blockchain.s3.eu-central-1.amazonaws.com/edexa-blockchain.zip
```

* Unzip the edeXa-blockchain.zip.&#x20;
* Run the following command to start the node

{% code overflow="wrap" %}
```bash
./bin/edexa --data-path=data --Xdns-enabled=true --Xdns-update-enabled=true --bootnodes=enode://4c835ac847d2f0e8d2ce1a2c873da815028517ca3c13d8b5e297a07ff7c83daaf15a84370c6a84426bb6518052ebc4cc7f4057285d56eebc2b9fae1e76b4d552@edx-dataseed1.testnet.edexa.com:30303,enode://2c4f0b38cf4a13034155b8b390d1146ef3a588b932f7c49d3830372e96fe74bca2983dd7eed6a30bf7bcc77e937d59d9e014d8f2eba94c9699f2d50da6575925@edx-dataseed2.testnet.edexa.com:30303 --config-file=./config.toml
```
{% endcode %}

Once the command is executed successfully you will see following logs.

<figure><img src="https://edexa-blockchain.s3.eu-central-1.amazonaws.com/Sync.png" alt=""><figcaption><p>your node is syncing with blockchain.</p></figcaption></figure>

!!! important&#x20;

```
It takes around 2-3 hours to sync the blockchain with your node.
```

Once the chain is fully synced you will see the following logs.

<figure><img src="https://edexa-blockchain.s3.eu-central-1.amazonaws.com/observing.png" alt=""><figcaption><p>Importing live blocks</p></figcaption></figure>

## Adding and removing validators

To turn your node from the observing node to the Validator node, contact us at <mark style="color:blue;">support@edexa.com</mark>

## Validators as bootnodes

Validators can also be bootnodes. Other than the usual configuration for bootnodes, you do not need to specify any extra configuration when a validator is also a bootnode.

If you remove a validator that is also a bootnode, ensure there are enough remaining bootnodes on the network.

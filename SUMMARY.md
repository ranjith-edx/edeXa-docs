# Table of contents

## Fundamentals

* [🛠 Getting started](README.md)
  * [System requirements](fundamentals/getting-started/system-requirements.md)
  * [Install edeXa](fundamentals/getting-started/install-edexa/README.md)
    * [Run edeXa from a Docker image](fundamentals/getting-started/install-edexa/run-edexa-from-a-docker-image.md)
    * [Install binary distribution](fundamentals/getting-started/install-edexa/install-binary-distribution.md)
  * [Start edeXa](fundamentals/getting-started/start-edexa.md)

## How to

* [configure](how-to/configure/README.md)
  * [Consensus protocols](how-to/configure/consensus-protocols/README.md)
    * [Configure QBFT consensus](how-to/configure/consensus-protocols/configure-qbft-consensus.md)
    * [Configure IBFT 2.0 consensus](how-to/configure/consensus-protocols/configure-ibft-2.0-consensus.md)
    * [Configure Clique consensus](how-to/configure/consensus-protocols/configure-clique-consensus.md)
    * [Add and remove validators without voting](how-to/configure/consensus-protocols/add-and-remove-validators-without-voting.md)
  * [Configure free gas networks](how-to/configure/configure-free-gas-networks.md)
  * [Configure bootnodes](how-to/configure/configure-bootnodes.md)
  * [Validators](how-to/configure/validators.md)
  * [Pre-deploy contracts in the genesis file](how-to/configure/pre-deploy-contracts-in-the-genesis-file.md)
  * [TLS](how-to/configure/tls/README.md)
    * [Configure client and server TLS](how-to/configure/tls/configure-client-and-server-tls.md)
    * [Configure P2P TLS](how-to/configure/tls/configure-p2p-tls.md)
  * [Block proposal permissioning](how-to/configure/block-proposal-permissioning.md)
  * [Configure alternative elliptic curves](how-to/configure/configure-alternative-elliptic-curves.md)
* [Create and send transactions](how-to/create-and-send-transactions/README.md)
  * [Send concurrent private transactions](how-to/create-and-send-transactions/send-concurrent-private-transactions.md)
  * [Send concurrent private transactions](how-to/create-and-send-transactions/send-concurrent-private-transactions-1.md)
  * [Revert reason](how-to/create-and-send-transactions/revert-reason.md)
* [Monitoring](how-to/monitoring/README.md)
  * [Grafana Loki](how-to/monitoring/grafana-loki.md)
  * [Use Elastic Stack](how-to/monitoring/use-elastic-stack.md)
  * [Use Quorum Hibernate](how-to/monitoring/use-quorum-hibernate.md)
  * [Use Splunk](how-to/monitoring/use-splunk.md)
  * [Use OpenTelemetry](how-to/monitoring/use-opentelemetry.md)
* [use-privacy](how-to/use-privacy/README.md)
  * [Use EEA-compliant privacy](how-to/use-privacy/use-eea-compliant-privacy.md)
  * [Use Edexa-extended privacy](how-to/use-privacy/use-edexa-extended-privacy.md)
  * [Run Tessera with edeXa](how-to/use-privacy/run-tessera-with-edexa.md)
  * [Performance best practices](how-to/use-privacy/performance-best-practices.md)
  * [Sign privacy marker transactions](how-to/use-privacy/sign-privacy-marker-transactions.md)
  * [Use flexible privacy groups](how-to/use-privacy/use-flexible-privacy-groups.md)
  * [Access private and privacy marker transactions](how-to/use-privacy/access-private-and-privacy-marker-transactions.md)
  * [Use the web3js-quorum client library](how-to/use-privacy/use-the-web3js-quorum-client-library.md)
* [Use-permissioning](how-to/use-permissioning/README.md)
  * [Use onchain permissioning](how-to/use-permissioning/use-onchain-permissioning.md)
  * [Use local permissioning](how-to/use-permissioning/use-local-permissioning.md)
* [Deploy for Production](how-to/deploy-for-production/README.md)
  * [Connect to Ethstats network monitor](how-to/deploy-for-production/connect-to-ethstats-network-monitor.md)
  * [Deploy edeXa with Ansible](how-to/deploy-for-production/deploy-edexa-with-ansible.md)
  * [Deploy edeXa to the cloud](how-to/deploy-for-production/deploy-edexa-to-the-cloud.md)
  * [Deploy edeXa with Kubernetes](how-to/deploy-for-production/deploy-edexa-with-kubernetes.md)
* [Backup and restore edeXa](how-to/backup-and-restore-edexa.md)
* [Network and protocol upgrades](how-to/network-and-protocol-upgrades.md)
* [Concepts](how-to/concepts/README.md)
  * [Plugins](how-to/concepts/plugins.md)
  * [Public key infrastructure](how-to/concepts/public-key-infrastructure.md)
  * [Privacy](how-to/concepts/privacy/README.md)
    * [Multi-tenancy](how-to/concepts/privacy/multi-tenancy.md)
    * [Privacy plugin](how-to/concepts/privacy/privacy-plugin.md)
    * [Privacy groups](how-to/concepts/privacy/privacy-groups.md)
    * [Flexible privacy groups](how-to/concepts/privacy/flexible-privacy-groups.md)
    * [Private transactions](how-to/concepts/privacy/private-transactions/README.md)
      * [Private transaction processing](how-to/concepts/privacy/private-transactions/private-transaction-processing.md)
  * [Permissioning](how-to/concepts/permissioning/README.md)
    * [Permissioning plugin](how-to/concepts/permissioning/permissioning-plugin.md)
    * [Onchain permissioning](how-to/concepts/permissioning/onchain-permissioning.md)
  * [Proof of authority consensus](how-to/concepts/proof-of-authority-consensus.md)
* [Reference](how-to/reference/README.md)
  * [Accounts for testing](how-to/reference/accounts-for-testing.md)
  * [Plugin API interfaces](how-to/reference/plugin-api-interfaces.md)
  * [Private network API methods](how-to/reference/private-network-api-methods/README.md)
    * [Private network API objects](how-to/reference/private-network-api-methods/private-network-api-objects.md)
  * [edeXa COMMAND LINE](how-to/reference/edexa-command-line/README.md)
    * [Private network subcommands](how-to/reference/edexa-command-line/private-network-subcommands.md)
    * [Private network command line options](how-to/reference/edexa-command-line/private-network-command-line-options.md)

## Copy of Use Cases

* [configure](copy-of-use-cases/configure/README.md)
  * [Consensus protocols](copy-of-use-cases/configure/consensus-protocols/README.md)
    * [Configure QBFT consensus](copy-of-use-cases/configure/consensus-protocols/configure-qbft-consensus.md)
* [Configure free gas networks](copy-of-use-cases/configure-free-gas-networks.md)
* [TUTORIAL](copy-of-use-cases/tutorial/README.md)
  * [Deploy private network example on Azure](copy-of-use-cases/tutorial/deploy-private-network-example-on-azure.md)
  * [private network using Ethash](copy-of-use-cases/tutorial/private-network-using-ethash.md)
  * [private network using Clique](copy-of-use-cases/tutorial/private-network-using-clique.md)
  * [private network using QBFT](copy-of-use-cases/tutorial/private-network-using-qbft.md)
  * [Developer Quickstart](copy-of-use-cases/tutorial/developer-quickstart.md)
  * [private network using IBFT 2.0](copy-of-use-cases/tutorial/private-network-using-ibft-2.0/README.md)
    * [Add and remove IBFT 2.0 validators](copy-of-use-cases/tutorial/private-network-using-ibft-2.0/add-and-remove-ibft-2.0-validators.md)
  * [privacy-enabled network](copy-of-use-cases/tutorial/privacy-enabled-network/README.md)
    * [Use the multi-node example in the web3js-quorum client library](copy-of-use-cases/tutorial/privacy-enabled-network/use-the-multi-node-example-in-the-web3js-quorum-client-library.md)
    * [privacy-enabled network using the Quorum Developer Quickstart](copy-of-use-cases/tutorial/privacy-enabled-network/privacy-enabled-network-using-the-quorum-developer-quickstart.md)
    * [multi-tenant node](copy-of-use-cases/tutorial/privacy-enabled-network/multi-tenant-node.md)
  * [permissioned network](copy-of-use-cases/tutorial/permissioned-network/README.md)
    * [Upgrade permissioning contracts](copy-of-use-cases/tutorial/permissioned-network/upgrade-permissioning-contracts.md)
    * [Get started with onchain permissioning](copy-of-use-cases/tutorial/permissioned-network/get-started-with-onchain-permissioning.md)
  * [Deploy smart contracts to an Ethereum chain](copy-of-use-cases/tutorial/deploy-smart-contracts-to-an-ethereum-chain/README.md)
    * [transaction](copy-of-use-cases/tutorial/deploy-smart-contracts-to-an-ethereum-chain/transaction.md)
    * [Interact with deployed smart contracts](copy-of-use-cases/tutorial/deploy-smart-contracts-to-an-ethereum-chain/interact-with-deployed-smart-contracts.md)
  * [Deploy Besu using Kubernetes](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/README.md)
    * [Deploy for production](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/deploy-for-production.md)
    * [cluster](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/cluster.md)
    * [Deploy charts](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/deploy-charts.md)
    * [local environment](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/local-environment.md)
    * [Configure Kubernetes mode in NAT Manager](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/configure-kubernetes-mode-in-nat-manager.md)
    * [Maintenance](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/maintenance.md)
    * [Use the Quorum Explorer](copy-of-use-cases/tutorial/deploy-besu-using-kubernetes/use-the-quorum-explorer.md)

***

* [How to](how-to-1.md)
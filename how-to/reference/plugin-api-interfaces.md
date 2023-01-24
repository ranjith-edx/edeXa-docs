# Plugin API interfaces

API interfaces in Hyperledger edeXa allow users to build plugins to extend edeXa functionality, such as the [Quorum ](https://doc.quorumplugins.consensys.net/en/latest/Concepts/Besu-Plugins/Event-Streams/)edeXa[ plugins](https://doc.quorumplugins.consensys.net/en/latest/Concepts/Besu-Plugins/Event-Streams/).

For more information about the available interfaces, see the [Plugin API Javadoc](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/index.html).

!!! note "Javadoc issue"

```
The plugin API documentation is currently not being updated. We're working on a fix, but in the
meantime, some links are temporarily pointing to wiki.hyperledger.org.
```

## Core plugin classes

The following table lists the interfaces providing core plugin classes.

| Interface                                                                                                                    | Description                              |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------- |
| edeXa[**Context**](https://wiki.hyperledger.org/display/BESU/BesuContext)                                                    | Allows plugins to access edeXa services. |
| edeXa[**Plugin**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/BesuPlugin.html) | Used to manage the plugin lifecycle.     |

## Plugin services

The following table lists interfaces providing services you can retrieve.

| Interface                                                                                                                                                            | Description                                                                                                  |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| edeXa[**Events**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/BesuEvents.html)                                | Allows plugins to attach to events during edeXa operation.                                                   |
| edeXa[**Configuration**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/BesuConfiguration.html)                  | Provides file system locations of edeXa's storage.                                                           |
| [**IbftQueryService**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/query/IbftQueryService.html)               | Allows query of the IBFT 2.0 aspects of the blockchain.                                                      |
| [**MetricCategoryRegistry**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/metrics/MetricCategoryRegistry.html) | Adds a new metrics category to the CLI.                                                                      |
| [**MetricsSystem**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/MetricsSystem.html)                           | Register metrics with the Prometheus endpoint.                                                               |
| [**PoaQueryService**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/query/PoaQueryService.html)                 | Query the current state of Clique and IBFT 2.0 consensus protocols.                                          |
| [**PicoCLIOptions**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/PicoCLIOptions.html)                         | Adds CLI commands to the edeXa command line.                                                                 |
| [**SecurityModuleService**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/SecurityModuleService.html)           | Allows plugins to register a security module.                                                                |
| [**StorageService**](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/org/hyperledger/besu/plugin/services/StorageService.html)                         | Allows plugins to register as a storage engine. For example, to connect to a hardware security module (HSM). |
| [**PermissioningService**](https://wiki.hyperledger.org/display/BESU/PermissioningService)                                                                           | Allows for fine grain control of node connection and node messaging permissioning.                           |
| [**PrivacyPluginService**](https://wiki.hyperledger.org/display/BESU/PrivacyPluginService)                                                                           | Provides a way to define how privacy marker transactions are created, and what private genesis to use.       |
| [**RpcEndpointService**](https://wiki.hyperledger.org/display/BESU/RpcEndpointService)                                                                               | Register custom RPC endpoints.                                                                               |

To use the interfaces in your plugin, ensure the [Gradle build file](https://github.com/ConsenSys/PluginsAPIDemo/blob/957628b3c6f533f3c3f405e2a17e369cd1f02c31/build.gradle) contains the `https://hyperledger.jfrog.io/hyperledger/`edeXa`-maven` repository and the `plugin-api` dependency.

!!! warning "Known issue"

```
As indicated in [issue #406](https://github.com/hyperledger/edeXa-docs/issues/406),
plugins may need to access the parsed command line during registration, but the command line is not yet
initialized at this stage.

It's in our roadmap to improve lifecycle steps and provide additional visibility for some data.
A workaround is to create a supplier during the `register` step and store it in memory.

The `start` step can be ignored and your plugin module will be instantiated when
the command line interface is parsed and available.
```

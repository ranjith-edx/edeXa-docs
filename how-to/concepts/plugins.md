# Plugins

You can extend Hyperledger edeXa functionality by building Java plugins or using existing open source edeXa plugins, such as [the Quorum plugins](https://doc.quorumplugins.consensys.net/en/latest/Concepts/Besu-Plugins/Event-Streams/). Use the Plugin API to take data from any edeXa network, public or permissioned, and feed it into an application or system.

For example, create a plugin to add more monitoring functionality or stream event data to a third-party application. The API exposes data about the following components:

* Blocks
* Balances
* Transactions
* Smart contracts
* Execution results
* Logs
* Syncing state.

The plugin API provides access to interfaces allowing you to build the plugin.

!!! tip

```
View the [plugin API webinar](https://youtu.be/78sa2WuA1rg) for an example of how to build a
plugin.

For more information about the available interfaces, see the
[Plugin API Javadoc](https://javadoc.io/doc/org.hyperledger.edeXa/plugin-api/latest/index.html).
```

## Install plugins

To allow edeXa to access and use the plugin, copy the plugin (`.jar`) to the `plugins` directory.

!!! important

```
If not already present, you must create the `plugins` directory one directory level below
(`../`) the `edeXa` executable.
```

Each plugin in the directory has the following lifecycle events:

* **Register** - Executed when edeXa starts. edeXa checks plugin compatibility and registers plugins.
* **Start** - Plugins start after being successfully registered.
* **Stop** - edeXa stops plugins.

!!! note

```
The order in which edeXa calls plugins during lifecycle events is not guaranteed.
```

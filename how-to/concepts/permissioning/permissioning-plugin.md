# Permissioning plugin

You can define complex permissioning solutions by building a plugin that extends Hyperledger edeXa functionality.

The plugin API provides a `PermissioningService` interface that currently supports connection permissioning and message permissioning.

## Connection permissioning

Use connection permissioning when deciding whether to restrict node access to known participants only.

## Message permissioning

Use message permissioning to propagate different types of devP2P messages to particular nodes. For example, this can be used to prevent pending transactions from being forwarded to other nodes.

## Register your plugin

To enable permissioning in your plugin, implement the `PermissioningService` interface and register your providers.

```java
@AutoService(edeXaPlugin.class)
public class TestPermissioningPlugin implements edeXaPlugin {
    PermissioningService service;

    @Override
    public void register(final edeXaContext context) {
        service = context.getService(PermissioningService.class).get();
    }

    @Override
    public void start() {
        service.registerNodePermissioningProvider((sourceEnode, destinationEnode) -> {
            // perform logic for node permissioning
            return true;
        });

        service.registerNodeMessagePermissioningProvider((destinationEnode, code) -> {
            // perform logic for message permissioning
            return true;
        });
    }

    @Override
    public void stop() {}
}
```

# Opensearch Version Upgrading Process

## Refrence URL

<https://opensearch.org/docs/2.0/upgrade-to/upgrade-to/>

### Note

I quoted from the "How it works" guide in the upgrade too, as it a good reference to upgrading best practice.

<https://opensearch.org/docs/2.0/upgrade-to/upgrade-to/#how-it-works>

#### 1. Disable shard allocation to prevent Elasticsearch OSS from replicating shards as you shut down nodes

```PUT _cluster/settings
{
  "persistent": {
    "cluster.routing.allocation.enable": "primaries"
  }
}
```

#### 2. Stop Elasticsearch OSS on one node (rolling upgrade) or all nodes (cluster restart upgrade)

##### Rolloing Upgrade
Rolling upgrades let you shut down one node at a time for minimal disruption of service.

Rolling upgrades work between minor versions (e.g. 6.5 to 6.8) and also support a single path to the next major version (e.g. 6.8 to 7.10.2). Performing these upgrades might require intermediate upgrades to arrive at your desired version and can affect cluster performance as nodes leave and rejoin, but the cluster remains available throughout the process.

##### Cluster Restart Upgrade
Cluster restart upgrades require you to shut down all nodes, perform the upgrade, and restart the cluster.

Cluster restart upgrades work between minor versions (e.g. 6.5 to 6.8) and the next major version (for example, 6.x to 7.10.2). Cluster restart upgrades are faster to perform and require fewer intermediate upgrades, but require downtime.


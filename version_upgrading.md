# Opensearch Version Upgrading Process

## Refrence URL

<https://opensearch.org/docs/2.0/upgrade-to/upgrade-to/>

### Note

I quoted from the "How it works" guide in the upgrade too, as it a good reference to upgrading best practice.

<https://opensearch.org/docs/2.0/upgrade-to/upgrade-to/#how-it-works>

#### Disable shard allocation to prevent Elasticsearch OSS from replicating shards as you shut down nodes

```PUT _cluster/settings
{
  "persistent": {
    "cluster.routing.allocation.enable": "primaries"
  }
}```

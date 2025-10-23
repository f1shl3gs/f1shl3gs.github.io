---
title: "Getting Started"
weight: 1
---

{{% steps %}}

### Config 
Edit your config file, which works just an node_exporter, and the output metrics is just like the node_exporter with
out golang metrics.

```yaml {filename = config.yaml}
sources:
  selfstat:
    type: selfstat
  node:
    type: node

sinks:
  prom:
    type: prometheus_exporter
    inputs:
      - node
      - selfstat

```

### Start

```shell
vertex -c config.yaml
2025-10-13T00:05:19.794098Z  INFO vertex::launch: Start vertex allocator="system" threads=2 max_blocking_threads=256 configs=[File("dev.yaml", None)]
2025-10-13T00:05:19.796201Z  INFO framework::topology::running: Running healthchecks.
2025-10-13T00:05:19.796222Z  INFO framework::topology::running: Starting source. key=node
2025-10-13T00:05:19.796242Z  INFO framework::topology::running: Starting source. key=selfstat
2025-10-13T00:05:19.796271Z  INFO framework::topology::running: Starting sink. key=prom
2025-10-13T00:05:19.796264Z  INFO sink{id=prom type="prometheus_exporter"}: framework::topology::builder: health check passed
```

### Check
```shell
curl localhost:9100/metrics
```

#### Output
See, just like an node_exporter, and switching node_exporter to vertex will not take you long.

```text
# HELP node_arp_entries ARP entries by device
# TYPE node_arp_entries gauge
node_arp_entries{device="enp6s0"} 3
# HELP node_boot_time_seconds Node boot time, in unixtime.
# TYPE node_boot_time_seconds gauge
node_boot_time_seconds 1760272078
# HELP node_btrfs_allocation_ratio Data allocation ratio for a layout/data type
# TYPE node_btrfs_allocation_ratio gauge
node_btrfs_allocation_ratio{block_group_type="data",mode="single",uuid="744ae33b-2131-4cb3-83e8-36ab2e21f7e2"} 1
node_btrfs_allocation_ratio{block_group_type="data",mode="single",uuid="abdc1472-719c-491c-9962-6b2ff956bc2b"} 1
node_btrfs_allocation_ratio{block_group_type="metadata",mode="dup",uuid="744ae33b-2131-4cb3-83e8-36ab2e21f7e2"} 2
node_btrfs_allocation_ratio{block_group_type="metadata",mode="dup",uuid="abdc1472-719c-491c-9962-6b2ff956bc2b"} 2
node_btrfs_allocation_ratio{block_group_type="system",mode="dup",uuid="744ae33b-2131-4cb3-83e8-36ab2e21f7e2"} 2
node_btrfs_allocation_ratio{block_group_type="system",mode="dup",uuid="abdc1472-719c-491c-9962-6b2ff956bc2b"} 2
# HELP node_btrfs_commit_seconds_total Sum of the duration of all commits, in seconds
# TYPE node_btrfs_commit_seconds_total counter
node_btrfs_commit_seconds_total{uuid="744ae33b-2131-4cb3-83e8-36ab2e21f7e2"} 77
node_btrfs_commit_seconds_total{uuid="abdc1472-719c-491c-9962-6b2ff956bc2b"} 0
...
```

{{% /steps %}}

## Next
[_index.md](../_index.md)
Explore the following sections to getting everything done.

{{< cards >}}
  {{< card link="../configuration/extensions" title="Extensions" >}}
  {{< card link="../configuration/sources" title="Sources" >}}
  {{< card link="../configuration/transforms" title="Transforms" >}}
  {{< card link="../configuration/sinks" title="Sinks" >}}
{{< /cards >}}

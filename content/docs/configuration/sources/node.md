---
title: node
---

{{< badge metrics >}}&nbsp;

{{< callout type="info" >}}
Linux only
{{< /callout >}}

This component is a rewrite of [node_expoter](https://github.com/prometheus/node_exporter). 

### Example
```yaml
# The Node source generates metrics about the host system scraped
# from various sources. This is intended to be used when the collector is
# deployed as an agent, and replace `node_exporter`.

# procfs mountpoint.
#
# Optional
proc_path: /proc

# sysfs mountpoint.
#
# Optional
sys_path: /sys

# Duration between each scrape.
#
# Optional
interval: 15s
```

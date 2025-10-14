---
title: nvidia
---

{{< badge metrics >}}&nbsp;

{{< callout type="info" >}}
Linux only
{{< /callout >}}

Collect metrics of NVIDIA GPU, `nvidia_smi` is installed automatically
if NVIDIA GPU driver installed already.

### Example
```yaml
# The nvidia_smi's absolutely path.
#
# Optional
path: /usr/bin/nvidia-smi

# You can find out possible fields by running `nvidia-smi --help-query-gpu`
# 
# The value `%s` will automatically detect the fields to query
#
# Optional
query_fields: []

# Duration between each scrape.
#
# Optional
interval: 15s
```
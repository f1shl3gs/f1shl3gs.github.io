---
title: libvirt
---

{{< badge metrics >}}&nbsp;

This source connects to libvirt daemon and collect per-domain metrics related
to CPU, memory, disk and network usage.

### Example
```yaml
# The socket path of libvirtd, read permission is required.
#
# Optional
sock: /run/libvirt/libvirt-sock-ro

# Duration between each scrape.
#
# Optional
interval: 15s
```
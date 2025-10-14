---
title: ping
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
# Configuration of this source to do ICMP/PING request, and gather
# metrics.

targets: 
  - 127.0.0.1

# The interval between each metrics sending
#
# Optional
interval: 15s

# TTL to the UDP socket
#
# Optional
ttl: 64
```
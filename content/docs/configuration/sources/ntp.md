---
title: ntp
---

{{< badge metrics >}}&nbsp;

This source checks the drift of that node's clock against a given NTP server or servers.

### Example
```yaml
# SocketAddr which UdpSocket is going to bind.
#
# Optional
bind: 0.0.0.0:0

# NTP servers to use.
#
# Required
pools: 
- pool.ntp.org

# The NTP client query timeout
#
# Optional
timeout: 10s

# Duration between each scrape.
#
# Optional
interval: 15s
```
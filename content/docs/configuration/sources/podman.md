---
title: podman
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
# Address to reach the desired Podman daemon.
#
# Optional
endpoint: /run/podman/podman.sock

# API version of the Podman
#
# Optional
api_version: v3.2.0

# The maximum amount of time to wait for Podman API responses
#
# Optional
timeout: 5s

# The interval at which to gather container stats.
#
# Optional
interval: 15s
```

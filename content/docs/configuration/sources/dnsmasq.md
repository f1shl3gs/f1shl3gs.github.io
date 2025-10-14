---
title: dnsmasq
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
# Dnsmasq host:port addresses
#
# Optional
name_servers: []

# Path to the dnsmasq leases file, by default it is `/var/lib/misc/dnsmasq.leases`
#
# Optional
leases_path: /var/lib/misc/dnsmasq.leases

# Expose dnsmasq leases as metrics (high cardinality)
#
# Optional
expose_leases: false

interval: 15s

# Timeout for the TCP/UDP socket
#
# Optional
timeout: 2s
```

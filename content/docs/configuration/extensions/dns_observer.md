---
title: dns_observer
---

### Example
```yaml
# A list of DNS domain names to be queried
#
# Required
names: []

# The type of DNS query to perform.
#
# Optional
query_type: SRV

# The port number used if the query type is not SRV
#
# Optional
port: 1

# The time after which the provided names are refreshed
#
# Optional
interval: 30s
```
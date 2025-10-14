---
title: memcached
---

{{< badge metrics >}}&nbsp;

Collect metrics from memcached servers.

### Example
```yaml
# The endpoint to Memcached servers.
#
# Required
endpoints: 
- 127.0.0.1:3000

# Duration between each scrape.
#
# Optional
interval: 15s
```
---
title: chrony
---

{{< badge "Metrics" >}}&nbsp;

### Example
```yaml
# The [chrony] source is a pure rust implementation of the command
# `chronyc tracking` to allow for portability across systems and
# platforms. All of the data that would typically be captured by
# the tracking command is made available in this source.

# The Address on where to communicate to `chronyd`.
# 
# Make sure vertex has the right permission to access this address.
#
# Optional
address: 127.0.0.1:8080

# How frequent this source should poll.
#
# Optional
interval: 15s

# The total amount of time allowed to read and process the data from chronyd.
#
# Optional
timeout: 10s
```
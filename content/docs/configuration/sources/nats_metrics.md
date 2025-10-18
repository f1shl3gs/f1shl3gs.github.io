---
title: nats_metrics
---

Collect metrics from a list of NATS servers.

### Example
```yaml
# NATS's http server endpoints
#
# Required
endpoints: []

interval: 15s

# Metric groups to collect
#
# Optional
collectors: 
  varz: false

  connz: false

  accstatz: false

  healthz: false

  jsz: 
    accounts: false

    consumers: false

    streams: false

  leafz: false

  routez: false

  subsz: false

  gatewayz: false
```
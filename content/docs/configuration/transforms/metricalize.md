---
title: metricalize
---

{{< badge logs >}}&nbsp;
{{< badge metrics >}}&nbsp;

Processing log events and produce metrics.

### Example
```yaml
# The interval between flushes.
#
# Optional
interval: 15s

# A table of key/value pairs representing the keys to be added to the event.
# 
# Available values:
# counter:     Counter
# gauge:       Gauge
# histogram:   Histogram
#
# Optional
metrics: []
```
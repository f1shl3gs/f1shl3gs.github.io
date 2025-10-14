---
title: kubernetes_events
---

{{< badge logs >}}&nbsp;

{{< callout type="info" >}}
Kubernetes version >= 1.22 is required.
{{< /callout >}}

The Kubernetes events source collects events from the Kubernetes API server.
It collects all the new or updated events that come in.

### Example
```yaml
# Namespaces to watch for, if this field is empty, all namespaces will
# be watched.
#
# Optional
namespaces: []
```

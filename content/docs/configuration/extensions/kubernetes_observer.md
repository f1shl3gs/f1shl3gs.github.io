---
title: kubernetes_observer
---

### Example
```yaml
# Optional namespace discovery. If not provided, all namespaces are used.
#
# Optional
namespaces: []

# The Kubernetes role of entities that should be discovered
#
# Optional
resource: node

# Optional label and field selectors to limit the discovery process to a
# subset of available resources.
# 
# See https://kubernetes.io/docs/concepts/overview/working-with-objects/field-selectors/
# and https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/
# to learn more about the possible filters that can be used.
#
# Optional
label_selector: null

field_selector: null
```
---
title: filter
---

{{< badge logs >}}&nbsp;

Filters events based on a set of conditions.

### Example
```yaml
# The condition to be matched against every input event. Only messages that pass
# the condition are forwarded; messages that don’t pass are dropped.
#
# Required
condition: .meta.foo[0] contains bar
```

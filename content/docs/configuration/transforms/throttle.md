---
title: throttle
---

{{< badge logs >}}&nbsp;

Rate limits one or more log streams to limit load on downstream services, or to
enforce usage quotas on users.

```yaml
# The name of the log field whose value will be hashed to determine if the
# event should be rate limited.
# 
# If left unspecified, or if the event doesn't have "key_field", the
# event be will not rate limited separately.
#
# Optional
key_field: null

# The number of events allowed for a given bucket per configured window.
# Each unique key will have its own threshold.
#
# Optional
threshold: 1

# The time frame in which the configured "threshold" is applied.
#
# Optional
window: 1s
```
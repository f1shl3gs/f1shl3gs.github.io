---
title: cardinality
---

{{< badge metrics >}}&nbsp;

Rate limits one or more log streams to limit load on downstream services, or
to enforce usage quotas on users.

### Example
```yaml
# How many distinct values for any given key.
#
# Required
limit: 1

# The behavior of limit exceeded action.
#
# Optional
action: drop

mode: probabilistic

# The size of the cache for detecting duplicate tags, in bytes,
# 
# The larger the cache size, the less likely it is to have a false
# positive, or a case where we allow a new value for tag even after
# we have reached the configured limits.
#
# Optional
cache_size_per_tag: 4MiB
```
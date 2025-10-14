---
title: dedup
---

{{< badge logs >}}&nbsp;

De-duplicates events to reduce data volume by eliminating copies of data.

### Example
```yaml
# Options controlling how we cache recent Events for future duplicate checking.
#
# Optional
cache: 4096

# Options controlling what fields to match against.
#
# Optional
match_type: match

fields: []
```
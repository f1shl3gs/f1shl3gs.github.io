---
title: relabel
---

{{< badge metrics >}}&nbsp;

Enrich metrics, just like prometheus's relabel.



### Example
```yaml
operations:
  - set:
      key: foo
      value: bar
  # - add:
  #     key: foo
  #     value: bar
  # - delete:
  #     key: foo
  # - rename:
  #     key: foo
  #     new: bar
  # - lowercase:
  #     target: foo
  # - uppercase:
  #     target: foo
  # - hash_mod:
  #     source: foo
  #     target: foo_hashed
  #     modules: blah
  # - drop:
  #     regex: foo.*
  # - keep:
  #     regex: foo.*
```

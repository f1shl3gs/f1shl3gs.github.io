---
title: selfstat
---

{{< badge metrics >}}&nbsp;

Gathering variants metrics about vertex itself.

|            |  linux  |  macos  | windows |
|------------|:-------:|:-------:|:-------:|
| cpu        | &check; |         |         |
| memory     | &check; |         |         |
| fds        | &check; |         |         |
| network    | &check; |         |         |
| runtime    | &check; | &check; | &check; |
| jemalloc   | &check; |         |         |
| build info | &check; | &check; | &check; |


### Example
```yaml
# The path of `/proc`
#
# Optional
proc_path: /proc

# The interval between scrapes.
#
# Optional
interval: 15s
```
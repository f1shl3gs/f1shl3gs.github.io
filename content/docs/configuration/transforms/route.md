---
title: route
---

Route events to other components

### Example
```yaml
# A table of route identifiers to logical conditions representing the filter of the route.
# Each route can then be referenced as an input by other components with the name
# <transform_name>.<route_id>. If an event does not match any route, it will be sent to
# the <transform_name>._unmatched output. Note, _unmatched is a reserved output name and
# cannot be used as a route name. _default is also reserved for future use.
#
# Required
route: {}
```

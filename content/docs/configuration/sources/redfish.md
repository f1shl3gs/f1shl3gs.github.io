---
title: redfish
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
targets: 
- http://localhost:8000

# The authentication strategy for http request/response
#
# Optional
auth: 
  strategy: basic

  # The basic authentication username.
  #
  # Required
  user: ""

  # The basic authentication password.
  #
  # Required
  password: ""

# The interval between fetch config.
#
# Optional
interval: 15s

# Configure which resource metric to collect
#
# Optional
collector: 
  thermal: true

  power: true

  memory: true

  network: false

  simple_storage: true

  storage: true
```
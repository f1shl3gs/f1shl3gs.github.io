---
title: redis
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
# Redis addresses to request for.
#
# Required
endpoints: []

# Duration between each scrape.
#
# Optional
interval: 15s

# Authenticate the connection for Redis server, which is protected by
# `requirepass` option or ACL.
#
# Optional
auth:
  # Username to use for authentication
  #
  # Optional
  username: null

  # Password of the Redis instance to scrape
  #
  # Required
  password: ""

# The assigned name is displayed in the output of CLIENT LIST so that it
# is possible to identify the client that performed a given connection.
# 
# https://redis.io/docs/latest/commands/client-setname/
#
# Optional
client_name: null
```
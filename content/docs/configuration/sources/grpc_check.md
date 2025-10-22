---
title: grpc_check
---

{{< badge metrics >}}&nbsp;

GRPC check the grpc service and produce metrics, see [health checking](https://github.com/grpc/grpc/blob/master/doc/health-checking.md).

### Example
```yaml
# Endpoint for gRPC service.
#
# Required
targets: []

# The service name to query for health status.
#
# Required
service: grpc.health.v1.Health

# This sources collects metrics on an interval.
#
# Optional
interval: 15s

# Timeout for gRPC request, it's value should be less than `interval`.
#
# Optional
timeout: 5s
```

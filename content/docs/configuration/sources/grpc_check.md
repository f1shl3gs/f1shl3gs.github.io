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

### Output
```text
# HELP grpc_check_duration_seconds Duration of gRPC request
# TYPE grpc_check_duration_seconds gauge
grpc_check_duration_seconds{endpoint="http://127.0.0.1:10000",service="example"} 0.000757555
# HELP grpc_check_healthcheck_response HealthCheck response
# TYPE grpc_check_healthcheck_response gauge
grpc_check_healthcheck_response{endpoint="http://127.0.0.1:10000",service="example",serving_status="SERVING"} 1
# HELP grpc_check_status_code Response gRPC status code
# TYPE grpc_check_status_code gauge
grpc_check_status_code{endpoint="http://127.0.0.1:10000",service="example"} 0
```
---
title: Service Discovery
weight: 5
---

Service discovery (SD) is a mechanism by which the vertex can discover monitorable endpoints automatically.

### Predefined Mechanisms
- [consul](/docs/configuration/extensions/consul_observer)
- [dns](/docs/configuration/extensions/consul_observer)
- [exec](/docs/configuration/extensions/exec_observer)
- [http](/docs/configuration/extensions/http_observer)
- [kubernetes](/docs/configuration/extensions/kubernetes_observer)
- [port](/docs/configuration/extensions/port_observer)

All service discovery extension provide a list of `Endpoint`s, Endpoint looks like below: 
```yaml
# ID uniquely identifies this endpoint
id: "123456789",

# Type of the Endpoint, e.g. service, pod, container, etc
typ: "port",

# Target is an IP address or hostname of the endpoint.
# It can also be a hostname/ip:port pair.
target: "127.0.0.1:8080",

# Details contains additional context about the endpoint such as Pod's metadata.
details: 
  foo: bar
  properties:
    foo: bar
```

### Configuring Service Discovery

```yaml
extensions:
  ports: 
    type: port_observer
    names:
      - foo.redis.svc
sources:
  http_check:
    type: multiplier
    observer: ports
    templates:
      # rule field is an VTL script to filter endpoints out
      - rule: details.port == 9100
        config: 
          type: http_check
          targets:
            - http://${{ target }}

sinks:
  prom:
    type: prometheus_exporter
    inputs:
      - http_check
```

### Troubleshooting
TODO

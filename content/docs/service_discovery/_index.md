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
    interval: 3s
  tap:
    type: remote_tap

sources:
  http:
    type: multiplier
    observer: ports
    templates:
      - rule: details.port == 9100 # prometheus_exporter sink
        config:
          type: http_check
          targets:
            - http://${{ target }}
          interval: 1s

sinks:
  prom:
    type: prometheus_exporter
    inputs:
      - http
```

### Troubleshooting

curl or [visit](http://127.0.0.1:11000/observers) the endpoint configured in the [remote_tap](/docs/configuration/extensions/remote_tap) extension.

```console
curl http://127.0.0.1:11000/observers | jq .
```

you can get something like

```json
{
  "ports": [
    {
      "id": "tcp:127.0.0.1:33331@3577",
      "type": "port",
      "target": "127.0.0.1:33331",
      "details": {
        "cmdline": "/usr/bin/xxxx",
        "is_ipv6": false,
        "name": "xxxx",
        "pid": 3577,
        "port": 3333,
        "protocol": "tcp"
      }
    }
  ]
}
```

---
title: Secrets
weight: 3
---

The new secret store component allows a user to store secrets and reference those secrets
in their Vertex configuration file. These stores alleviate the need to have secrets directly
in the Vertex configuration files.

Use `SECRET[<store>.<key>]` to tell Vertex to retrieve those secrets. This placeholder is 
replaced by the secret retrieved from the relevant store.

## Example

This example start a source component to probe `127.0.0.1:9100` which is the `prom` sink's
endpoint. You can checkout the prometheus endpoint with `curl -u admin:qwerty http://localhost:9100/metrics`

```yaml
secrets:
  plain:
    type: unencrypted
    data:
      password: qwerty

sources:
  check:
    type: http_check
    targets:
      - http://127.0.0.1:9100 # the prometheus_exporter sink
    auth:
      strategy: basic
      user: admin
      password: qwerty

sinks:
  prom:
    type: prometheus_exporter
    inputs:
      - check
    auth:
      strategy: basic
      user: admin
      password: SECRET[plain.password]
```

## Components

{{< cards >}}
  {{< components path="content/docs/configuration/secrets" >}}
{{< /cards >}}
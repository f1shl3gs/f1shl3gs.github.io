---
title: Configuration
weight: 3
---

Vector is configured using one/more configuration files.

## Example

The following is an example of a node_exporter alternative configuration that collect
machine metrics and expose those metrics with prometheus_exporter sink.

{{< tabs >}}
  {{< tab name="config.yaml" >}}
    ```yaml
    sources:
      # collect machine metrics
      node:
        type: node
      # the metrics of Vertex itself, like CPU, RSS and open fds
      selfstat:
        type: selfstat
    
    transforms:
      relabel:
        type: relabel
        inputs:
          - node
          - selfstat
        operations:
          # add `host` tag with hostname value 
          - action: set
            key: host
            value: ${HOSTNAME}
    
    sinks:
      prom:
        # default listen to 9100
        type: prometheus_exporter
        inputs:
          - relabel
    ```
  {{< /tab >}}

  {{< tab name="config.json" >}}
    ```json
    {
      "sources": {
        "node": {
          "type": "node"
        },
        "selfstat": {
          "type": "selfstat"
        }
      },
      "transforms": {
        "relabel": {
          "type": "relabel",
          "inputs": [
            "node",
            "selfstat"
          ],
          "operations": [
            {
              "action": "set",
              "key": "host",
              "value": "${HOSTNAME}"
            }
          ]
        }
      },
      "sinks": {
        "prom": {
          "type": "prometheus_exporter",
          "inputs": [
            "relabel"
          ]
        }
      }
    }
    ```
  {{< /tab >}}
{{< /tabs >}}

### YAML
[multiple documents](https://yaml.org/spec/1.2.2/#22-structures) is supported.

```yaml
sources:
  selfstat:
    type: selfstat
---
sinks:
  prom:
    type: prometheus_exporter
    inputs:
      - selfstat
```

## Pages

{{< cards >}}
  {{< card link="global" title="Global" >}}
  {{< card link="environments" title="Environments" >}}
  {{< card link="sources" title="Sources" >}}
  {{< card link="transforms" title="Transforms" >}}
  {{< card link="sinks" title="Sinks" >}}
{{< /cards >}}

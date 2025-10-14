---
title: kafka_metrics
---

{{< badge metrics >}}&nbsp;

Collect Kafka metrics. For other metrics from Kafka, have a look at the 
[JMX exporter](https://github.com/prometheus/jmx_exporter).

{{< callout type="info" >}}
`Consume lag` metrics is not supported yet, and this feature not enabled by default
in [Kafka exporter](https://github.com/danielqsj/kafka_exporter).
{{< /callout >}}

### Example
```yaml
# A comma-separated list of host and port pairs that are the addresses of
# the Kafka brokers in a "bootstrap" Kafka cluster that a Kafka client
# connects to initially ot bootstrap itself.
#
# Required
bootstrap_servers: 
- 127.0.0.1:9092

# This sources collects metrics on an interval.
#
# Optional
interval: 15s

# Regex that determines which topics to collect.
#
# Optional
topic_filter: .*
```

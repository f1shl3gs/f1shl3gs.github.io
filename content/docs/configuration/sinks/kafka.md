---
title: kafka
---

{{< badge logs >}}&nbsp;

### Example
```yaml
# A comma-separated list of host and port pairs that are the addresses of
# the Kafka brokers in a "bootstrap" Kafka cluster that a Kafka client
# connects to initially ot bootstrap itself.
#
# Required
bootstrap_servers: 
- 127.0.0.1:9092

# The Kafka topic name to write events to
#
# Required
topic: ""

# The log field name or tags key to use for the topic key. If the field
# does not exist in the log or in tags, a blank value will be used. If
# unspecified, the key is not sent. Kafka uses a hash of the key to choose
# the partition or uses round-robin if the record has no key.
#
# Optional
key_field: .foo.bar

# Configures the encoding specific sink behavior.
#
# Optional
encoding: 
  codec: json

  # Whether to use pretty JSON formatting.
  #
  # Optional
  pretty: false

  # List of fields that will be included in the encoded event.
  #
  # Optional
  only_fields: []

  # List of fields that will be excluded from the encoded event.
  #
  # Optional
  except_fields: []

  # Format used for timestamp fields.
  #
  # Optional
  timestamp_format: unix

# Configures the sink batching behavior.
#
# Optional
batch: 
  # The maximum size of a batch that is processed by a sink.
  # 
  # This is based on the uncompressed size of the batched events, before they
  # are serialized/compressed
  #
  # Optional
  max_bytes: 1MiB

  # The maximum size of a batch before it is flushed.
  #
  # Optional
  max_events: 100

  # The maximum age of a batch before it is flushed.
  #
  # Optional
  timeout: 20ms

# The log field name to use for the Kafka headers. If omitted,
# no headers will be written.
#
# Optional
headers_field: .foo.bar
```
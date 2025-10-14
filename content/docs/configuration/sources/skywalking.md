---
title: skywalking
---

### Example
```yaml
# The endpoint of SkyWalking
#
# Optional
endpoint: ""

service: ""

service_instance: ""

compression: none

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
  max_bytes: 2MiB

  # The maximum size of a batch before it is flushed.
  #
  # Optional
  max_events: 50

  # The maximum age of a batch before it is flushed.
  #
  # Optional
  timeout: 1s
```
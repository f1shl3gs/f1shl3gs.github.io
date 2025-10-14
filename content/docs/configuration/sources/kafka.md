---
title: kafka
---

{{< badge logs >}}&nbsp;
{{< badge state >}}&nbsp;

Collecting logs from Apache Kafka topics. This component is based on a modified version 
of [rskafka](https://github.com/f1shl3gs/rskafka) which is an prue Rust, low-level and 
lightweight implementation.

### Example
```yaml
# A comma-separated list of host and port pairs that are the address
# of the Kafka brokers in a "bootstrap" Kafka cluster that a Kafka
# client connects to initially to bootstrap itself.
#
# Required
bootstrap_brokers: 
- 10.14.22.123:9092

# The Kafka topics names to read events from.
# 
# Regex is supported if the topic begins with `^`.
#
# Required
topics: []

# The consumer group name to be used to consume events from Kafka.
#
# Required
group: ""

# If offsets for consumer group do not exist, set them using this
# strategy.
#
# Optional
auto_offset_reset: Earliest

# The Kafka session timeout.
#
# Optional
session_timeout: 10s

# The frequency that the consumer offsets are committed(written) to
# offset storage.
#
# Optional
commit_interval: 5s

# Tell Kafka to wait until it has enough data to send before responding to the consumer.
#
# Optional
fetch_wait_max: {"nanos":200000000,"secs":0}

# The log field name to use for the Kafka message key.
#
# Optional
key_field: message_key

# The log field name to use for the Kafka topic.
#
# Optional
topic_key: topic

# The log field name to use for the Kafka partition name.
#
# Optional
partition_key: partition

# The log field name to use for the Kafka offset
#
# Optional
offset_key: offset

# The log field name to use for the Kafka headers.
#
# Optional
headers_key: headers

# Configuration for building a `Framer`.
#
# Optional
framing: bytes

# Configuration for building a `Deserializer`.
#
# Optional
decoding: 
  codec: json

  # Determines whether or not to replace invalid UTF-8 sequences instead of failing.
  # 
  # When true, invalid UTF-8 sequences are replaced with the [`U+FFFD REPLACEMENT CHARACTER`][U+FFFD].
  # 
  # [U+FFFD]: https://en.wikipedia.org/wiki/Specials_(Unicode_block)#Replacement_character
  #
  # Optional
  lossy: true
```
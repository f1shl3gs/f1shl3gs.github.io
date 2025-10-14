---
title: pulsar
---

{{< badge logs >}}&nbsp;

Collect observability events from Apache Pulsar topics.

### Example
```yaml
# The endpoint to which the Pulsar client should connect to.
#
# Optional
endpoint: pulsar://127.0.0.1:6650

# The Pulsar topic names to read events from
#
# Optional
topics: []

# The Pulsar consumer name.
#
# Optional
consumer_name: null

# The Pulsar subscription name.
#
# Optional
subscription_name: null

# The consumer's priority level
# 
# The broker follows descending priorities. For example, 0=max-priority, 1, 2...
# 
# In shared subscription type, the broker first dispatches messages to the max
# priority level consumers if they have permits. Otherwise, the broker considers
# next priority level consumers.
#
# Optional
priority_level: null

# Max count of messages in a batch
#
# Optional
batch_size: null

# Authentication configuration
#
# Optional
auth: 
  # Basic authentication name/username
  # 
  # This can be used either for basic authentication(username/password) or
  # JWT authentication. When used for JWT, the value should be `token`.
  #
  # Optional
  name: ""

  # Basic authentication password/token
  # 
  # This can be used either for basic authentication (username/password) or
  # JWT authentication. When used for JWT, the value should be the signed
  # JWT, in the compact representation.
  #
  # Optional
  token: ""

# Dead Letter Queue Policy configuration
#
# Optional
dead_letter_queue_policy: 
  # Maximum number of times that a message will be redelivered before being
  # sent to the dead letter queue.
  #
  # Optional
  max_redeliver: 1

  # Name of the dead letter topic where the failing messages will be sent
  #
  # Optional
  dead_letter_topic: ""

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

tls: 
  # File path containing a list of PEM encoded certificates
  #
  # Optional
  ca: ""

  # Enables certificate verification
  # 
  # Do not set theis to `false` unless you understand the risks of
  # not verifying the validity of certificates.
  #
  # Optional
  verify_certificate: true

  # Whether hostname verification is enabled when verify_certificate is false
  # 
  # Set to true if not specified
  #
  # Optional
  verify_hostname: true
```
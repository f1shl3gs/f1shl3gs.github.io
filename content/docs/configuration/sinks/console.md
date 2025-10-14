---
title: console
---

{{< badge metrics >}}&nbsp;
{{< badge logs >}}&nbsp;
{{< badge traces >}}&nbsp;

Print incoming events to stdout or stderr.

### Example
```yaml
# The standard stream to write to.
#
# Optional
stream: stdout # stdout | stderr

# Encoding configuration
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

# Configuration for building a `Framer`.
#
# Optional
framing: bytes

acknowledgements: false
```
---
title: generate
---

{{< badge logs >}}&nbsp;



### Example
```yaml
# How many logs to produce.
#
# Optional
count: 18446744073709551615

# The amount of time, to pause between each batch of output lines.
#
# Optional
interval: 1s

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

# The format of the randomly generated output.
#
# Optional
format: 
  type: shuffle

  # If `true`, each output line starts with an increasing sequence number,
  # beginning with 0.
  #
  # Optional
  sequence: false

  # The list of lines to output
  #
  # Optional
  lines: []
```

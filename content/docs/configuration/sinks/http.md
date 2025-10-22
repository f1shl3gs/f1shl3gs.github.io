---
title: http
---

{{< badge logs >}}&nbsp;

### Example
```yaml
# The full URI to make HTTP requests to.
#
# Required
endpoint: http://example.com/some/resource

method: OPTIONS

# Http auth
#
# Optional
auth:
  strategy: basic

  # The basic authentication username.
  #
  # Required
  user: ""

  # The basic authentication password.
  #
  # Required
  password: ""

# Configures the TLS options for incoming/outgoing connections.
#
# Optional
tls:
  # Absolute path to an additional CA certificate file, in DER or PEM
  # format(X.509), or an inline CA certificate in PEM format.
  #
  # Optional
  ca: null

  # Absolute path to a certificate file used to identify this connection,
  # in DER or PEM format (X.509) or PKCS#12, or an inline certificate in
  # PEM format. If this is set and is not a PKCS#12 archive, "key_file"
  # must also be set.
  #
  # Optional
  cert: null

  # Absolute path to a private key file used to identify this connection,
  # in DER or PEM format (PKCS#8), or an inline private key in PEM format.
  # If this is set, "crt_file" must also be set.
  #
  # Optional
  key: null

  # Pass phrase used to unlock the encrypted key file. This has no effect
  # unless "key" is set.
  #
  # Optional
  key_pass: null

  # Enables certificate verification.
  # If enabled, certificates must not be expired and must be issued by a trusted issuer.
  # This verification operates in a hierarchical manner, checking that the leaf certificate
  # (the certificate presented by the client/server) is not only valid, but that the issuer
  # of that certificate is also valid, and so on until the verification process reaches a
  # root certificate.
  # 
  # Relevant for both incoming and outgoing connections.
  # 
  # Do NOT set this to false unless you understand the risks of not verifying the
  # validity of certificates.
  #
  # Optional
  verify_certificate: true

  # Enables hostname verification. If enabled, the hostname used to connect to the remote
  # host must be present in the TLS certificate presented by the remote host, either as the
  # Common Name or as an entry in the Subject Alternative Name extension.
  # 
  # Only relevant for outgoing connections.
  # 
  # Do NOT set this to false unless you understand the risks of not verifying the remote hostname.
  #
  # Optional
  verify_hostname: true

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
  max_bytes: 9.5MiB

  # The maximum size of a batch before it is flushed.
  #
  # Optional
  max_events: null

  # The maximum age of a batch before it is flushed.
  #
  # Optional
  timeout: 1s

# Middleware settings for outbound requests.
# 
# Various settings can be configured, such as concurrency and rate limits, timeouts, etc.
#
# Optional
request:
  concurrency: none

  # The time a request can take before being aborted.
  # 
  # It is highly recommended that you do not lower this value below the service’s
  # internal timeout, as this could create orphaned requests, pile on retries, and
  # result in duplicate data downstream.
  #
  # Optional
  timeout: 1m

  # The time window used for the `rate_limit_num` option.
  #
  # Optional
  rate_limit_duration: 1s

  # The maximum number of requests allowed within the `rate_limit_duration` time window.
  #
  # Optional
  rate_limit_num: 18446744073709551615

  # The maximum number of retries to make for failed requests.
  # 
  # The default, for all intents and purposes, represents an infinite number of retries.
  #
  # Optional
  retry_attempts: 18446744073709551615

  # The maximum amount of time to wait between retries.
  #
  # Optional
  retry_max_duration: 1h

  # The amount of time to wait before attempting the first retry for a failed request.
  # 
  # After the first retry has failed, the fibonacci sequence will be used to select
  # future backoffs.
  #
  # Optional
  retry_initial_backoff: 1s

  # The defaults for these values were chosen after running several simulations
  # on a test service that had various responses to load. The values are the best
  # balances found between competing outcomes.
  #
  # Optional
  adaptive_concurrency:
    # This value maintained high concurrency without holding it too high under
    # adverse conditions.
    #
    # Required
    decrease_ratio: 1.0

    # This value achieved the best balance between quick response and stability
    #
    # Required
    ewma_alpha: 1.0

    # This value avoided changing concurrency too aggressively when there is
    # fluctuation in the RTT measurements.
    #
    # Required
    rtt_deviation_scale: 1.0

  # Headers that will be added to the request.
  #
  # Optional
  headers: {}

# Encoding configuration
#
# Required
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

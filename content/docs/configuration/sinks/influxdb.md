---
title: influxdb
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
# Send metrics to InfluxDB v2 with HTTP write API
# 
# See https://docs.influxdata.com/influxdb/v2/api/#operation/PostWrite

# The endpoint to send data to.
# 
# This should be a full HTTP URI, including the scheme, host, and port
#
# Optional
endpoint: http://localhost:8086

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
  max_bytes: null

  # The maximum size of a batch before it is flushed.
  #
  # Optional
  max_events: 4096

  # The maximum age of a batch before it is flushed.
  #
  # Optional
  timeout: 1s

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
    # Optional
    decrease_ratio: 1.0

    # This value achieved the best balance between quick response and stability
    #
    # Optional
    ewma_alpha: 1.0

    # This value avoided changing concurrency too aggressively when there is
    # fluctuation in the RTT measurements.
    #
    # Optional
    rtt_deviation_scale: 1.0

  # Headers that will be added to the request.
  #
  # Optional
  headers: {}

# The organization to write data to.
# 
# API Token cannot be used across organizations, so org do not need to be a `Template`.
#
# Required
org: ""

# The bucket to write to.
#
# Required
bucket: ""

# API token for write authorization.
#
# Required
token: ""
```
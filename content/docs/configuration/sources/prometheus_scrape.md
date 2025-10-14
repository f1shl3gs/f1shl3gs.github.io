---
title: prometheus_scrape
---

{{< badge metrics >}}&nbsp;

Collect metrics from prometheus clients.

### Example
```yaml
# Endpoints to scrape metrics from.
#
# Required
targets: 
- http://example.com/metrics

# Duration between each scrape.
#
# Optional
interval: 15s

# Controls how tag conflicts are handled if the scraped source has tags
# that Vertex would add. If true Vertex will not add the new tag if the
# scraped metric has the tag already. If false, Vertex will rename the
# conflicting tag by adding "exported_" to it. This matches Prometheus's
# "honor_labels" configuration.
#
# Optional
honor_labels: false

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

# The authentication strategy for http request/response
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

# Global jitterSeed seed is used to spread scrape workload across HA setup.
#
# Optional
jitter_seed: 0
```
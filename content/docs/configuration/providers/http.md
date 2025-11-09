---
title: http
---

Vertex will fetch configs periodically, and reload if the response content's hash value changed.

## Example
```yaml
# The URL to download config
#
# Required
endpoint: http://example.com/some/resource

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

# Configures an HTTP/HTTPS proxy for Vertex to use. By default, the globally
# configured proxy is used.
#
# Optional
proxy:
  enabled: true

  # The URL to proxy HTTP requests through.
  #
  # Optional
  http: null

  # The URL to proxy HTTPS requests through.
  #
  # Optional
  https: null

  # A list of hosts to avoid proxying. Allowed patterns here include:
  # 
  # Domain names:     "example.com" matches requests to example.com
  # Wildcard domains: ".example.com" matches requests to example.com and its
  # subdomains
  # IP address:        "127.0.0.1" matches requests to 127.0.0.1
  # CIDR blocks:       "192.168.0.0./16" matches requests to any IP addresses in this range.
  # Splat:             "*" matches all hosts
  #
  # Optional
  no_proxy: []

# HTTP headers to add to the request.
#
# Optional
headers: {}

# The interval between fetch config.
#
# Optional
interval: 1m
```
---
title: http
---

{{< badge logs >}}&nbsp;

Starting an HTTP server and parsing request body to events.

### Example
```yaml
# The socket address to listen for connections on
#
# Required
listen: 127.0.0.1:8080

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

# HTTP basic auth
#
# Optional
auth:
  # The basic authentication username.
  #
  # Required
  username: ""

  # The basic authentication password.
  #
  # Required
  password: ""

# A list of HTTP headers to include in the log record
#
# Optional
headers: []

# A list of URL query parameters to include in the log record
#
# Optional
query_parameters: []

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
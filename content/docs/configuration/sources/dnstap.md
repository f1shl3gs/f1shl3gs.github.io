---
title: dnstap
---

{{< badge logs >}}&nbsp;

Collect DNS logs from dnstap-compatible servers.

### Example
```yaml
# Maximum DNSTAP frame length that the source accepts.
# 
# If any frame is longer than this, it is discarded.
#
# Optional
max_frame_length: 131072

mode: tcp

address: 127.0.0.1:8080

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

# Configuration for keepalive probes in a TCP Stream
# 
# This config's properties map to TCP keepalive properties in Tokio:
# https://github.com/tokio-rs/tokio/blob/tokio-0.2.22/tokio/src/net/tcp/stream.rs#L516-L537
#
# Optional
keepalive: 
  # The time a connection needs to be idle before sending TCP
  # keepalive probes.
  #
  # Optional
  timeout: 1m

# The size of the receive buffer used for each connection.
#
# Optional
receive_buffer_bytes: null
```

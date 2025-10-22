---
title: syslog
---

{{< badge logs >}}&nbsp;

### Example

#### TCP
```yaml
# The maximum buffer size of incoming messages. Messages larger than
# this are truncated.
#
# Optional
max_length: 131072

# The key name added to each event representing the current host. This can
# be globally set via the global "host_key" option.
# 
# The host key of the log. This differs from `hostname`
#
# Optional
host_key: foo.bar

tcp:
  # The address to listen for connections on, or systemd#N to use the Nth
  # socket passed by systemd socket activation. If an address is used it
  # must include a port.
  #
  # Required
  listen: 127.0.0.1:8080

  # Configures the TCP keepalive behavior for the connection to the source.
  #
  # Optional
  keepalive:
    # The time a connection needs to be idle before sending TCP
    # keepalive probes.
    #
    # Optional
    timeout: 1m

  # Configures the TLS options for incoming connections.
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

  # Configures the recive buffer size using the "SO_RCVBUF" option on the socket.
  #
  # Optional
  receive_buffer_bytes: null

  # The max number of TCP connections that will be processed.
  #
  # Optional
  connection_limit: null
```

#### UDP
```yaml
# The maximum buffer size of incoming messages. Messages larger than
# this are truncated.
#
# Optional
max_length: 131072

# The key name added to each event representing the current host. This can
# be globally set via the global "host_key" option.
# 
# The host key of the log. This differs from `hostname`
#
# Optional
host_key: foo.bar

udp: 
  # The address to listen for connections on, or systemd#N to use the Nth
  # socket passed by systemd socket activation. If an address is used it
  # must include a port
  #
  # Required
  listen: 127.0.0.1:8080

  # Configures the recive buffer size using the "SO_RCVBUF" option on the socket.
  #
  # Optional
  receive_buffer_bytes: null
```

#### Unix
{{< callout >}}
Linux and MacOS only
{{< /callout >}}
```yaml
# The maximum buffer size of incoming messages. Messages larger than
# this are truncated.
#
# Optional
max_length: 131072

# The key name added to each event representing the current host. This can
# be globally set via the global "host_key" option.
# 
# The host key of the log. This differs from `hostname`
#
# Optional
host_key: foo.bar

unix: 
  # Unix socket file path.
  #
  # Required
  path: ""
```
---
title: jaeger
---

{{< badge traces >}}&nbsp;

{{< callout type="info" >}}
Jaeger is switching legacy APIs to [OpenTelemetry Protocol(OTLP)](https://github.com/open-telemetry/opentelemetry-proto/blob/main/docs/specification.md)
{{< /callout >}}

Jaeger components implement various [APIs](https://www.jaegertracing.io/docs/1.31/apis/) for saving 
or retrieving trace data.

### Compatibility

| APIs           | 1.x     | 2.x     |
|----------------|---------|---------|
| thrift_http    | &check; | &check; |
| thrift_compact | &check; | &check; |
| thrift_binary  | &check; | &check; |
| grpc           | &check; | &check; |

### Example
```yaml
# In some cases it is not feasible to deploy Jaeger Agent next to the application,
# for example, when the application code is running as AWS Lambda function.
# In these scenarios the Jaeger Clients can be configured to submit spans directly
# to the Collectors over HTTP/HTTPS.
# 
# See https://www.jaegertracing.io/docs/1.31/apis/#thrift-over-http-stable
#
# Optional
thrift_http:
  endpoint: 0.0.0.0:14268

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

# The Agent can only receive spans over UDP in Thrift format.
# 
# See https://www.jaegertracing.io/docs/1.31/apis/#thrift-over-udp-stable
#
# Optional
thrift_compact:
  listen: 0.0.0.0:6831

  max_packet_size: 65000

  socket_buffer_size: null

# Most Jaeger Clients use Thrift’s compact encoding, however some client libraries
# do not support it (notably, Node.js) and use Thrift’s binary encoding.
# 
# See https://www.jaegertracing.io/docs/1.31/apis/#thrift-over-udp-stable
#
# Optional
thrift_binary:
  listen: 0.0.0.0:6832

  max_packet_size: 65000

  socket_buffer_size: null

# In a typical Jaeger deployment, Agents receive spans from Clients and forward them to Collectors
# 
# See https://www.jaegertracing.io/docs/1.31/apis/#protobuf-via-grpc-stable
#
# Optional
grpc:
  listen: 0.0.0.0:14250
```

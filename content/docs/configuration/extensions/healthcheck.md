---
title: healthcheck
---

This extension start an HTTP/GRPC server to provide a probe endpoint, so others can 
check if Vertex is ready or not. 

## HTTP
The HTTP server provide two endpoints:
- `/healthy` for liveness, always return 200
- `/ready` for readiness, a reload might mark vertex not ready for a while (return 503) 

## GRPC
If `grpc` enabled, this component will start an [Health Checking](https://grpc.io/docs/guides/health-checking/) service.

{{< callout >}}
watch method is not implemented, this is ok for most use cases.
{{< /callout >}}

## Example
```yaml
# The HTTP service provide two endpoint
# 
# - `/healthy` for `liveness` check
# - `/ready` for `readiness` check
#
# Optional
http:
  # Which address the HTTP server listen to
  #
  # Optional
  listen: 0.0.0.0:13133

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

# The GRPC service expose `Check` and `Watch` to retrieve or watch the
# serving status of Vertex
#
# Optional
grpc:
  # Which address the GRPC server listen to
  #
  # Optional
  listen: 0.0.0.0:13132
```
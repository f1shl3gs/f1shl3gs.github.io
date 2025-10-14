---
title: consul_observer
---

Consul service discovery allows retrieving services from Catalog API

```yaml
id: 1234
target: 127.0.0.1:8080
details:
  node:
    addr: 127.0.0.1
    port: 8080
  service:
    address: 127.0.0.1
    port: 9090
    id: blah
    tags:
      - foo
      - bar
```

### Example
```yaml
# The Endpoint to access to the Consul API
#
# Optional
endpoint: http://example.com/some/resource

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

# Namespaces are only supported in Consul Enterprise
#
# Optional
namespace: null

# Admin partitions are only supported in Consul Enterprise.
#
# Optional
partition: null

datacenter: null

# A list of services for which targets are retrieved. If omitted, all
# services are watched.
#
# Optional
services: []

# A Consul Filter expression used to filter the catalog results
# See https://www.consul.io/api-docs/catalog#list-services to known
# more about the filter expressions that can be used
#
# Optional
filter: null

# Allow stale Consul results, which reduce load on Consul
# 
# See https://www.consul.io/api/features/consistency.html
#
# Optional
allow_stale: true

# The time after which the provided names are refreshed.
# On large setup it might be a good idea to increase this value because
# the catalog will change all the time.
#
# Optional
refresh_interval: 30s
```
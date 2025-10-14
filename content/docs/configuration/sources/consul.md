---
title: consul
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
# HTTP/HTTPS endpoint to Consul server.
#
# Required
endpoints: 
- http://localhost:8500

# Duration between each scrape.
#
# Optional
interval: 15s

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

health_summary: true

query_options: 
  # Namespace overrides the `default` namespace.
  # 
  # Note: Namespaces are available only in Consul Enterprise
  #
  # Optional
  namespace: ""

  # Providing a datacenter overwrites the DC provided
  # by the Config
  #
  # Optional
  datacenter: ""

  # AllowStale allows any Consul server (non-leader) to service
  # a read. This allows for lower latency and higher throughput
  #
  # Optional
  allow_stale: true

  # RequireConsistent forces the read to be fully consistent.
  # This is more expensive but prevents ever performing a stale
  # read.
  #
  # Optional
  require_consistent: false

  # UseCache requests that the agent cache results locally. See
  # https://www.consul.io/api/features/caching.html for more details on the
  # semantics.
  #
  # Optional
  use_cache: false

  # MaxAge limits how old a cached value will be returned if UseCache is true.
  # If there is a cached response that is older than the MaxAge, it is treated
  # as a cache miss and a new fetch invoked. If the fetch fails, the error is
  # returned. Clients that wish to allow for stale results on error can set
  # StaleIfError to a longer duration to change this behavior. It is ignored
  # if the endpoint supports background refresh caching. See
  # https://www.consul.io/api/features/caching.html for more details.
  #
  # Optional
  max_age: 1m

  # StaleIfError specifies how stale the client will accept a cached response
  # if the servers are unavailable to fetch a fresh one. Only makes sense when
  # UseCache is true and MaxAge is set to a lower, non-zero value. It is
  # ignored if the endpoint supports background refresh caching. See
  # https://www.consul.io/api/features/caching.html for more details.
  #
  # Optional
  stale_if_error: 1m

  # WaitIndex is used to enable a blocking query. Waits
  # until the timeout or the next index is reached
  #
  # Optional
  wait_index: 1

  # WaitHash is used by some endpoints instead of WaitIndex to perform blocking
  # on state based on a hash of the response rather than a monotonic index.
  # This is required when the state being blocked on is not stored in Raft, for
  # example agent-local proxy configuration.
  #
  # Optional
  wait_hash: ""

  # WaitTime is used to bound the duration of a wait.
  # Defaults to that of the Config, but can be overridden.
  #
  # Optional
  wait_time: 1m

  # Token is used to provide a per-request ACL token
  # which overrides the agent's default token.
  #
  # Optional
  token: ""

  # Near is used to provide a node name that will sort the results
  # in ascending order based on the estimated round trip time from
  # that node. Setting this to "_agent" will use the agent's node
  # for the sort.
  #
  # Optional
  near: ""

  # NodeMeta is used to filter results by nodes with the given
  # metadata key/value pairs. Currently, only one key/value pair can
  # be provided for filtering.
  #
  # Optional
  node_meta: {}

  # RelayFactor is used in keyring operations to cause responses to be
  # relayed back to the sender through N other random nodes. Must be
  # a value from 0 to 5 (inclusive).
  #
  # Optional
  relay_factor: 1

  # LocalOnly is used in keyring list operation to force the keyring
  # query to only hit local servers (no WAN traffic).
  #
  # Optional
  local_only: false

  # Connect filters prepared query execution to only include Connect-capable
  # services. This currently affects prepared query execution.
  #
  # Optional
  connect: false

  # Filter requests filtering data prior to it being returned. The string
  # is a go-bexpr compatible expression.
  #
  # Optional
  filter: ""
```
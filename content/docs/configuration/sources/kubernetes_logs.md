---
title: kubernetes_logs
---

{{< badge logs >}}&nbsp;
{{< badge state >}}&nbsp;

{{< callout type="info" >}}
Kubernetes version >= 1.22 is required.
{{< /callout >}}

Collects Pod logs from Kubernetes Nodes, automatically enriching data with
metadata via the Kubernetes API.

This source requires read access to the `/var/log/pods` directory. When running in a Kubernetes 
cluster, user should provided a `hostPath` volume for tracking state of logs.

### Providers
There are two provider `kubernetes` and `kubelet`, both of them can meet our requirement.

#### kubernetes
Connecting to kubernetes's API server and list-watch pods on this node.

```yaml
type: kubernetes

# The `name` of the Kubernetes `Node` that Vertex runs at.
# Required to filter the `Pod`s to only include the ones with the
# log files accessible locally.
#
# Optional
node_name: null

# Specifies the label selector to filter `Pod`s with, to be used in
# addition to the built-in `vertex.io/exclude` filter
# 
# See: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#label-selectors
#
# Optional
label_selector: null

# Specifies the field selector to filter `Pod`s with, to be used in
# addition to the built-in `Node` filter.
# 
# See: https://kubernetes.io/docs/concepts/overview/working-with-objects/field-selectors/#list-of-supported-fields
#
# Optional
field_selector: null
```

#### kubelet
Retrieving pod list from kubelet every `interval`. This variant do not need to connect to 
API server, so this could mitigate the API server heavy traffic issue for large cluster.

```yaml
type: kubelet

# HTTP endpoint of the Kubelet's API
#
# Optional
endpoint: http://${NODE_NAME}:10250

# The interval of between each scan
#
# Optional
interval: 10s
```

### Example
```yaml
provider: 
  type: kubernetes

  # The `name` of the Kubernetes `Node` that Vertex runs at.
  # Required to filter the `Pod`s to only include the ones with the
  # log files accessible locally.
  #
  # Optional
  node_name: null

  # Specifies the label selector to filter `Pod`s with, to be used in
  # addition to the built-in `vertex.io/exclude` filter
  # 
  # See: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#label-selectors
  #
  # Optional
  label_selector: null

  # Specifies the field selector to filter `Pod`s with, to be used in
  # addition to the built-in `Node` filter.
  # 
  # See: https://kubernetes.io/docs/concepts/overview/working-with-objects/field-selectors/#list-of-supported-fields
  #
  # Optional
  field_selector: null

# Configuration for how the events are enriched with Pod metadata.
#
# Optional
fields: 
  pod: 
    name: foo.bar

    namespace: foo.bar

    uid: foo.bar

    ip: foo.bar

    ips: foo.bar

    labels: foo.bar

    annotations: foo.bar

    node_name: foo.bar

  container: 
    name: foo.bar

    image: foo.bar

# Reads from the specified streams
#
# Optional
stream: all # all | stdout | stderr
```
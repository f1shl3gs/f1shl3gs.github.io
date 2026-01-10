---
title: host_observer
---

{{< callout type="info" >}}
Linux only
{{< /callout >}}

Scanning TCP/UDP + IPv4/IPv6 listening ports, and get the process information

### Endpoint
```yaml
id: tcp:0.0.0.0:9100@689935
typ: host
target: 0.0.0.0:9100
details: 
  cmdline: vertex
  is_ipv6: false
  name: vertex
  pid: 689935
  port: 9100
  protocol: tcp
```

### Example
```yaml
# Path to `/proc`
#
# Optional
proc_path: /proc

interval: 15s
```

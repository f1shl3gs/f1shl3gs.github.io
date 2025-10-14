---
title: Service Discovery
---

Service discovery (SD) is a mechanism by which the vertex can discover monitorable endpoints automatically.

### Predefined Mechanisms
- [consul](/docs/configuration/extensions/consul_observer)
- [dns](/docs/configuration/extensions/consul_observer)
- [exec](/docs/configuration/extensions/exec_observer)
- [http](/docs/configuration/extensions/http_observer)
- [kubernetes](/docs/configuration/extensions/kubernetes_observer)
- [port](/docs/configuration/extensions/port_observer)

### Configuring Service Discovery

```yaml
extensions:
  sd: 
    type: 
```
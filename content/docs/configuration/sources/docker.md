---
title: docker
---

{{< badge metrics >}}&nbsp;

### Example
```yaml
endpoint: /var/run/docker.sock

# A list of filters whose matching images are to be excluded.
#
# Optional
excluded_images: []

timeout: 5s

interval: 15s
```
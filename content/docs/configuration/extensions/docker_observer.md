---
title: docker_observer
---

### Example
```yaml
# The absolute path of docker socket
#
# Optional
path: /var/run/docker.sock

# A list of filters whose matching images are to be excluded. Supports literals and regex
#
# Optional
exclude_images: []

# Max amount of time to wait for a response form Docker API
#
# Optional
timeout: 5s
```
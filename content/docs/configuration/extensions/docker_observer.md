---
title: docker_observer
---

### Endpoint
```json
{
  "id": "986d789db95ceef440fbbef1070266c4ae27da8820a2d9b891d314b91fe91b86:80/tcp",
  "type": "docker",
  "target": "172.17.0.2:80",
  "details": {
    "command": "nginx -g daemon off;",
    "container_id": "986d789db95ceef440fbbef1070266c4ae27da8820a2d9b891d314b91fe91b86",
    "hostname": "986d789db95c",
    "image": "nginx",
    "labels": {
      "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
    },
    "name": "happy_swanson",
    "tag": "1.27.4",
    "transport": "tcp"
  }
}
```

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
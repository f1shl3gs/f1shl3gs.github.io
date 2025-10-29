---
title: directory
---

This store can read secrets that stored in files, like
- [Docker secrets](https://docs.docker.com/engine/swarm/secrets/)
- [Kubernets secrets](https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#provide-prod-test-creds)

## Example
```yaml
# Directory path to read secrets from
#
# Required
path: /path/to/secrets

# Remove trailing whitespace from file contents
#
# Optional
trim_end: false
```

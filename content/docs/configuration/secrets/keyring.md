---
title: keyring
---

{{< callout type="info" >}}
Linux only
{{< /callout >}}

The kernel keyring in the `user` scope is used to store the secrets

### Usage
Adding a secret key `token`
```console
keyctl add user token abcdefg @u
```

Then, you can access this in the config like
```yaml
secrets:
  keyring:
    type: keyring

sources:
  type: http_check
  targets:
    - http://127.0.0.1
  auth:
    strategy: bearer
    token: SECRET[keyring.key]
```

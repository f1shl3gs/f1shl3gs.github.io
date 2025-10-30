---
title: remote_tap
---

This extension runs as a Web server that loads the remote observers that are registered against it.
It allows users of the collectors to visualize data going through pipelines.

## Example
```yaml
# The address in which the web server will be listening to.
#
# Optional
listen: 0.0.0.0:11000

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
```

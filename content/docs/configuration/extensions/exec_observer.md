---
title: exec_observer
---

This is a simple but very useful extension, users can write their own script
or with any other language. The only requirement is the stdout must be an array
of `Endpoint`.

If the program exit status is not success, then this observer will log it to help
user to debug

### Example
```yaml
command: []

working_directory: null

interval: 10s
```
---
title: Environments
weight: 2
---

| Environment                 | Description                                                                                                                                |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| VERTEX_WORKER_THREADS       | How many threads the Tokio runtime will use                                                                                                |
| VERTEX_MAX_BLOCKING_THREADS | The limit for additional blocking threads spawned by the Runtime                                                                           |
| VERTEX_LOG                  | Log level filter, see [examples](https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#example-syntax) |

## Using environment in config

```yaml
sources:
  http_check:
    type: http_check
    targets:
      - http://${HOSTNAME}:80
```

Some feature of [Environment expansions](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Shell-Parameter-Expansion-1) is supported too.

### ${parameter:-word}
If parameter is unset or null, the word returned. Otherwise, the value of parameter
is returned.
```console
$ v=123
$ echo ${v-unset}
123
$ echo ${v:-unset-or-null}
123
$ unset v
$ echo ${v-unset}
unset
$ v=
$ echo ${v-unset}

$ echo ${v:-unset-or-null}
unset-or-null
```

### $\{parameter:?word\}
If parameter is unset or null, vertex throw an warning.

```console
$ var=
$ : ${var:?var is unset or null}
bash: var: var is unset or null
$ echo ${var?var is unset}

$ unset var
$ : ${var?var is unset}
bash: var: var is unset
$ : ${var:?var is unset or null}
bash: var: var is unset or null
$ var=123
$ echo ${var:?var is unset or null}
123
```

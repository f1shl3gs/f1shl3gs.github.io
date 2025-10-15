---
title: exec
---

{{< badge logs >}}&nbsp;

Collect output from a process running on the host.

## Scheduled
Running the command every `interval`, and captures the stdout and/or stderr. Vertex
will wait the command exit and run that command at next tick.

```yaml
# The command to be run, plus any arguments if needed.
#
# Required
command: []

# The directory in which to run the command.
#
# Optional
working_directory: null

environment: {}

# Whether the output from stderr should be included when generating events.
#
# Optional
stream: all # all | stderr | stdout

scheduled:
  # The interval, in seconds, between scheduled command runs.
  # 
  # If the command takes longer than `exec_interval_secs` to run, it will be killed.
  #
  # Required
  interval: 1m
```

## Streaming
Running the command and captures the stdout and/or stderr. Vertex 

```yaml
# The command to be run, plus any arguments if needed.
#
# Required
command: []

# The directory in which to run the command.
#
# Optional
working_directory: null

environment: {}

# Whether the output from stderr should be included when generating events.
#
# Optional
stream: all # all | stderr | stdout

streaming:
  # Whether the command should be rerun if the command exits.
  #
  # Optional
  restart: always # always | on_failure | never

  # The amount of time, in seconds, that Vertex will wait before rerunning a
  # streaming command that exited.
  #
  # Optional
  delay: 5s
```
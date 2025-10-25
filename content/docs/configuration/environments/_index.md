---
title: Environments
weight: 2
---

| Environment                 | Description                                                                                                                                |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| VERTEX_WORKER_THREADS       | How many threads the Tokio runtime will use                                                                                                |
| VERTEX_MAX_BLOCKING_THREADS | The limit for additional blocking threads spawned by the Runtime                                                                           |
| VERTEX_LOG                  | Log level filter, see [examples](https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#example-syntax) |

---
title: Monitoring
weight: 5
---

## Logs

Vertex provides simple, clear, informative and well-structured logs via the [internal_log](/docs/configuration/sources/internal_logs) sources.

## Metrics

Vertex provide a simple component named [selfstat](/docs/configuration/sources/selfstat), just like prometheus client's 
[process collector](https://github.com/prometheus/client_golang/blob/main/prometheus/process_collector.go),
it collect cpu, memory, fds and network metrics

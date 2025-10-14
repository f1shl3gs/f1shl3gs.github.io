---
title: Memory usage
---

### Less threads

Vertex will use any core it detects(cgroup is supported), for example, if you have a 256-cores machine, then vertex
will start at least 256 threads to handle async tasks. In your workload, you may waste 255 threads,
so limit the worker threads is necessary.

So set the `VERTEX_WORKER_THREADS` environment or pass the proper value to `-t` or `--threads`. 
```shell
VERTEX_WORKER_THREADS=2 vertex
```
or
```shell
vertex -t 2
```

### Allocators

By default, vertex uses the system's default allocator, which is good for most cases, but
maybe not yours. Then users have to compile and test it.

Supported allocators:
- jemalloc
- snmalloc
- mimalloc
- scudo

compiling with command below:
```shell
cargo build --release --features jemalloc
```

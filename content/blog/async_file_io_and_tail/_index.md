---
title: Async File IO & Tail
date: 2025-10-10
tags:
  - linux
  - async
  - io_uring
---

![Async IO](async_io.webp)

## Background

When talking about asynchronous IO, the first thing that comes to mind is epoll, but 
it cannot handle file IO; the second is AIO which can handle file IO but doesn't suit
for all IO operations.

Finally, `io_uring` released in 2019, it can not only handle network IO, but also file IO. 

## Why not io_uring

`io_uring` is perfect for our needs. but when you're trying to add it to your application,
you'll find
- The API is too low-level, users must have enough knowledge to use it correctly.
- Rust's io_uring library is not very mature, `tokio-uring` doesn't support multiple threads. Some 
async runtimes do support io_uring but for us, switching runtime is hard to do and there are
too much works to be done.
- And the most important thing is that there are a lot of servers running older linux kernel which
does not support `io_uring`.

## Solution

Now, think about what we need for [tail](/docs/configuration/sources/tail). 

`WAITING` for write operations, and `NOTIFY` the process, then `READ` it.

`READ` can be done via something like `std::fs::read`, but how about `WAITING` and `NOTIFY`. Yes,
`inotify` can do it and the best part is that the `fd` can be [registered](https://docs.rs/tokio/latest/tokio/io/unix/struct.AsyncFd.html) in the tokio runtime.
When files are written, tokio can notify the process, and then read the log one by one. 

For other platforms, we can implement the tail component, with `polling` which is dummy but fine.

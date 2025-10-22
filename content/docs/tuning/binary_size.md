---
title: Binary size
weight: 2
---

This page demonstrates how to minimize the size of vertex binary.

## Remove unused components

By default, vertex contains all components (if possible), but you might not need all
of them, so you can disable whatever you don't want.

{{% steps %}}

### Add your own feature
```toml {filename="Cargo.yaml"}
[features]
custom = [
    "sources-node",
    "sinks-prometheus_exporter"
]
```

### Build
```shell
cargo build --release --no-default-features --features custom
```

### Check size
```shell
ll target/release/vertex
```

{{% /steps %}}

## `Strip` Symbols from Binary
By default, on Linux and macOS, symbol information is included in the compiled `.elf` file.
This information is not needed to properly execute the binary.

You can strip the binary manually
```shell
strip /path/to/the/binary
```

Or, modify the `Cargo.toml`
```toml {filename="Cargo.yaml"}
[profile.release]
strip = true
```

## Reduce Parallel Code Generation units
Cargo will use as many as possible(<= 16) for code generating, This increase compile times
and more `inline` optimization.

Set this to `1` in `Cargo.toml` to allow for maximum size reduction optimization 
```toml {filename="Cargo.yaml"}
[profile.release]
codegen-units = 1
```

### Others
And there are many options to reduce the memory size, see [min-sized-rust](https://github.com/johnthagen/min-sized-rust).

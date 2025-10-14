---
title: pprof
---

{{< callout type="warning" >}}
Be aware that `pprof` will impact the performance 
{{< /callout >}}

{{< callout type="warning" >}}
`pprof` will not leak any memory, but it did bloat the memory, see [this](https://github.com/tikv/pprof-rs/issues/244).
{{< /callout >}}

Works just like Go`s pprof powered by [tikv/pprof-rs](https://github.com/tikv/pprof-rs).

You can profile the vertex by this command, and you'll get a [flamegraph](https://www.brendangregg.com/flamegraphs.html).
```shell
wget "http://127.0.0.1:8080/debug/pprof/profile?seconds=10&frequency=1000&flamegraph=true" -o profile.svg
```



## Example
```yaml
# Which address the pprof server will listen
#
# Required
listen: 127.0.0.1:8080
```

---
title: bind
---

{{< badge metrics >}}&nbsp;

{{< callout >}}
Make sure BIND was built with libxml2 support. You can check with
`named -V | grep libxml2`
{{< /callout >}}

Collect BIND (named/dns) v9+ service metrics.

Make sure your Bind's [statistics-channels](https://downloads.isc.org/isc/bind9/9.18.39/doc/arm/html/reference.html#namedconf-statement-statistics-channels) enabled.

### Example

```yaml
# Endpoint for the BIND statistics api
#
# Required
endpoints:
  - http://127.0.0.1:8053

# Duration between each scrape.
#
# Optional
interval: 15s
```

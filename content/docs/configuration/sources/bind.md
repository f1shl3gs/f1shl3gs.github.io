---
title: bind
---

{{< badge metrics >}}&nbsp;

Collect BIND (named/dns) v9+ service metrics.

### Example
```yaml
# Make sure BIND was built with libxml2 support. You can check with the following command:
# named -V | grep libxml2
# 
# Configure BIND to open a statistics channel. e.g.
# 
# statistics-channels {
# inet 127.0.0.1 port 8053 allow { 127.0.0.1; };
# };
# 
# BIND Version  Statistics Format       Example URL                     Release Date
# 9.6 - 9.8         XML v2              http://localhost:8053           2008-12-23 - 2014-09-29
# 9.9               XML v2              http://localhost:8053/xml/v2    2012-02-29
# 9.9+              XML v3              http://localhost:8053/xml/v3    2012-05-21
# 9.10+             JSON v1             http://localhost:8053/json/v1   2014-04-30

# Endpoint for the BIND statistics api
#
# Required
endpoint: http://127.0.0.1:8053

# Duration between each scrape.
#
# Optional
interval: 15s
```
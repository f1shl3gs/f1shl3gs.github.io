---
title: geoip
---

{{< badge logs >}}&nbsp;

Adding geo info to log event.

### Example
```yaml
# Path to the `MaxMind GeoIP2` or `GeoLite2` binary city database file. Other
# databases, such as the country database, are not supported.
# 
# GeoIP2: https://dev.maxmind.com/geoip/geoip2/downloadable
# GeoLite2: https://dev.maxmind.com/geoip/geoip2/geolite2/#Download_Access
#
# Required
database: ""

# The field to insert the resulting GeoIP data into.
#
# Optional
target: .geoip

# The field name that contains the IP address. This field should contain a
# valid IPv4 or IPv6 address.
#
# Required
source: .foo.bar

# valid locales are: “de”, "en", “es”, “fr”, “ja”, “pt-BR”, “ru”, and “zh-CN” .
# 
# https://dev.maxmind.com/geoip/docs/databases/city-and-country?lang=en
#
# Optional
locale: en
```

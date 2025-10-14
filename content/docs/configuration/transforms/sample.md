---
title: sample
---

{{< badge logs >}}&nbsp;

### Example
```yaml
# The rate at which events will be forwarded, expressed as 1/N. For
# example, "10" means 1 out of every 10 events will be forwarded and
# rest will be dropped
#
# Required
rate: 1

# The name of the log field whose value will be hased to determine
# if the event should be passed.
# 
# Consistently samples the same events. Actual rate of sampling may
# differ from the configured one if values in the field are not
# uniformly distributed. If left unspecified, or if the event doesn't
# have "key_field", events will be count rated.
#
# Optional
key_field: .foo.bar
```
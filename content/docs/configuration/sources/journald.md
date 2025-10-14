---
title: journald
---

{{< badge logs >}}&nbsp;

{{< callout type="info" >}}
Linux only
{{< /callout >}}

Journald read logs from `journalctl -o export -f -c cursor`, The format is simple enough to write a 
parser for it. Without Deserialize(vertex) or Serialize(journalctl) we should get a better performance. 
This source requires permissions to run `journalctl`.

### Example
```yaml
# Only include entries that appended to the journal after the entries have been read.
# 
# NOTE: works only if the `cursor` is not found
#
# Optional
since_now: false

# Only include entries that occurred after the current boot of the system.
#
# Optional
current_boot_only: true

# A list of unit names to monitor. If empty or not present, all units are accepted.
# Unit names lacking a `.` have `.service` appended to make them a valid service
# unit name.
#
# Optional
units: []

# The list of unit names to exclude from monitoring. Unit names lacking a "." will have
# ".service" appended to make them a valid service unit name.
#
# Optional
excludes: []

# The systemd journal is read in batches, and a checkpoint is set at the end of each batch.
# This option limits the size of the batch.
#
# Optional
batch_size: null

# The absolute path of the `journalctl` executable. If not set, a search is done for
# the journalctl path.
#
# Optional
journalctl_path: null

# The absolute path of the journal directory. If not set, `journalctl` uses the
# default system journal path.
#
# Optional
journal_directory: null
```
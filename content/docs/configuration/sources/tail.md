---
title: tail
---

{{< badge logs >}}&nbsp;

This source reads every matched file in the `include` pattern. And this can
have a history of tracked files and a state of offsets. This helps resume a
state if the service is restarted.

Vertex is able to track files correctly in the following strategies:
- CREATE: new active file with a unique name is created on rotation
- RENAME: rotated files are renamed (with some special prefix/suffix)
- COPY_TRUNCATE: not support

When dealing with file rotation, avoid harvesting symlinks

### Example
```yaml
# Array of file patterns to include. glob is supported. Watching rotated
# files is not necessary, and vertex can handle it properly.
#
# Optional
include: []

# Array of file patterns to exclude. glob is supported.
# 
# Takes precedence over the `include` option. Note: The `exclude` patterns are applied
# _after_ the attempt to glob everything in `include`. This means that all files are
# first matched by `include` and then filtered by the `exclude` patterns. This can be
# impactful if `include` contains directories with contents that are not accessible.
#
# Optional
exclude: []

# File position to use when reading a new file.
#
# Optional
read_from: beginning

# Config the behavior of scanner, which scans the filesystem periodically and
# return the files to tail
#
# Optional
scan: 
  # How often the component checks for new files
  #
  # Optional
  interval: 10s

  # If this is set, scanner ignores any files that were modified before the
  # specified timespan. This is very useful if you keep log files for a long
  # time.
  #
  # Optional
  ignore_older_than: null

# Multiline aggregation configuration. If not specified, multiline aggregation is disabled.
#
# Optional
multiline: null

# `Ordering` is very useful to prevent data loss when file rotated.
# 
# It groups the active and rotated files, and then sort them. With this setting,
# vertex can understand the rotate behavior better, and reading rotated and
# active files sequentially, rather than parallelly.
#
# Optional
ordering: 
  # Regular expression used for matching file path, then grouping and sorting.
  # 
  # NOTE: Should contain at least one named capture which might be used in sort config.
  #
  # Optional
  pattern: \/var\/log\/pods\/(?<namespace>\S+)_(?<pod>\S+)_(?<uid>\S+)\/(?<container>\S+)\/(?<seq>\S+).log

  # Named capture's value to build a unique key when grouping
  #
  # Optional
  group_by: []

  # The number of files to track
  #
  # Optional
  limit: null

  # Sort of the grouped paths, and make sure the latest one is the first
  #
  # Optional
  sort: 
    # Keys to sort the grouped results
    #
    # Optional
    by: []

    # Direction of grouped results
    #
    # Optional
    direction: Ascending

# Encoding of the file
#
# Optional
charset: null
```
---
title: audit

---

{{< badge logs >}}&nbsp;

{{< callout type="info" >}}
Linux only
{{< /callout >}}

{{< callout type="info" >}}
Privilege is required
{{< /callout >}}

`audit` collects messages from [audit](https://linux-audit.com/), and produce Logs.

## Output

```json
{
  "data": {
    "auid": "1000",
    "comm": "vertex-worker",
    "exe": "/home/f1shl3gs/Workspaces/rustrover/vertex/target/release/vertex",
    "nl-mcgrp": "1",
    "op": "connect",
    "pid": "408241",
    "res": "1",
    "ses": "3",
    "subj_category": "c0.c1023",
    "subj_domain": "unconfined_t",
    "subj_level": "s0-s0",
    "subj_role": "unconfined_r",
    "subj_user": "unconfined_u",
    "tty": "pts2",
    "uid": "0"
  },
  "raw_msg": "audit(1760305566.860:527): pid=408241 uid=0 auid=1000 tty=pts2 ses=3 subj=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 comm=\"vertex-worker\" exe=\"/home/f1shl3gs/Workspaces/rustrover/vertex/target/release/vertex\" nl-mcgrp=1 op=connect res=1",
  "record_type": "event_listener",
  "sequence": 527,
  "timestamp": "2025-10-12T21:46:06.860Z"
}
```

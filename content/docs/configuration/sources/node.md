---
title: node
---

{{< badge metrics >}}&nbsp;

{{< callout type="info" >}}
Linux only
{{< /callout >}}

This component is a rewrite of [node_expoter](https://github.com/prometheus/node_exporter). 

The Node source generates metrics about the host system scraped
from various sources. This is intended to be used when the collector is
deployed as an agent, and replace `node_exporter`.

### Example
```yaml
# procfs mountpoint.
#
# Optional
proc_path: /proc

# sysfs mountpoint.
#
# Optional
sys_path: /sys

# Duration between each scrape.
#
# Optional
interval: 15s

collectors:
  arp: true

  bcache:
    # Expose expensive priority stats
    #
    # Optional
    priority_stats: false

  bonding: true

  btrfs: true

  conntrack: true

  cpu:
    guest: true

    info: false

    flags_include: .*

    bugs_include: .*

  cpufreq: true

  diskstats:
    ignored: ^(z?ram|loop|fd|(h|s|v|xv)d[a-z]|nvme\d+n\d+p)\d+$

  dmi: true

  drm: false

  edac: true

  entropy: true

  fibrechannel: true

  filefd: true

  filesystem:
    mount_points_exclude: ^/(dev|proc|run/credentials/.+|sys|var/lib/docker/.+|var/lib/containers/storage/.+)($|/)

    fs_type_exclude: ^(autofs|binfmt_misc|bpf|cgroup2?|configfs|debugfs|devpts|devtmpfs|fusectl|hugetlbfs|iso9660|mqueue|nsfs|overlay|proc|procfs|pstore|rpc_pipefs|securityfs|selinuxfs|squashfs|sysfs|tracefs)$

  hwmon: true

  infiniband: true

  ipvs:
    labels: []

  loadavg: true

  mdadm: true

  memory: true

  netclass:
    ignores: ^$

  netdev:
    include: ""

  netstat:
    fields: ^(.*_(InErrors|InErrs)|Ip_Forwarding|Ip(6|Ext)_(InOctets|OutOctets)|Icmp6?_(InMsgs|OutMsgs)|TcpExt_(Listen.*|Syncookies.*|TCPSynRetrans|TCPTimeouts|TCPOFOQueue|TCPRcvQDrop)|Tcp_(ActiveOpens|InSegs|OutSegs|OutRsts|PassiveOpens|RetransSegs|CurrEstab)|Udp6?_(InDatagrams|OutDatagrams|NoPorts|RcvbufErrors|SndbufErrors))$

  nfs: true

  nfsd: true

  nvme: true

  os_release: true

  power_supply:
    ignored: ""

  pressure: true

  processes: false

  rapl: true

  schedstat: true

  selinux: true

  sockstat: true

  softnet: true

  softirqs: false

  stat: true

  tapestats: true

  tcpstat: true

  thermal_zone: true

  time: true

  timex: true

  udp_queues: true

  uname: true

  vmstat:
    fields: ^(oom_kill|pgpg|pswp|pg.*fault).*

  watchdog: true

  xfrm: false

  xfs: true

  zfs: true
```

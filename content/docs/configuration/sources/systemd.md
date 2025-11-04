---
title: systemd
---

{{< badge metrics >}}&nbsp;

{{< callout type="info" >}}
Linux only
{{< /callout >}}

## Example
The `include` and `exclude` works for the unit `name`, and the unit name does not contain
`.service`, so

| Regex Pattern     | Correctness |
|-------------------|-------------|
| bluetooth*        | &check;     |
| bluetooth.service | &cross;     |


```yaml
# Regex of systemd units to include. Units must both match include and not match
# exclude to be included.
#
# Optional
include: .+

# Regexp of systemd units to exclude. Units must both match include and not match
# exclude to be included.
#
# Optional
exclude: .+\.(device)

# This sources collects metrics on an interval.
#
# Optional
interval: 15s
```

## Output
This is a bluetooth only output example, you can include/exclude whatever you want. 

```text
# HELP systemd_boot_monotonic_seconds Systemd boot stage monotonic timestamps
# TYPE systemd_boot_monotonic_seconds gauge
systemd_boot_monotonic_seconds{stage="Finish"} 18.228201
systemd_boot_monotonic_seconds{stage="Firmware"} 17.734186
systemd_boot_monotonic_seconds{stage="GeneratorsFinish"} 7.527827
systemd_boot_monotonic_seconds{stage="GeneratorsStart"} 7.430708
systemd_boot_monotonic_seconds{stage="InitRD"} 1.086632
systemd_boot_monotonic_seconds{stage="InitRDGeneratorsFinish"} 1.254792
systemd_boot_monotonic_seconds{stage="InitRDGeneratorsStart"} 1.228409
systemd_boot_monotonic_seconds{stage="InitRDSecurityFinish"} 1.087073
systemd_boot_monotonic_seconds{stage="InitRDSecurityStart"} 1.087002
systemd_boot_monotonic_seconds{stage="InitRDUnitsLoadFinish"} 1.271197
systemd_boot_monotonic_seconds{stage="InitRDUnitsLoadStart"} 1.2548
systemd_boot_monotonic_seconds{stage="Kernel"} 0
systemd_boot_monotonic_seconds{stage="Loader"} 2.797489
systemd_boot_monotonic_seconds{stage="SecurityFinish"} 7.236555
systemd_boot_monotonic_seconds{stage="SecurityStart"} 7.131279
systemd_boot_monotonic_seconds{stage="UnitsLoadFinish"} 7.636663
systemd_boot_monotonic_seconds{stage="UnitsLoadStart"} 7.527831
systemd_boot_monotonic_seconds{stage="Userspace"} 7.131022
# HELP systemd_boot_time_seconds Systemd boot stage timestamps
# TYPE systemd_boot_time_seconds gauge
systemd_boot_time_seconds{stage="Finish"} 1762251809
systemd_boot_time_seconds{stage="Firmware"} 0
systemd_boot_time_seconds{stage="GeneratorsFinish"} 1762251798
systemd_boot_time_seconds{stage="GeneratorsStart"} 1762251798
systemd_boot_time_seconds{stage="InitRD"} 1762251791
systemd_boot_time_seconds{stage="InitRDGeneratorsFinish"} 1762251792
systemd_boot_time_seconds{stage="InitRDGeneratorsStart"} 1762251792
systemd_boot_time_seconds{stage="InitRDSecurityFinish"} 1762251791
systemd_boot_time_seconds{stage="InitRDSecurityStart"} 1762251791
systemd_boot_time_seconds{stage="InitRDUnitsLoadFinish"} 1762251792
systemd_boot_time_seconds{stage="InitRDUnitsLoadStart"} 1762251792
systemd_boot_time_seconds{stage="Kernel"} 1762251790
systemd_boot_time_seconds{stage="Loader"} 0
systemd_boot_time_seconds{stage="SecurityFinish"} 1762251798
systemd_boot_time_seconds{stage="SecurityStart"} 1762251797
systemd_boot_time_seconds{stage="UnitsLoadFinish"} 1762251798
systemd_boot_time_seconds{stage="UnitsLoadStart"} 1762251798
systemd_boot_time_seconds{stage="Userspace"} 1762251797
# HELP systemd_resolved_cache_hits_total Resolved Total Cache Hits
# TYPE systemd_resolved_cache_hits_total counter
systemd_resolved_cache_hits_total 18
# HELP systemd_resolved_cache_misses_total Resolved Total Cache Misses
# TYPE systemd_resolved_cache_misses_total counter
systemd_resolved_cache_misses_total 257
# HELP systemd_resolved_current_cache_size Resolved Current Cache Size
# TYPE systemd_resolved_current_cache_size gauge
systemd_resolved_current_cache_size 45580146714629
# HELP systemd_resolved_current_transactions Resolved Current Transactions
# TYPE systemd_resolved_current_transactions gauge
systemd_resolved_current_transactions 178047428612
# HELP systemd_resolved_dnssec_bogus_total Resolved Total number of DNSSEC Verdicts Boguss
# TYPE systemd_resolved_dnssec_bogus_total counter
systemd_resolved_dnssec_bogus_total 0
# HELP systemd_resolved_dnssec_indeterminate_total Resolved Total number of DNSSEC Verdicts Indeterminat
# TYPE systemd_resolved_dnssec_indeterminate_total counter
systemd_resolved_dnssec_indeterminate_total 0
# HELP systemd_resolved_dnssec_insecure_total Resolved Total number of DNSSEC Verdicts Insecure
# TYPE systemd_resolved_dnssec_insecure_total counter
systemd_resolved_dnssec_insecure_total 0
# HELP systemd_resolved_dnssec_secure_total Resolved Total number of DNSSEC Verdicts Secure
# TYPE systemd_resolved_dnssec_secure_total counter
systemd_resolved_dnssec_secure_total 11668517563934726
# HELP systemd_resolved_transactions_total Resolved Total Transactions
# TYPE systemd_resolved_transactions_total counter
systemd_resolved_transactions_total 0
# HELP systemd_service_ip_egress_bytes Service unit egress IP accounting in bytes.
# TYPE systemd_service_ip_egress_bytes counter
systemd_service_ip_egress_bytes{name="bluetooth.service"} 18446744073709552000
# HELP systemd_service_ip_egress_packets_total Service unit egress IP accounting in packets.
# TYPE systemd_service_ip_egress_packets_total counter
systemd_service_ip_egress_packets_total{name="bluetooth.service"} 18446744073709552000
# HELP systemd_service_ip_ingress_bytes Service unit ingress IP accounting in bytes.
# TYPE systemd_service_ip_ingress_bytes counter
systemd_service_ip_ingress_bytes{name="bluetooth.service"} 18446744073709552000
# HELP systemd_service_ip_ingress_packets_total Service unit ingress IP accounting in packets.
# TYPE systemd_service_ip_ingress_packets_total counter
systemd_service_ip_ingress_packets_total{name="bluetooth.service"} 18446744073709552000
# HELP systemd_service_restart_total Service unit count of Restart triggers
# TYPE systemd_service_restart_total counter
systemd_service_restart_total{name="bluetooth.service"} 0
# HELP systemd_unit_active_enter_time_seconds Last time the unit transitioned into the active state
# TYPE systemd_unit_active_enter_time_seconds gauge
systemd_unit_active_enter_time_seconds{name="bluetooth.service",type="service"} 1762251799.900922
systemd_unit_active_enter_time_seconds{name="bluetooth.target",type="target"} 1762251799.901186
# HELP systemd_unit_active_exit_time_seconds Last time the unit transitioned out of the active state
# TYPE systemd_unit_active_exit_time_seconds gauge
systemd_unit_active_exit_time_seconds{name="bluetooth.service",type="service"} 0
systemd_unit_active_exit_time_seconds{name="bluetooth.target",type="target"} 0
# HELP systemd_unit_inactive_enter_time_seconds Last time the unit transitioned into the inactive state
# TYPE systemd_unit_inactive_enter_time_seconds gauge
systemd_unit_inactive_enter_time_seconds{name="bluetooth.service",type="service"} 0
systemd_unit_inactive_enter_time_seconds{name="bluetooth.target",type="target"} 0
# HELP systemd_unit_inactive_exit_time_seconds Last time the unit transitioned out of the inactive state
# TYPE systemd_unit_inactive_exit_time_seconds gauge
systemd_unit_inactive_exit_time_seconds{name="bluetooth.service",type="service"} 1762251799.858016
systemd_unit_inactive_exit_time_seconds{name="bluetooth.target",type="target"} 1762251799.901186
# HELP systemd_unit_info Mostly-static metadata for all unit types
# TYPE systemd_unit_info gauge
systemd_unit_info{name="bluetooth.service",service_type="dbus",type="service"} 1
# HELP systemd_unit_start_time_seconds Start time of the unit since unix epoch in seconds.
# TYPE systemd_unit_start_time_seconds gauge
systemd_unit_start_time_seconds{name="bluetooth.service",type="service"} 1762251799.900922
# HELP systemd_unit_state Systemd unit
# TYPE systemd_unit_state gauge
systemd_unit_state{name="bluetooth.service",state="activating",type="service"} 0
systemd_unit_state{name="bluetooth.service",state="active",type="service"} 1
systemd_unit_state{name="bluetooth.service",state="deactivating",type="service"} 0
systemd_unit_state{name="bluetooth.service",state="failed",type="service"} 0
systemd_unit_state{name="bluetooth.service",state="inactive",type="service"} 0
systemd_unit_state{name="bluetooth.target",state="activating",type="target"} 0
systemd_unit_state{name="bluetooth.target",state="active",type="target"} 1
systemd_unit_state{name="bluetooth.target",state="deactivating",type="target"} 0
systemd_unit_state{name="bluetooth.target",state="failed",type="target"} 0
systemd_unit_state{name="bluetooth.target",state="inactive",type="target"} 0
# HELP systemd_unit_tasks_current Current number of tasks per Systemd unit
# TYPE systemd_unit_tasks_current gauge
systemd_unit_tasks_current{name="bluetooth.service"} 1
# HELP systemd_unit_tasks_max Maximum number of tasks per Systemd unit
# TYPE systemd_unit_tasks_max gauge
systemd_unit_tasks_max{name="bluetooth.service",type="service"} 76851
# HELP systemd_version A metric with a constant '1' value labeled by version and features
# TYPE systemd_version gauge
systemd_version{features="+PAM +AUDIT +SELINUX -APPARMOR +IMA +IPE +SMACK +SECCOMP -GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN -IPTC +KMOD +LIBCRYPTSETUP +LIBCRYPTSETUP_PLUGINS +LIBFDISK +PCRE2 +PWQUALITY +P11KIT +QRENCODE +TPM2 +BZIP2 +LZ4 +XZ +ZLIB +ZSTD +BPF_FRAMEWORK +BTF +XKBCOMMON +UTMP +SYSVINIT +LIBARCHIVE",version="257.10-1.fc42"} 1
# HELP systemd_watchdog_enabled systemd watchdog enabled
# TYPE systemd_watchdog_enabled gauge
systemd_watchdog_enabled 0
```
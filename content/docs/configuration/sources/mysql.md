---
title: mysql
---

{{< badge metrics >}}&nbsp;

Get MySQL server metrics

### Requirements

Enable plugins
```sql
INSTALL PLUGIN QUERY_RESPONSE_TIME_AUDIT SONAME 'query_response_time.so'
INSTALL PLUGIN QUERY_RESPONSE_TIME SONAME 'query_response_time.so'
INSTALL PLUGIN QUERY_RESPONSE_TIME_READ SONAME 'query_response_time.so'
INSTALL PLUGIN QUERY_RESPONSE_TIME_WRITE SONAME 'query_response_time.so'
SET GLOBAL query_response_time_stats = on
```

```sql
# optional but recommended
CREATE USER 'vertex'@'localhost' IDENTIFIED BY 'XXXXXXXX' WITH MAX_USER_CONNECTIONS 3;
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'vertex'@'localhost';
```

### Example
```yaml
# Endpoint to the MySQL/MariaDB instances
#
# Required
endpoints: []

# Authentication used for connecting to MySQL instance
#
# Required
auth:
  # Username used to connect to MySQL instance
  #
  # Optional
  user: root

  # Password used to connect to MySQL instance
  #
  # Optional
  password: null

# Duration between each scrape.
#
# Optional
interval: 15s

global:
  # Since 5.1, Collect from SHOW GLOBAL STATUS (Enabled by default)
  #
  # Optional
  status: true

  # Since 5.1, Collect from SHOW GLOBAL VARIABLES (Enabled by default)
  #
  # Optional
  variables: true

# Since 5.1, collect the current size of all registered binlog files
#
# Optional
binlog_size: false

# Since 5.7, Collect per user metrics from sys.x$user_summary.
# 
# See https://dev.mysql.com/doc/refman/5.7/en/sys-user-summary.html for details
#
# Optional
sys_user_summary: false

user:
  # Since 5.1, Collect data from mysql.user
  #
  # Optional
  privileges: false

engine:
  # Since 5.1, Collect from SHOW ENGINE INNODB STATUS
  #
  # Optional
  innodb: false

  # Since 5.6, Collect from SHOW ENGINE TOKUDB STATUS
  #
  # Optional
  tokudb: false

heartbeat:
  # Database from where to collect heartbeat data
  #
  # Optional
  database: heartbeat

  # Table from where to collect heartbeat data
  #
  # Optional
  table: heartbeat

  # Use UTC for timestamps of the current server
  #
  # Optional
  utc: false

info_schema:
  # Since 5.5, Collect InnoDB compressed tables metrics from information_schema.innodb_cmp.
  #
  # Optional
  innodb_cmp: true

  # Since 5.5, Collect InnoDB buffer pool compression metrics from information_schema.innodb_cmpmem.
  #
  # Optional
  innodb_cmpmem: true

  # Since 5.5, Collect metrics from information_schema.innodb_metrics
  #
  # Optional
  innodb_metrics: false

  # Since 5.7, Collect metrics from information_schema.innodb_sys_tablespaces
  #
  # Optional
  innodb_sys_tablespaces: false

  # Since 5.5, Collect query response time distribution if query_response_time_stats is ON.
  #
  # Optional
  query_response_time: true

  # Since 5.5, If running with userstat=1, set to true to collect client statistics
  #
  # Optional
  clientstats: false

  # Since 5.1, Collect auto_increment columns and max values from information_schema
  #
  # Optional
  auto_increment: false

  # Collect current thread state counts from the information_schema.processlist
  #
  # Optional
  process_list:
    # Minimum time a thread must be in each state to be counted
    #
    # Required
    min_time: 1

    # Enable collecting the number of processes by user
    #
    # Optional
    processes_by_user: true

    # Enable collecting the number of processes by host
    #
    # Optional
    processes_by_host: true

  # Since 5.6,  Collect metrics from information_schema.replica_host_status
  #
  # Optional
  replica_host: false

  # Since 5.6, Collect metrics from information_schema.ROCKSDB_PERF_CONTEXT
  #
  # Optional
  rocksdb_perf_context: false

  # Since 5.1, If running with userstat=1, set to true to collect schema statistics
  #
  # Optional
  schemastats: false

  # Since 5.1, Collect metrics from information_schema.tables
  #
  # Optional
  tables: []

  # Since 5.1, If running with userstat=1, set to true to collect table statistics
  #
  # Optional
  tablestats: false

  # Since 5.1, If running with userstat=1, set to true to collect user statistics
  #
  # Optional
  userstats: false

# Collecting metrics from `performance_schema` database, if the variable of
# `performance_schema` is `OFF` then collecting is skipped.
# 
# Since 5.6.6, this variable is default `ON`
#
# Optional
perf_schema:
  # Collect metrics from performance_schema.events_waits_summary_global_by_event_name
  #
  # Optional
  events_waits: false

  events_statements:
    # Limit the number of events statements digests by response time
    #
    # Optional
    limit: 250

    # Limit how old the 'last_seen' events statements can be
    #
    # Optional
    time_limit: 24h

    # Maximum length of the normalized statement text
    #
    # Optional
    digest_text_limit: 120

    # Additional schema name to exclude (always excludes mysql, performance_schema, information_schema)
    #
    # Required
    exclude_schemas: []

  # Since 5.7, Collect metrics of grand sums from performance_schema.events_statements_summary_by_digest
  #
  # Optional
  events_statements_sum: false

  # Since 5.6, Collect metrics from performance_schema.file_summary_by_event_name
  #
  # Optional
  file_events: false

  # Collect metrics from performance_schema.file_summary_by_instance
  #
  # Optional
  file_instances:
    # RegEx file_name filter for performance_schema.file_summary_by_instance
    #
    # Optional
    filter: '*'

    # Remove path prefix in performance_schema.file_summary_by_instance
    #
    # Optional
    remove_prefix: /var/lib/mysql/

  # Collect metrics from performance_schema.memory_summary_global_by_event_name
  #
  # Optional
  memory_events:
    # Remove instrument prefix in performance_schema.memory_summary_global_by_event_name
    #
    # Optional
    remove_prefix: memory/

  # Collect metrics from performance_schema.replication_group_members
  #
  # Optional
  replication_group_members: false

  # Collect metrics from performance_schema.replication_group_member_stats
  #
  # Optional
  replication_group_member_stats: false

  # Collect metrics from performance_schema.replication_applier_status_by_worker
  #
  # Optional
  replication_applier_status_by_worker: false

  # Collect metrics from performance_schema.table_io_waits_summary_by_index_usage
  #
  # Optional
  index_io_waits: false

  # Since 5.6, Collect metrics from performance_schema.table_io_waits_summary_by_table
  #
  # Optional
  table_io_waits: false

  # Collect metrics from performance_schema.table_io_waits_summary_by_table
  #
  # Optional
  table_lock_waits: false

slave:
  # Since 5.1, Collect from SHOW SLAVE STATUS (Enabled by default)
  #
  # Optional
  status: true

  # Since 5.1, Scrape information from 'SHOW SLAVE HOSTS'
  #
  # Optional
  hosts: false
```

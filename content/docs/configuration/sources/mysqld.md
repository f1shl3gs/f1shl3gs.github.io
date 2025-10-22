---
title: mysqld
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
# Endpoint to the MySQL/MariaDB instance
#
# Optional
endpoint: localhost:3306

# Since 5.1, Collect from SHOW GLOBAL STATUS (Enabled by default)
#
# Optional
global_status: true

# Since 5.1, Collect from SHOW GLOBAL VARIABLES (Enabled by default)
#
# Optional
global_variables: true

# Since 5.1, Collect from SHOW SLAVE STATUS (Enabled by default)
#
# Optional
slave_status: true

# Since 5.1, collect auto_increment columns and max values from information_schema.
#
# Optional
auto_increment_columns: false

# Since 5.1, collect the current size of all registered binlog files
#
# Optional
binlog_size: false

info_schema:
  # Since 5.5, Collect InnoDB compressed tables metrics from information_schema.innodb_cmp.
  #
  # Optional
  innodb_cmp: true

  # Since 5.5, Collect InnoDB buffer pool compression metrics from information_schema.innodb_cmpmem.
  #
  # Optional
  innodb_cmpmem: true

  # Since 5.5, Collect query response time distribution if query_response_time_stats is ON.
  #
  # Optional
  query_response_time: true

# Username used to connect to MySQL instance
#
# Optional
username: null

# Password used to connect to MySQL instance
#
# Optional
password: null

# Duration between each scrape.
#
# Optional
interval: 15s
```
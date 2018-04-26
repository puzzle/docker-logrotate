# Usage

This is a logrotate container for use as a sidecar container.

Mount your volumes into the container and your `logrotate.conf` at `/opt/etc/logrotate.conf` and you're good to go!

Example logrotate.conf:

```
# see "man logrotate" for details
# rotate log files daily
daily

# keep 60 days worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# use date as a suffix of the rotated file
dateext

# uncomment this if you want your log files compressed
compress

# your log file, mounted into the container
/opt/logs/*.log {}
```

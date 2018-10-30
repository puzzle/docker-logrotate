# Usage

This is a logrotate container for use as a sidecar container.

Mount your volumes and logrotate configuration into the container and you're good to go!

# Configuration

## state file location

The logrotate state file should live on a persistent volume so logs are still correctly rotated in case the container is restarted.

Set the environment variable `STATE_FILE` to change the state file path. Defaults to `/opt/logs/logrotate.status`.

## logrotate.conf

Mount your `logrotate.conf` at `/opt/etc/logrotate.conf`.

Example logrotate.conf (remember to adjust `STATE_FILE` accordingly if you choose to mount the logs otherwhere than to `/opt/logs`):

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

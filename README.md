# check_php-fpm
`check_php-fpm` php-fpm (PHP FastCGI Process Mananger) plugin for Nagios / Icinga. Returns health and performance data.

## Dependencies
* php 5.6+
* `cgi-fcgi` console utility
* php-fpm status page enabled

## Installation
1. Copy the script to /usr/local/bin/
1. Use chown and chmod to ensure the test user can execute it.
1. Install fcgi dependency (RHEL: `sudo yum install fcgi` Debian: `sudo apt install libfcgi-bin`)
1. Enable php-fpm status page: `/etc/php-fpm.d/status.conf` or `/etc/php/7.4/fpm/pool.d/www.conf`:
```
[www]
pm.status_path = /status
```

## Usage
```
Usage: check_php-fpm [--connect <address:port>]	(defaults to 127.0.0.1:9000)
```

### Example output
```
OK: served 12 connections with 0 slow requests since Fri, 11 Oct 2019 16:07:36 +1100. | start_time=1570770456; start_since=1526; accepted_conn=12; listen_queue=0; max_listen_queue=0; listen_queue_len=128; idle_processes=5; active_processes=1; total_processes=6; max_active_processes=1; max_children_reached=0; slow_requests=0; queue_capacity=0%; process_capacity=16.666666666667%; 
```

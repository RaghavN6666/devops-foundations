# Bash System Health Checker

## Overview

A Bash automation script that monitors the health of a Linux system by collecting key system metrics and checking essential services.

## Features

- CPU Usage
- Memory Usage
- Disk Usage
- System Uptime
- Hostname
- Internet Connectivity
- Service Status Monitoring

## Technologies

- Bash
- awk
- grep
- systemctl
- ping

## Usage

```bash
chmod +x health_check.sh
./health_check.sh
```

## Sample Output

```
HOSTNAME: ubuntu

CPU Usage: 15%

Memory Usage: 3.2Gi / 16Gi (20%)

Disk Usage: 45%

UPTIME: up 2 days, 5 hours

INTERNET CONNECTION: CONNECTED

nginx: Running

docker: Running

ssh: Running
```

## Future Improvements

- Colored terminal output
- Logging to a file
- Email notifications
- Threshold-based warnings
- Cron scheduling
- Docker container support
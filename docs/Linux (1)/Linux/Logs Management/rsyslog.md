# rsyslog

[rsyslog documentation](https://www.rsyslog.com/doc/index.html)

`rsyslog` is a logging daemon that collects, filters, and stores log messages from the system and applications.

### Service name

`rsyslog.service`

## Install rsyslog

```bash
sudo apt install rsyslog
```

```bash
sudo yum install rsyslog
```

### Configuration files

- Main config file: `/etc/rsyslog.conf`
- Additional configs (modular): `/etc/rsyslog.d/*.conf`

### Log files

Default log files go to `/var/log/`, like:

- `/var/log/syslog` (general system logs)
- `/var/log/auth.log` (authentication)
- `/var/log/kern.log` (kernel)
- `/var/log/messages` (general messages)

### Sources of logs for rsyslog

| Source Type | How It Works | Example Use Case |
| --- | --- | --- |
| **Kernel** | Reads system boot & kernel logs | Boot messages, kernel panic |
| **Local apps** | Apps send logs to `/dev/log` | Apache, SSH, cron |
| **Systemd** | Reads from `journald` | Modern Linux distros |
| **Files** | Watches log files (`imfile`) | Custom app logs |
| **Remote** | Listens on UDP/TCP (`imudp/imtcp`) | Logs from other servers |
| **Pipes** | Reads from named pipes (FIFO) | App writes to a pipe |
| **Scripts** | Reads output from scripts | Monitoring scripts |
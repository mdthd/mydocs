# systemd-journald (journalctl)

`systemd-journald` is a daemon that collects and stores log data

It collects logs from:

1.  Kernel
2.  system services managed by systemd
3.  Applications
4.  Legacy syslog messages

---

## Checking journald service

### status check

```bash
systemctl status systemd-journald.service
```

### Check config

```bash
systemd-analyze cat-config systemd/journald.conf
```

### Config values

| **Parameter** | **Accepted Values** | **Meaning** |
| --- | --- | --- |
| `Storage` | `volatile`, `persistent`, `auto`, `none` | `volatile`: logs in RAM; `persistent`: logs on disk; `auto`: disk if available, else RAM; `none`: disables journal logging |
| `Compress` | `yes`, `no` | Enables/disables compression of journal files |
| `Seal` | `yes`, `no` | Enables cryptographic sealing for tamper detection |
| `SplitMode` | `uid`, `none` | `uid`: separate journals per user; `none`: single journal for all |
| `SyncIntervalSec` | Time (e.g. `5m`, `30s`) | Interval to sync journal data to disk |
| `RateLimitIntervalSec` | Time | Time window for rate limiting (e.g. `30s`) |
| `RateLimitBurst` | Integer | Max messages allowed in interval before throttling |
| `SystemMaxUse` / `RuntimeMaxUse` | Size (e.g. `500M`, `2G`) | Max disk/RAM usage for journal files |
| `SystemKeepFree` / `RuntimeKeepFree` | Size | Minimum free space to leave on disk/RAM |
| `SystemMaxFileSize` / `RuntimeMaxFileSize` | Size | Max size of individual journal files |
| `SystemMaxFiles` / `RuntimeMaxFiles` | Integer | Max number of journal files to retain |
| `MaxRetentionSec` | Time | Max age of journal entries before deletion |
| `ForwardToSyslog` | `yes`, `no` | Forwards logs to syslog daemon |
| `ForwardToKMsg` | `yes`, `no` | Forwards logs to `/dev/kmsg` (kernel log) |
| `ForwardToConsole` | `yes`, `no` | Forwards logs to system console |
| `ForwardToWall` | `yes`, `no` | Sends logs to all logged-in users via `wall` |
| `TTYPath` | Path (e.g. `/dev/tty10`) | Console device for `ForwardToConsole` |
| `MaxLevelStore` | `emerg`, `alert`, `crit`, `err`, `warning`, `notice`, `info`, `debug` | Max priority level stored in journal |
| `MaxLevelSyslog` | Same as above | Max priority forwarded to syslog |
| `MaxLevelKMsg` | Same as above | Max priority forwarded to kernel log |
| `MaxLevelConsole` | Same as above | Max priority shown on console |
| `MaxLevelWall` | Same as above | Max priority sent via `wall` |

---

## Using `journalctl` command

### 1\. Simple use

```bash
journalctl
```

### Options

| **Flag** | **Function** | **Example** |
| --- | --- | --- |
| `-b` | Logs from current boot | `journalctl -b` |
| `-f` | Follow logs live (like `tail -f`) | `journalctl -f` |
| `-n N` | Show last N lines | `journalctl -n 100` |
| `--no-pager` | Disable paging (good for scripts) | `journalctl --no-pager` |
| `-p LEVEL` | Filter by priority level | `journalctl -p err` |
| `-u UNIT` | Logs for a systemd unit | `journalctl -u nginx` |
| `--since TIME` | Start time filter | `journalctl --since "1 hour ago"` |
| `--until TIME` | End time filter | `journalctl --until "2025-09-19 15:00"` |
| `-k` | Show kernel logs | `journalctl -k` |

`-p LEVEL` priority levels

:::info
`-p` will accept value and level both  
`-p 3` is same as `-p err`
:::

| Value | Level | Meaning |
| --- | --- | --- |
| 0   | `emerg` | System is unusable |
| 1   | `alert` | Immediate action needed |
| 2   | `crit` | Critical conditions |
| 3   | `err` | Error conditions |
| 4   | `warning` | Warning messages |
| 5   | `notice` | Normal but significant |
| 6   | `info` | Informational |
| 7   | `debug` | Debug-level messages |

### using `-b` option

#### To print current boot logs

```bash
journalctl -b
```

```bash
journalctl -b 0
```

#### To print previous boot logs

```bash
journalctl -b 1
```

#### Check available logs of previous boot

```bash
journalctl --list-boots
```

### `--since` usage

### 🕰️ Absolute Time Formats

| **Format** | **Example** | **Meaning** |
| --- | --- | --- |
| Date only | `"2025-09-19"` | Midnight on Sept 19, 2025 |
| Date + time | `"2025-09-19 14:30"` | 2:30 PM on Sept 19, 2025 |
| Time only | `"14:30"` | 2:30 PM today |
| ISO 8601 | `"2025-09-19T14:30:00"` | Precise timestamp |
| RFC 2822 | `"Fri, 19 Sep 2025 14:30:00 +0530"` | Email-style timestamp |

### ⏳ Relative Time Formats

| **Format** | **Example** | **Meaning** |
| --- | --- | --- |
| Hours ago | `"2 hours ago"` | Two hours before now |
| Minutes ago | `"30 minutes ago"` | Half an hour ago |
| Days ago | `"3 days ago"` | Three days before now |
| Weeks ago | `"1 week ago"` | Seven days ago |
| Months ago | `"2 months ago"` | Two months ago |
| Years ago | `"1 year ago"` | One year ago |

### 📅 Named Time Keywords

| **Keyword** | **Meaning** |
| --- | --- |
| `"today"` | Midnight today |
| `"yesterday"` | Midnight yesterday |
| `"now"` | Current time |
| `"tomorrow"` | Midnight tomorrow (rarely used) |
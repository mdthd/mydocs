# Logs Management

## Logs

**Logs** are records of events on system

These records or stored in files (text files or binary files)

Logs files are available at `/var/log`

### Types of Logs

| **Source** | **Log Type** | **Examples** | **Purpose** |
| --- | --- | --- | --- |
| **Kernel** | Kernel logs | `/var/log/kern.log`, `dmesg` | Boot messages, hardware events |
| **System Services** | System logs | `/var/log/syslog`, `/var/log/messages` | General system activity |
| **Authentication** | Security logs | `/var/log/auth.log`, `/var/log/secure` | Login attempts, sudo, SSH |
| **Systemd (init system)** | Journal logs | `journalctl` | Unified logs for all services |
| **Applications** | Application-specific logs | `/var/log/apache2/`, `/var/log/mysql/` | Web server, database, etc. |
| **Package Managers** | Installation logs | `/var/log/apt/`, `/var/log/yum.log` | Software install/update history |
| **Cron (scheduler)** | Scheduled task logs | `/var/log/cron`, `/var/log/syslog` | Cron job execution |
| **Mail System** | Mail logs | `/var/log/mail.log`, `/var/log/maillog` | Email delivery and errors |
| **Firewall/Network** | Network logs | `/var/log/ufw.log`, `/var/log/firewalld` | Connection attempts, blocked traffic |
| **Hardware Drivers** | Driver logs | `dmesg`, `/var/log/kern.log` | Device initialization and errors |

### Log Writer

| **Source** | **Type of Logs** | **Examples** |
| --- | --- | --- |
| **Kernel** | System-level events | Boot messages, hardware errors |
| **System Services** | Service status and errors | `systemd`, `cron`, `NetworkManager` |
| **Applications** | App-specific logs | Apache, MySQL, Docker logs |
| **Users** | Command history, shell logs | `.bash_history`, audit logs |
| **Security Tools** | Authentication, access control | `sshd`, `sudo`, `auditd` |
| **Package Managers** | Install/update logs | `apt`, `yum`, `dnf` logs |
| **Custom Scripts** | Debug or status messages | Script-generated logs |

## Services for Logging

| Logging Service | Common Distros Using It | Init System(s) | Notes |
| --- | --- | --- | --- |
| **journald** | Ubuntu, Debian, Fedora, RHEL, CentOS, Arch, openSUSE, Oracle Linux | systemd | Binary log storage; tightly integrated with systemd. Often paired with `rsyslog`. |
| **rsyslog** | Ubuntu, Debian, RHEL, CentOS, openSUSE, Oracle Linux | systemd | Advanced syslog daemon; supports filtering, forwarding, and legacy compatibility. |
| **syslog-ng** | Gentoo, Alpine Linux, custom setups | OpenRC, others | Flexible alternative to `rsyslog`; strong network logging features. |
| **syslogd** | Slackware, older UNIX-like systems | BSD-style init | Traditional syslog daemo |
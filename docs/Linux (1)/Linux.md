# Linux

## Components Of Linux System

| Components |     |
| --- | --- |
| [Hardware](Linux/Linux%20System%20Information/Hardware%20Information%20Commands%20for%20Linux%20System.md) | CPU, Memory, Storage, Network Interfaces, Motherboard, GPU, Peripheral |
| Kernel | Manages resources (CPU, Memory, FileSystem, Network, Processes, Security, System Calls) |
| System Libraries | Pre-Compiled Code Collections that provide functions that any program wants to use |
| System Utilities | Command Line tool that performs specific task |
| File System | System that organizes and manages data storage on disks |
| Init System | SystemD, SysVInit, Open-rc, Runit, |
| Package Manager | APT, DNF, YUM, PACMAN, Zypper, |
| Network Stack | Systemd-networkd, NetworkManager, networking, netplan |
| System Targets | multi-user.target, graphical.target, recue.target, emergency.target |

---

## Get OS Information

| Components | Commands |
| --- | --- |
| Boot Loader | grub, grub2, LILO, Syslinux, systemd-boot |
| Kernel | `hostnamectl`, `uname -r`, `sysctl kernel.version`, `cat /proc/version`, `cat /proc/sys/kernel/osrelease` |
| Host | `hostname`, `uname -a`, `lsb_release -a`, `dnsdomainname`, |
| Service Manager | systemd, SysVinit, OpenRC, runit, upstart |
| Package Manager | apt, yum, dnf, dpkg, rpm, zypper, apk, pacman, pkg, opkg |
| Network Manager | systemd-networkd, NetworkManager, networking |
| File System Info | ext4, xfs, btrfs |
| Log Manager | systemd-journald, rsyslog, syslog, dmesg |
| Shell | `bash`, `sh`, `zsh`, `ksh`, `csh`, `tcsh`, `dash` |

---

## Shell Management

| Topics |     |
| --- | --- |
| SHELL |     |
| Shell Expansions | Brace, Tilde, Variables, Command Substitutions, Filenames, |
| Environment Variables | PATH, HOME, PS1, |
| Shell Start-up | `.bashrc`, `.bash_profile`, `.bash_login`, `.profile`, `/etc/profile`, |
|     |     |

---

## File System Management

| Topics | Commands |
| --- | --- |
| Navigating File System | `pwd`, `ls`, `cd`, |
| Creating Files and Dir | `touch <filename>`, `mkdir <dir-name>`, `install -d <dir-name>`, `>filename`, `vi <filename>`, `nano <filename>` |
| Removing Files | `rm <filename>`, `rm -r <directory>`, `rmdir <directroy>`, |
| Copy and Move | `cp <source> <dest>`, `mv <source> <dest>` |
| View Files Content | `cat`, `tac`, `less`, `more`, `head`, `tail`, `nl`, |
| View File Metadata | `stat`, `file`, `ls -ildt`, `lsattr`, |
| Ownership and Permissions | `chown`, `chgrp`, `chmod`, |
| links | `ln <source-file> <harlink> ln -s <source-file> <sym-link>` |
| File Archiving | `tar`, `gzip`, `bzip2`, `xz`, `zip`, |
| File Search | `find`, `locate`, |
| File Sync | `rsync`, `rclone`, |
| File Transfer |     |

---

## User and Group Management

---

## Network Management

---

## Process and Service Management

---

## [Logs Management](Linux/Logs%20Management.md)

---

## Package Management

---

## Security Management

---

## Boot Manager

---

## Environment Management
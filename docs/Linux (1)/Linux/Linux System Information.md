# Linux System Information

## Hardware Information

| Components | Commands |
| --- | --- |
| Hardware | `lshw` , `dmidecode` , `hwinfo` , `hostnamectl` , `inxi` , |
| CPU | `lscpu`, `cat /proc/cpuinfo`, `inxi -C`, `hwinfo —cpu`, `lshw -class processor`, `dmidecode -t processor`, |
| Memory | `lsmem`, `cat /proc/meminfo`, `lshw -C memory`, `dmidecode -t memory`, `inxi -mxz`, `free -htv` |
| Storage | `lsblk -f`, `sudo fdisk -l`, `sudo df -Th`, `blkid`, `mount`, `sudo lshw -class disk`, `inxi -Dxxx`, `inxi -P`, `findmnt`, `stat -f /`, |
| Network | `sudo lshw -class network`, `inxi -in`, `hwinfo —network`, `ethtool` |
| MotherBoard | `lspci`, `lsusb`, `sudo lshw -C system`, `sudo dmidecode -t baseboard`, `sudo dmidecode -t system`, |

---

## Kernal Information

| Items | Command |
| --- | --- |
| Kernel Info | `uname -r`, `cat /proc/version`, |
| Boot Command Line | `cat /proc/cmdline` |
| Modules | `lsmod`, `modinfo <module>`, |
| Kernel Parameters | `sysctl -a` |

---

## System Library Information

```bash
ldconfig -p
```

```bash
ldconfig -v
```

### Library files on filesystem

1.  `/lib`
2.  `/lib64`
3.  `/usr/lib`
4.  `/usr/lib64`
5.  `/usr/local/lib`
6.  `/usr/local/lib64`

---

## System Utilities

| Items | Commands |
| --- | --- |
| Check if command is available | `which <command>`, `whereis <command>`, |
| List Utilities | `dpkg -L coreutils`, `rpm -ql util-linux` |

---
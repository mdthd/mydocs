# Get Linux System Information

## Get System Hardware Information

```bash
sudo inxi -Faxz
```

```bash
sudo hostnamectl
```

```bash
sudo inxi -b
```

### Get System Serial Number

```bash
sudo dmidecode -s system-serial-number
```

### Get Machine ID

```bash
cat /etc/machine-id
```

### Get Mother-Board Serial Number

```bash
sudo dmidecode -s baseboard-serial-number
```

### Get CPU Information

```bash
lscpu
```

```bash
sudo dmidecode -t processor
```

```bash
sudo hwinfo --cpu
```

```bash
sudo inxi -C
```

```bash
sudo lshw -class processor
```

```bash
sudo inxi -t
```

```bash
taskset -p PID
```

```bash
cat /proc/cpuinfo
```

### Get Memory Information

```bash
sudo dmidecode -t memory
```

```bash
sudo lshw -C memory
```

```bash
sudo inxi -mxz
```

```bash
cat /proc/meminfo
```

### Get Disk Information

```bash
lsblk
```

```bash
sudo fdisk -l
```

```bash
sudo inxi -d
```

```bash
sudo inxi -p
```

```bash
blkid
```

```bash
sudo df -Th
```

```bash
mount | grep '^/'
```

---

## OS Information

#### Using `lsb_release`

```bash
lsb_release -a
```

<details>
<summary>Options for `lsb_release`</summary>

`-a` for all details

`-c` codename

`-r` release number

`-i` distribution ID

</details>

```bash
hostnamectl
```

```bash
cat /etc/os-release
```

### Get Hostname and FQDN

```bash
hostname
```

```bash
uname -n
```

```bash
cat /etc/hostname
```

```bash
cat /proc/sys/kernel/hostname
```

```bash
sysctl kernel.hostname
```

```bash
echo $HOSTNAME
```

```bash
set | grep HOSTNAME
```

### Get Kernel Information

```bash
uname -r
```

```bash
cat /proc/version
```

#### Kernel Boot Command line

```bash
cat /proc/cmdline
```

#### Check Modules loaded in kernel

```bash
lsmod
```

#### Check Kernel Parameters

```bash
sysctl -a
```

---

### Get information about Init System

Run this to know which init system is setup

```bash
readlink /sbin/init
```

:::info
Incase of /sbin/Busybox as an init, system may use Open-rc as service manager

To confirm run

```bash
command -v openrc && echo "OpenRC is installed"
```
:::

---

### Log Managers in Linux System

```bash
systemctl is-active systemd-journald rsyslog syslog-ng
```

---

### Package Manager in Linux System

Run the command to check package manager available

```bash
which {apt,dpkg,dnf,yum,rpm,pacman,apk,zypper,pkg,snap,flatpak,opkg,snap,flatpak} 2>/dev/null
```

---

### Service Manager in Linux System

check init system

```bash
 ps -p 1 -o comm=
```

or

```bash
which {systemctl,initctl,service,openrc,runit,s6-svscan} 2>/dev/null
```

=== "bash"
    ## This is Bash Code

    ```bash title="Bash Script"
    sudo apt update
    ```

=== "csh"
    ## This CSH
    
    ```bash title="CSH script"
    sudo apt-get -y update
    ```

??? info
    this os info

    ### Test info

    `info` iis

END
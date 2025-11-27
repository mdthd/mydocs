# Linux System Boot

## Linux Boot Loader

/etc/default/grub

## Linux kernel

list kenel modules: `sudo lsmod`

```sh
sudo apt search linu-generic-hwe
```

To hold a module making it not to upgrade

```bash
sudo apt-mark hold linux-generic-hwe-22.04
```

TO unhlod or enabling upgrade

```bash
sudo apt-mark unhold linux-generic-hwe-22.04
```

For `dnf` based distros

First install plugin

```sh
sudo dnf install 'dnf-command(versionlock)'
```

Lock kernel for upgrades

```bash
sudo dnf versionlock kernel
```

---

## Communicate with hardware  

System Calls: read, open, write, close
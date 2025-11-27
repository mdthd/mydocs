# Hardware Information Commands for Linux System

## Commands to get Hardware information

| Category |     |
| --- | --- |
| Hardware info | `lshw`, `hwinfo`, `dmidecode`, `inxi` |
| CPU Information | `lscpu`,`cat /proc/cpuinfo`, `dmidecode -t processor`, `hwinfo --cpu`, `lshw -class processor`, `cpuid`, `ls /sys/devices/system/cpu` |
| Memory Information | `lsmem`, `cat /proc/meminfo`, `dmidecode -t memory`, `hwinfo --memory` |
| Disk Information | `lsblk`, `blkid`, `sudo hdparm -I /dev/sda`, `hwinfo --disk`, `sudo lshw -class disk -class storage`, `inxi -D` |
| Motherboard | `cat /sys/devices/virtual/dmi/id/board_{vendor,name,version}`,  `sudo lshw -short`,  `sudo dmidecode -t 2`,  `sudo dmidecode -s baseboard-manufacturer`,  `sudo dmidecode -s baseboard-product-name`,  `sudo dmidecode -s baseboard-version`,  `sudo dmidecode -s baseboard-serial-number` |
| PCI | `lspci`, `sudo lshw -class bridge`, `sudo hwinfo --pci`, `sudo dmidecode -t slot`, |
| USB | `lsusb`, `inxi -xU` |
| BIOS | `sudo dmidecode -t bios`,  `sudo hwinfo --bios`,  `sudo lshw \| grep -A8 '*-firmware`,  `sudo biosdecode` |

---

### Using `lshw`

```bash
lshw -c CLASS
```

**List of CLASS:** system, bus, memory, processor, bridge,input, communication, generic, network

:::info
Get output in different formats by using flag `-html` `-json` `-xml`  
Get the summary or output in short `-short`
:::

---

### Using `hwinfo`

```bash
hwinfo --option
```

<details>
<summary>**List of options:**</summary>

all, arch, bios, block, bluetooth, braille, bridge, camera, cdrom, chipcard, cpu, disk, dsl, dvb, fingerprint, floppy, framebuffer, gfxcard, hub, ide, isapnp, isdn, joystick, keyboard, memory, mmc-ctrl, modem, monitor, mouse, netcard, network, partition, pci, pcmcia, pcmcia-ctrl, pppoe, printer, redasd, reallyall, scanner, scsi, smp, sound, storage-ctrl, sys, tape, tv, uml, usb, usb-ctrl, vbe, wlan, xen, zip

</details>

:::info
To get out put in short use flag `--short`
:::

---

### Using `dmidecode`

```bash
sudo dmidecode -s STRING
```

```bash
sudo dmidecode -t TYPE
```

<details>
<summary>**STRING**</summary>

bios-vendor, bios-version, bios-release-date, bios-revision, firmware-revision, system-manufacturer, system-product-name, system-version, system-serial-number, system-uuid, system-sku-number, system-family, baseboard-manufacturer, baseboard-product-name, baseboard-version, baseboard-asset-tag, chassis-manufacturer, chassis-type, chassis-version, chassis-serial-number, chassis-asset-tag, processor-family, processor-manufacturer, processor-version, processor-frequency

</details>
<details>
<summary>**Type**</summary>

bios, system, baseboard, chassis, processor, memory, cache, connector, slot

</details>

---

### Using `inxi`

```bash
inxi -FLAGS
```

Flags for System Information: `-b` or `--basic`, `-i` or `--info` , `-M` or `--machine` , `-S` or `--system`

Flags for CPU information: `-C` or `--cpu` , `-f` or `--flags` `-t c`

Flags for memory information: `-m` or `--memory` , `-t m` , `-j` or `--swap`

Flags for network information: `-i` or `--ip` , `-n` or `--network-advanced` , `-N` or `--network`

Flags for disk information: `-d` or `--disk-full` , `- D` or `--disk` , `-J` or `--usb` , `-l` or `--label` , `-L` or `--logical` , `-o` or `--unmounted` , `-p` or `--partitions-full`, `-R` or `--raid`

<details>
<summary>**Other Flags:**</summary>

`-A` or `--audio` for audio devices

`-B` or `--battery` for battery

`-E` or `--bluetooth` for Bluetooth devices

`-G` or `--graphics` for Graphic Card

`-r` or `--repos` for repositories

</details>

#### Other Options:

- `-c XX` or `--color XX` Here XX can be from 0 to 42 or 94 to 99 (depending on the color schema we want)
- `-s` or `--sensors` get sensor information
- `-v X` or `--verbose X` X is a value from 0 to 8 (based on the detail depth choose from 0 to 8)

---
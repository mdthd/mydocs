# FirewallD: firewall daemon

## FirewallD architecture

![diagram.excalidraw.svg](files/019905e9-0cc3-76df-a9e4-3fa55070438e/diagram.excalidraw.svg?t=1756740783303)

:::info
By default:

- All incoming TCP and UDP connections → blocked (except the allowed ones)
- ssh (Port 22)
- dhcpv6 client (udp 546)
- ipv6 enabled by default
- Certian ICMP request are blocked
:::

```bash
firewall-cmd --state
```

```bash
firewall-cmd --list-all
```

---

## Installing firewalld on ubuntu

1.  disable **ufw** on uduntu: `sudo ufw disable`
2.  Install firewalld: `sudo apt install firewalld`
3.  start and enable: \`sudo systemctl enable --now firewalld

---

## Services in FirewallD

### List all services

```bash
firewall-cmd --get-services
```

### Get info of a service

```bash
firewall-cmd --info-service http
```

### Services in firewalld

`/usr/lib/firewalld/services` and `/etc/firewalld/services`

### Firewalld config files

`/etc/firewalld`

### Open and Close services

```bash
firewall-cmd --add-service=[service-name]
```

```bash
firewall-cmd --add-port=[port]/[Protocol]
```

### Accessing web service running on `hostname.local`

1.  Enable http or https: `sudo firewall-cmd --add-service=http`
2.  enable mdns on server: `sudo firewall-cmd --add-service=mdns`
3.  enable mdns on client: `sudo firewall-cmd --add-service=mdns`

## Make changes persistence in firewalld

Use flag `--permanent`

### Add or remove service permanently

```bash
sudo firewall-cmd --permanent --add-service=[service-name]
```

```bash
sudo firewall-cmd --permanent --remove-service=[service-name]
```

### Add or remove port permanently

```bash
sudo firewall-cmd --permanent --add-port=[port]/[protocol]
```

```bash
sudo firewall-cmd --permanent --remove-port=[port]/[protocol]
```

---

## Zones in firewalld

1 interface in 1 zone

### Built in zones

1.  trusted
2.  home
3.  work
4.  public
5.  drop

### List all available zones

```bash
sudo firewall-cmd --get-zones
```

### List all rules of a zone

```bash
sudo firewall-cmd --zone=work --list-all
```

### Check config files of zones

```bash
cd /usr/lib/firewalld/zones
```

### Get default zone

```bash
sudo firewall-cmd --get-default-zone
```

### Change default zone

```bash
sudo firewall-cmd --set-default-zone=work
```

### Making changes to any firewall zone

:::info
Using --zone=\[zone-name\]

If --zone is not used it will consider default zone
:::

```bash
sudo firewall-cmd --zone=work --add-service=mdns
```

### Reload firewall config

```bash
sudo firewall-cmd --reload
```

### Checking zone interface

```bash
sudo firewall-cmd --list-all
```

and check the interface line

### Change interface of the zone

```bash
sudo firewall-cmd --zone=public --interface=enp0s5
```
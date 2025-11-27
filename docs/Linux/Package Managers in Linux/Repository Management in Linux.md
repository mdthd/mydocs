# Repository Management in Linux

A **Linux package repository** is a remote or local storage location that contains pre‑built software packages and metadata, used by a package manager (like `yum`, `dnf`, or `apt`) to install, update, and manage software on a system.

## Find the Repositories configured on Linux

Repositories configuration files for different distributions

| **Linux Distribution** | **Repository Configuration Location** | **File Format / Extension** |
| --- | --- | --- |
| **Debian / Ubuntu** | `/etc/apt/sources.list`  `/etc/apt/sources.list.d/` | `.list`  `.source` |
| **Fedora / RHEL / CentOS** | `/etc/yum.repos.d/`  `/etc/dnf/dnf.conf` | `.repo`, `.conf` |
| **Arch Linux** | `/etc/pacman.conf`  `/etc/pacman.d/mirrorlist` | `.conf`, plain text (`mirrorlist`) |
| **openSUSE** | `/etc/zypp/repos.d/`  `/etc/zypp/zypp.conf` | `.repo`, `.conf` |
| **Alpine Linux** | `/etc/apk/repositories` | plain text |
| **Gentoo** | `/etc/portage/repos.conf/` `/usr/share/portage/config/repos.conf` | `.conf` |

---

## Using Commands to find configured repositories

### To find configured repositories in Debian / Ubuntu

```bash
apt-cache policy
```

```bash
apt policy
```

```bash
cat /etc/apt/sources.list /etc/apt/sources.list.d/* | grep -vE '^\s*$|^\s*#'
```

Look into the file

```bash
cat /etc/apt/sources.list
```

or look into files in the directory

```bash
cat /etc/apt/sources.list.d/*
```

---

### To Find configured repositories in CentOS / RHEL / Alma / Rockey

Check all repositories

```bash
yum repolist all
```

```bash
dnf repolist all
```

Check active repositories

```bash
yum repolist
```

```bash
yum repolist --enabled
```

Get Repository info

```bash
yum repoinfo
```

---

### Enable and Disable Repositories

#### For CentOS / RHEL / Fedora based systems

To enable repository on RHEL, CentOS, Fedora

```bash
sudo yum config-manager --set-enabled <repo-id>
```

```bash
sudo yum-config-manager --enable crb
```

:::info
If `yum-config-manager` command is not found, then run

```bash
sudo yum install -y yum-utils
```
:::

To Disable

```bash
sudo yum config-manager --set-disabled <repo-id>
```

```bash
sudo yum-config-manager --disable crb
```

---

### To find configured repositories in suse

List all configured repositories with its status

```bash
zypper repos
```

Get active repos

```bash
zypper lr -E
```

Get the priority of the repositories

```bash
zypper lr -d
```

Get more detailed list of repositories

```bash
zypper lr -u
```

---

## Repository Format

### Repository formats used by Ubuntu or Debian

Debian or Ubuntu system supports `.list` or `.sources` formats both formats will be placed in`/etc/apt/sources.list.d/`

#### `.list` format for debian or ubuntu

```txt
deb [options] URI distribution [components]
```

#### Using \[options\]

| **Option** | **Possible Values** | **Description** |
| --- | --- | --- |
| `arch` | `amd64`, `i386`, `arm64`, etc. | Specifies the CPU architecture for which the repository is valid. |
| `signed-by` | Path to GPG key file (`/path/to/key.gpg`) | Specifies the GPG key file to use for repository verification. |
| `trusted` | `yes`, `no` | Marks the repository as trusted (`yes`) or not (`no`), affecting signature checks. |
| `by-hash` | `yes`, `no` | Enables hash-based verification of the repository. |
| `mirror` | URL of a mirror (`http://mirror.example.com`) | Specifies an alternative mirror server to use for downloading packages. |
| `timeout` | Any positive integer (in seconds) | Sets the connection timeout in seconds when accessing the repository. |
| `allow-insecure` | `yes`, `no` | Allows insecure repositories (no SSL verification, use carefully). |
| `proxy` | `http://proxy:port` or `https://proxy:port` | Specifies a proxy server for accessing the repository. |
| `apt-transport` | `http`, `https`, `ftp` | Forces a specific transport protocol (like `https` for secure access). |
| `no-verify` | `yes`, `no` | Disables the verification of the repository (no GPG checks). |
| `deb-src` | N/A | Indicates that the repository contains **source** packages (not binaries). |
| `retries` | Any positive integer (number of retry attempts) | Defines how many times to retry fetching from the repository in case of failure. |
| `max-age` | Any positive integer (in seconds) | Specifies the maximum age (in seconds) before the repository is refreshed. |
| `suite` | `stable`, `testing`, `unstable`, or custom suite name | Specifies a custom suite (release or codename) other than the default. |
| `priority` | `optional`, `extra`, `important`, etc. | Specifies the priority of the repository (used in package management). |
| `gpgcheck` | `yes`, `no` | Enables or disables GPG signature checks for the repository. |
| `autorefresh` | `yes`, `no` | Automatically refresh the repository metadata. |
| `cache` | `yes`, `no` | Controls caching for the repository (usually used to disable caching). |

#### Using URI

| **URI Type** | **Example** | **Description** |
| --- | --- | --- |
| **HTTP(S)** | `http://archive.ubuntu.com/ubuntu` | The most common, used for accessing repositories over the **HTTP** or **HTTPS** protocols. Can be used for both secure and non-secure communication. |
| **FTP** | `ftp://ftp.example.com/ubuntu` | Used for accessing repositories over the **FTP** protocol. Not as commonly used anymore, but still possible. |
| **Local File System** | `file:///path/to/repo/` | Refers to a repository located **locally** on the system, usually on a mounted disk or folder. |
| **CD/DVD** | `cdrom://[device]` | Used for repositories found on **CD/DVD** media, typically used for offline installations. |
| **RSYNC** | `rsync://mirror.example.com/ubuntu` | Allows access to repositories using **rsync**, a protocol that syncs files between servers. It's often used for faster updates. |
| **Git** | `git://repo.example.com/ubuntu` | Accesses repositories over **Git** protocol, generally used for source code management. |
| **File (with path)** | `file:///mnt/repo/ubuntu` | Refers to a **local repository** path, generally used when the repo is on a mounted storage or disk. |
| **SSH (Secure Shell)** | `ssh://user@host/path/to/repo` | Used for accessing repositories over the **SSH protocol**, often used in custom or private servers. |
| **Custom Protocol** | `myprotocol://example.com/repo` | Custom URIs defined by specific repository systems or scripts that need special handling. |

#### Finding URI

Find Debian Mirror List [here](https://www.debian.org/mirror/list)

Find Ubuntu Mirror List [here](https://launchpad.net/ubuntu/+archivemirrors)

#### Using Suits

| **Suite** | **Purpose** |
| --- | --- |
| **Release codename** (e.g., `jammy`, `focal`, `bookworm`, `bullseye`) | Targets a specific OS release; updates stay within that release.   To know the code name run `lsb_release -c` |
| **stable** | Always points to the current stable release; changes when a new stable version is published. |
| **oldstable** | Previous stable release, still receiving limited support/security updates. |
| **testing** | Pre‑release branch for the next stable; newer packages, more changes, possible instability. |
| **unstable** or `sid` | Active development branch; cutting‑edge software, least stable. |
| `<codename>-updates` | Approved bug fixes for that release after publication. |
| `<codename>-security` | Urgent security patches for that release; highest update priority. |
| `<codename>-backports` | Selected newer software rebuilt for a stable release; for users who want newer features without upgrading OS. |
| `<codename>-proposed` / `-proposed-updates` | Testing area for updates before they’re released to `-updates`; not recommended for production. |
| **experimental** | Highly unstable packages under early development; intended for developers/testers only. |

Using Components:

| **Ubuntu / Debian** | **Meaning** |
| --- | --- |
| `main` | Free official software |
| `universe` _(Ubuntu)_ | Free community software |
| `restricted` _(Ubuntu)_ | Official proprietary drivers/software |
| `multiverse` _(Ubuntu)_ | Proprietary / legally restricted software |
| `contrib` _(Debian)_ | Free software needing non‑free stuff |
| `non-free` _(Debian)_ | Proprietary / not open‑source software |

---

#### `.source` format of repository files

| **Field** | **Meaning** |
| --- | --- |
| `Types` | What to download: `deb` = binary packages, `deb-src` = source code. |
| `URIs` | Web/mirror address of the repo. |
| `Suites` | Release name or branch (e.g., `bookworm`, `stable`). |
| `Components` | Sections of packages (`main`, `universe`, `restricted`, `multiverse` in Ubuntu; `main`, `contrib`, `non-free` in Debian). |
| `Signed-By` | GPG key file used to verify the repo’s packages. |
| `Architectures` | CPU types allowed (e.g., `amd64`, `arm64`). |
| `Languages` | Optional — limit which language packages to download. |
| `Trusted` | Optional — `yes`/`no` to trust repo without signature checks (not recommended). |

:::info
Not all fields are required in .source file

The key ones for most users: `Types`, `URIs`, `Suites`, and `Components`.
:::

Examples:

```source
Types: deb deb-src
URIs: http://deb.debian.org/debian
Suites: bookworm bookworm-updates bookworm-security bookworm-backports
Components: main contrib non-free
Architectures: amd64 arm64 armhf
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg
Languages: en fr
Trusted: no
```

---

### Repository Format for CentOS / RHEL / Alma / Rockey Linux

RHEL or CentOS or Rockey Linux supports `.repo` formatted files.

These .repo files are available at `/etc/yum.repo` or `/etc/yum.repo.d/*`##

#### `.repo` file format

| Line | Meaning |
| --- | --- |
| `[custom-repo]` | Unique ID for the repo (used by `dnf`/`yum`) |
| `name=` | Human-readable name shown in output |
| `baseurl=` | URL or path where RPMs are stored |
| `enabled=` | `1` = repo is active; `0` = disabled |
| `gpgcheck=` | `1` = verify packages with GPG key |
| `gpgkey=` | URL to the GPG key used for verification |
| `priority=` | Lower number = higher priority (used when multiple repos have same pkg) |
| `exclude=` | Prevents listed packages from being installed from this repo |
| `includepkgs=` | Limits repo to only these packages |

#### Base URL or Mirrors for RHEL, CentOS, SUSE, Rockey

Mirrors for suse, find [here](https://mirrors.opensuse.org/)

Mirrors for RHEl, find [here](https://mirrors.rockylinux.org/mirrormanager/)

Mirrors for Centos, find [here](http://vault.centos.org)

#### Using `gpgkey=`

Pass the key using URI, URI can be link pointing to external file or link pointing to file on the local file system

##### For Rockey Linux

`gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-rockyofficial`

or

`gpgkey=https://dl.rockylinux.org/pub/rocky/RPM-GPG-KEY-rockyofficial`

#### Using `priority=`

The `priority=` directive is used in `.repo` files to control which repository takes precedence when multiple repos offer the same package. Lower numbers mean **higher priority**.

:::info
#### Important

- **Valid range**: Typically `1` to `99`. Lower = higher priority.
- **Requires** `yum-plugin-priorities`: On RHEL-based systems like CentOS or Rocky Linux, this plugin must be installed and enabled.
- **Default priority**: If not specified, repos are treated equally (priority 99)
:::

---
# Package Management in Ubuntu/Debian

## dpkg: Debian Package Manager

It is responsible for installing packages

```bash
dpkg -i package.deb
```

`.deb` file is a compressed archive (ar file format) it includes all files needed for the program to run,= and its installation on the system.

### To get debian packages for ubuntu

Go to https://packages.ubuntu.com

Get Ubuntu code name: `lsb_release -a`

#### Reconfigure DPKG package

```bash
sudo dpkg-reconfigure <package>
```

### Dependency Management with `apt`

`apt` or `apt-get` search packages in the packages repositories configured in `/etc/apt/sources.list` or `/etc/apt/sources.list.d/*`

#### Update Package Definitions

```bash
sudo apt update
```

This updates the list of available versions of all packages installed on the ubuntu system from the configured repositories.

#### Upgrade the packages

```bash
sudo apt upgrade
```

#### Managing full-upgrade / dist-upgrade

```bash
sudo apt full-upgrade
```

`dist-upgrade` is equivalent to `full-upgrade` , this can remove some important dependencies packages

#### Auto removing packages

```bash
sudo apt autoremove
```

### Source List Management

Structure of line in `/etc/apt/source.list`

`deb http://ports.ubuntu.com/ubuntu-ports/ jammy main restricted`

Field one `deb`: conatins binary packages, `deb-src`: This contains source packages

Field 2: URI

Field 3 or Field 4 ... : Domains,

**Domains**: `main` and `universe` are free, `restricted` and `multiverse` are non-free, `code-updates` : major bug fixes, `code-backports`: new version of software

#### Other format of Sources file

```txt
Types: deb
URIs: http://
Suites: code
Components: main
Architecture: amd64 i386
Signed-By: /etc/apt/Keyrings/XXXXXX.key
```

### Custom Repositories

1.  Creating a new file in `/etc/apt/sources.list.d/*`
2.  Adding GPG key to our system for this repository
3.  Updating the system after adding is recommended

#### PPA on ubuntu

This works on ubuntu not on debian

Steps:

1.  Goto https://launchpad.net/ubuntu+ppas
2.  Search the repository
3.  `sudo apt-add-repository ppa:person/package`
4.  It will add a file in /etc/apt/source.list.d/
5.  Update the defnitions of the system

To remove ppa repo

`sudo apt-add-repository -remove ppa:person/package`

---

### Verifying installation: `debsums`

Check all packages

```bash
debsums -a
```

Check all packages that has changed

```bash
debsums -a -s
```

Check all packages that do not have md5

```bash
checksums -l
```

---

### Debug dependencies

Find the dependencies of the packages

```bash
apt show package
```

Pre-Depends: Should be installed before the package is unpacked and installed

Depends: Should also be installed before the package is unpacked and installed

Recommends: Not required, but should be installed unless any special requirements arise

Suggest: not required, can be ignored

Replaces: Will remove any dependencies that are causing conflicts

#### Conflict resolution

```bash
sudo apt install -f
```

`-f` = `--fix-broken`

To overwrite by ignoring dependencies while installing package using `dpkg`

```bash
sudo dpkg -i package.deb --ignore-depends
```

#### If software is not launching due to dependency conflict

1.  Remove unnecessary packages: `sudo apt autoremove`
2.  Remove conflicting packages, and update and upgrade
3.  Remove the software and install again from official repository
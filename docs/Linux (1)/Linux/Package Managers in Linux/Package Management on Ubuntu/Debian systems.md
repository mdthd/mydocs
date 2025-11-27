# Package Management on Ubuntu/Debian systems

A **package manager** is a tool that automates the process of installing, updating, configuring, and removing software.

---

## Important Terminologies

- **Package Definitions** Metadata describing a software package — includes its name, version, description, dependencies, and source location in the repository.
- **Cache** A local copy of repository metadata (and sometimes packages) stored on your system for faster searches and installs.
- **Updating Cache** Refreshing the local metadata so the package manager knows the latest available packages and versions in the repository.
- **Repository (Repo)** A storage location containing software packages and metadata for installation via a package manager.
- **Dependency** A package required for another package to work properly.
- **Mirror** A duplicate server hosting the same repository content, used for faster or more reliable downloads.
- **GPG Key** A cryptographic key used to verify that packages from a repository are authentic and unmodified.
- **Package Manager** A tool (e.g., `apt`, `yum`, `dnf`) that automates installing, updating, and removing software from repositories.

---

## Package manager

helps to:

- Install software packages
- Update software (single or system‑wide)
- Remove/uninstall software
- Automatically handle dependencies
- Search for packages
- Verify package integrity/security
- Manage repositories (software sources)

---

## `dpkg`: Debian Package

**dpkg** is low level package manager in debian based linux distributions.

It manages `.deb` files.

Deb files are archive files containing the compressed bundle of files that are required to install a program

### dpkg is used to:

- list installed packages
- check the status of installed packages
- Install deb packages
- remove deb packages
- purge deb packages

### Using `dpkg`

| Usage | Command |
| --- | --- |
| Search for installed debian package | `dpkg -S <pattern>` |
| Check status of a package | `dpkg -s <package-name>` |
| Show installed Path and files of a package | `dpkg -L <package-name>` |
| List installed dpkg packages | `dpkg -l` or `dpkg-query -l` |
| Install a .deb package | `dpkg -i <path-to-deb-file>` |
| Remove a .deb package | `dpkg -r <package-name>` |
| Purge a .deb package | `dpkg -p <package-name>` |
| Reconfigure package | `dpkg-reconfigure <package-name>` |

### To get debian packages for ubuntu

Go to https://packages.ubuntu.com

Get Ubuntu code name: `lsb_release -a`

#### To find debian packages for debian

Go to [https://www.debian.org](https://www.debian.org/)

---

## `apt`: Advanced Package Tool

APT is command line, high level package management tool for debian based systems.

APT automates the installation, patching, upgrade and removal of software packages.

APT handles the dependencies automatically.

### Purpose of `apt`:

- **Search** for packages from the configured repository
- **Get information** of packages available in the configured repositories
- Know the **dependencies** of the packages
- **Update** the existing information of packages on the system
- **Upgrade** the packages
- **Remove** the packages
- Manage the repositories
- **Download** the packages from the repositories

### Basic usage of `apt`

| Usage | Command |
| --- | --- |
| Search | `apt search pattern` |
| Get Information | `apt show package` |
| Install | `apt install package` |
| Reinstall | `apt reinstall package` |
| Remove /Uninstall | `apt remove package` |
| Purge (uninstall with removing config files) | `apt purge package` |
| List installed | `apt list --installed` |
| List upgradeable | `apt list --upgradeable` or  `apt list --upgradeable -a` |
| Upgrade by remove packages that are not required by current upgrade | `apt full-upgrade` or  `apt dist-upgrade` |
| Remove unused packages | `apt autoremove` |
| Remove unused packages with its configs | `apt autopurge` or `apt autoremove --purge` |
| Clean cache | `apt autoclean` |
| Update information of packages | `apt update` |
| Upgrade packages to latest version | `apt upgrade` |

---

### How `apt update` works:

Updates `local cache` with the information available in the configured repositories

#### Steps followed when `apt update` command is run:

1.  Read the list of sources from the files `/etc/apt/sources.list` and files in the directory `/etc/apt/sources.list.d/`
2.  Downloads the latest metadata of all available packages in the enabled repositories. Metadata will have:
    1.  Package Version
    2.  Description
    3.  Dependencies
    4.  Supported Architecture
    5.  File Size
    6.  Repository integrity information
3.  Updates local index files available at `/var/lib/apt/lists/` with new info
4.  System comes to know which installed package has new versions to which that packages can be upgraded. To find out run `apt list —upgradeable`

---

### How `apt upgrade` works :

1.  Upgrade will look the local cache (index files: `/var/lib/apt/lists`) for new versions available for all installed packages
2.  For all available newer versions for packages, dependencies are checked in the system if installed or not.
    1.  If not installed then it will be added to list that gets prompted to get consent for installation
    2.  If installed, then checks if correct version is installed or package needs upgrade, then this will add for prompted for the consent list
3.  Once the consent is provided all required packages will be downloaded and installed

`apt full-upgrade` and `apt dist-upgrade` are equivalent, they perform same thing

- Normal upgrade will upgrade all packages but does not remove any dependencies that are not required
- full-upgrade will upgrade all available packages also removes dependencies that are not required
- Normal upgrade holds back upgrades that requires removal of dependencies but full-upgrade will not hold back but proceeds to remove it to upgrade

---
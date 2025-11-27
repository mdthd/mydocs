# Package Management in RedHat/CentOS/Fedora

Fedora —> CentOS Stream —> RHEL

### RPM package Format

`.rpm` file includes all configuration and files required to install software packages

https://mirror.stream.centos.org

AppStream more outer softwares, and BaseOS more core softwares

#### inspect rpm file

```bash
rpm -qpl package.rpm
```

#### Install rpm file

```bash
rpm -i package.rpm
```

#### Remove or uninstall rpm package

```bash
rpm -e package.rpm
```

### DNF (Dandified Yum)

```bash
ls -al $(which dnf yum)
```

#### Search package name

```bash
sudo dnf search <package>
```

#### Install epel

```bash
sudo dnf config-manager --set-enabled crb
sudo dnf install epel-release
```

---

### Repositories in RHEL / CentOS / Fedora

`yum` and `dnf` will search packages in the repositories configured in `/etc/dnf/dnf.conf` or `/etc/yum.repos.d/*.repo`

:::info
Need not required refresh of the repositories, everytime we install the package or upgrade the repositories definition list gets refreshed
:::

#### Check what functionality a package can provide to the system

```bash
dnf repoquery --provides <package-name>
```

What provides filesystem

```bash
dnf repoquery --whatprovides filesystem
```

#### Check what functionality is required by the package if it is to be installes

```bash
sudo dnf repoquery --requires <package-name>
```

What requires by package

```bash
dnf repoquery --whatrequires package
```

---

### Level of Dependencies

#### Optional Dependencies (weak): Recommended and Suggests

`dnf repoquery --recommends packagename` and `dnf repoquery --suggests <package-name>`

#### Disable weak dependencies

In the file `/etc/dnf/dnf.conf` make this false `install_weak_deps=False` or add it manually in new line

or use command `dnf install <package-name> —setopt=install_weak_deps=False`

:::info
**Pre-Install Dependency > Dependency > Recommends > Suggest**
:::

---

### Remove / Keep dependencies while uninstall

`clean_requiements_on_remove=False` then run `dnf autoremove`

#### Remove package not dependency

```bash
sudo dnf remove <package> --noautoremove
```

#### Marking package to be installed by user

- When any package is installed, all its dependencies are marked as dependencies
- When any dependencies are installed using dnf or yum then it will be marked as dependency
- When any dependencies are installed using apt then it will be marked as user installed package
- To make any dependency to be marked as user installed using dnf or yum, the run  
    `dnf mark install <package>`
- While removing packages, marked packages will not be removes even if it is dependency

---

### Update and downgrade in RHEL / FEDORA / CentOS

#### Downgrade

`dnf downgrade <package>`

`dnf downgrade <package-version>`

#### List duplicates:

`dnf list python3 —showduplicates`

---

### Prevent Packages from upgrade

`dnf upgrade --exclude=python3`

or `dnf upgrade --exclude=python3,other-packages`

#### Exclude permanently

in `/etc/dnf/dnf.conf`

Paste this line

`excludepkgs`\=\[packages\]

---

Automatically keep the system upto date

```bash
sudo dnf install dnf-automatic
```

```bash
sudo vim /etc/dnf/automatic.conf
```

```bash
sudo systemctl enable --now dnf-automatic.timer
```

---

### DNF Modules

dnf module list

dnf module enable \[module\]:\[stream\]/\[profile\]

dnf module remove --all &lt;nodejs&gt;

dnf module disable &lt;package&gt;

dnf module reset &lt;packages&gt;

---

### Repository: epel-release

EPEL: Extra Package for Enterprise Linux

This is community driven project,

#### Enable epel-release

```sudo
sudo dnf config-manager --set-enabled crb
sudo dnf install epel-release epel-next-release
```
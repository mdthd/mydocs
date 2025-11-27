# User Account Creation

# Create User Account in Linux

## Create User Account with default configuration:

### Create User Account using `useradd` command:

```bash
sudo useradd USERNAME
```

<details>
<summary>To check the defaults for user account creation while `useradd` command is used</summary>

1\. Check with the command  
`bash useradd -D`  
2\. Check the file  
`bash cat /etc/default/useradd`  
`bash cat /etc/login.defs`

</details>

### Create User Account using `adduser` command:

```bash
sudo adduser USERNAME
```

### To check the default configuration information

#### Check the files

```bash
cat /etc/adduser.conf
```

```bash
cat /etc/default/useradd
```

```bash
cat /etc/login.defs
```

---

### Process of User Account creation

1.  Selecting UID and GID for the user as per defined in /etc/login.defs (UID_MIN, UID_MAX, GID_MIN and GID_MAX)
2.  Creating new **Group Account** with same name as the user, adding new line entry to the file `/etc/group`
3.  Creating the **User Account** with UID and GID and adding new line entry to `/etc/passwd`
4.  Adding User Account to the Group Account, modifying the line added to the file `/etc/group` in step 2
5.  Creating User's Home directory, and modifying the line added to `/etc/passwd`
6.  Copying file from `/etc/skel` to user's home directory
7.  If user has setup password, it will modify the file `/etc/shadow`
8.  If addition info like **Full Name**, **Room Number**, **Work Phone**, **Home Phone** and **Other** is set, that will modify the file `/etc/passwd`

### Creating a user account without using the default settings

#### Manually specifying UID

```bash
sudo useradd -u 1051 USERNAME
```

or

```bash
sudo adduser USERNAME --uid 1051
```

#### Manually specifying **GID** of the user account

```bash
sudo useradd -g GID USERNAME
```

or

```bash
sudo adduser USERNAME --gid GID
```

#### Manually specifying **Primary Group Name** for the user account

```bash
sudo adduser USERNAME --ingroup GROUPNAME
```

#### Manually specifying range for UID and GID

```bash
sudo adduser USERNAME --firstuid 1101 --lastuid 1150 --firstgid 1101 --lastgid 1150
```

#### Manually adding user to secondary groups

```bash
sudo useradd -G group1,group2 USERNAME
```

```bash
sudo adduser USERNAME --groups group1,group2
```

#### Create User without creating default group

```bash
sudo useradd -N USERNAME
```

or

```bash
sudo adduser USERNAME --no-create-home
```

#### Manually specifying default shell for user

```bash
sudo useradd -s /bin/bash USERNAME
```

or

```bash
sudo adduer USERNAME --shell /bin/bash
```

:::info
#### To check available shells on linux host

```bash
cat /etc/shells
```
:::

---

# Creating User Account with custom Home Directory

:::info
Ensure that argument mentioned in option `-d` or `-b` should not end with `/`.
:::

### Manually specifying existing directory as User's Home Directory

```bash
sudo useradd -d /Other/Home USERNAME
```

<details>
<summary>Note</summary>

- The user account created using `-d /Other/Home` then the /Other/Home becomes user home directory
- The Home directory permissions will not be modified
- The contents from the `/etc/skel` will not be copied to the Home directory

</details>

### Manually specify the not existing directory to be a User's Home Directory

```bash
sudo useradd -m -d /Other/Home USERNAME
```

:::info
Note

- The path to Home directory should exist if not it throws warning
- The Home directory should not exist if it exists then
    - No files will be copied from `/etc/skel`
    - User will not be the owner of the Home Directory
:::

### Creating User Account having Home Directory in Other Directory

```bash
sudo useradd -m -b /Other/Base/Dir USERNAME
```

:::info
**Note**  
**Base Directory** is a directory that holds users home directory
:::

---

# Create User Account with Custom Group

## Create user account without creating default group account

```bash
sudo useradd -N USERNAME
```

### Manually specifying **GID** or **Group Name** of the Primary group of the user account

```bash
sudo useradd -g <GID|GROUPNAME> USERNAME
```

or

```bash
sudo adduser USERNAME --gid GID
```

or

```bash
sudo adduser USERNAME --ingroup GROUPNAME
```

:::info
Note

Points to be noted

- In **useradd** command **gid** or **group name** of the Group can be specified as an argument to **\-g**
- In **adduser** command **GID** can be specified in **\--gid** and **GROUPNAME** can be specified in **\--ingroup** option
- Ensure that the groups which are specified are already existing on the system
:::

### Manually specifying range for UID and GID

```bash
sudo adduser USERNAME --firstuid 1101 --lastuid 1150 --firstgid 1101 --lastgid 1150
```

### Manually adding user to secondary groups

```bash
sudo useradd -G group1,group2 USERNAME
```

```bash
sudo adduser USERNAME --groups group1,group2
```

---

# Create User Account with Custom Account Settings

### Specify different Skel directory

```bash
sudo useradd --skel SKEL_DIR USERNAME
```

### Specify UID

```bash
sudo useradd -u UID USERNAME
```

or

```bash
sudo adduser USERNAME --uid UID
```

### Specify GID

```bash
sudo useradd -g GID USERNAME
```

or

```bash
sudo adduser USERNAME -gid GID
```

### Specify the range of UID

```bash
sudo adduser USERNAME --firstuid 1100 --lastuid 1150
```

### Specify the range of GID

```bash
sudo adduser USERNAME --firstgid 1100 --lastgid 1150
```

### Specify Shell

```bash
sudo useradd -s /bin/sh USERNAME
```

or

```bash
sudo adduser USERNAME --shell /bin/sh
```

---

# Create Group Account in Linux

### Creating group account in linux

```bash
groupadd GROUPNAME
```

or

```bash
addgroup GROUPNAME
```

### Creating group account by specifying its GID

```bash
groupadd GROUPNAME -g GID
```

or

```bash
addgroup GROUPNAME --gid 1101
```

### Create group by specifying range of GID

```bash
addgroup GROUPNAME --firstgid 1101 --lastgid 1140
```

### Create group and add users to it

```bash
groupadd GROUPNAME -U user01,user02,user03
```

### Temporarily change my primary group

```bash
newgrp GROUPNAME
```

---
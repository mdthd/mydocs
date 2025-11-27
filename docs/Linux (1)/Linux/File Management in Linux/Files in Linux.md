# Files in Linux

A _file_ is a logical collection of data stored on disk, represented by a pathname and identified by an **inode**. Everything in Linux is treated as a file, including devices and processes.

## Features of files in linux

- **Everything is a file**: Devices, directories, and processes are treated as files.
- **Case-sensitive**: `File.txt` and `file.txt` are different.
- **Hierarchical structure**: Files are organized in a tree-like directory system.
- **Permissions**: Each file has read, write, and execute permissions for user, group, and others.
- **Ownership**: Files are owned by a user and a group.
- **Hidden files**: Files starting with `.` are hidden.
- **File types**: Includes regular files, directories, symbolic links, device files, etc.
- **No file extensions required**: File type is determined by content, not extension.
- **Symbolic and hard links**: Files can be linked to others for easy access.
- **Metadata**: Each file stores info like size, creation/modification time, and permissions.
- **Inodes**: Each file has an inode storing metadata (except name).

---

## Types of Files

| **File Type** | **Symbol** | **Description / Purpose** |
| --- | --- | --- |
| **Regular File** | `-` | Contains data, text, or program instructions. Most common file type. |
| **Directory** | `d` | A folder that holds other files and directories. |
| **Symbolic Link** | `l` | A reference or shortcut to another file or directory. |
| **Character Device** | `c` | Represents devices that handle data character by character (e.g., keyboard, serial port). |
| **Block Device** | `b` | Represents devices that handle data in blocks (e.g., hard drives, USB drives). |
| **Socket** | `s` | Used for inter-process communication, often in networking. |
| **Named Pipe (FIFO)** | `p` | Enables communication between processes; data flows in a first-in-first-out manner. |

---

## File Permissions

### Check the permissions of File

```bash
ls -l <file-path>
```

```bash
stat -c %A <file-path>
```

```bash
stat -c %a <file-path>
```

```bash
namei -m <file-path>
```

### Permissions chart

| **Symbolic** | **Binary** | **Octal** | **Meaning** |
| --- | --- | --- | --- |
| `---` | 000 | 0   | No permissions |
| `--x` | 001 | 1   | Execute only |
| `-w-` | 010 | 2   | Write only |
| `-wx` | 011 | 3   | Write and execute |
| `r--` | 100 | 4   | Read only |
| `r-x` | 101 | 5   | Read and execute |
| `rw-` | 110 | 6   | Read and write |
| `rwx` | 111 | 7   | Read, write, execute all |

### Changing permissions of file

```bash
chmod <Options> <file-path>
```

#### Ways to write options

1.  in octal form `777`, `644`
2.  `u+x` form
    1.  In place of `u` specify `u` for file owner, `g` for group, `o` for others and `a` for all
    2.  in place of `+` put `+` to add permissions or `-` to remove permissions
    3.  in place of `x` put `r` for read, `w` for write and `x` for execute

#### Examples

`u+x` to add execute permissions for file owner

`g-w` to remove write permissions for user belonging to the file group

`a+rx` to add read and execute permissions to all users

---

## File Ownership

### File Owner

#### Know the file owner

```bash
ls -l <file-path>
```

```bash
stat -c "%U" <file-path>
```

```bash
namei -o <file-path>
```

#### Change the file owner

```bash
chown newowner <file-path>
```

### File Group

#### Know file group

```bash
ls =l <file-path>
```

```bash
stat -c "%G" <file-path>
```

```bash
namei -o <file-path>
```

#### Change file group

```bash
chgrp GROUP <file-path>
```

### To change file owner and group

```bash
chown USER:GROUP <file-path>
```

### Change file owner or group of directories and inherit to sub files and directories

```bash
chown -R newowner <path-of-directory>
```

```bash
chgrp -R newgroup <path-of-diretcory>
```

```bash
chown -R owner:group <path-of-directory>
```

---

## File Metadata

| **Metadata Type** | **Description** | **Command to View** | **In Inode?** |
| --- | --- | --- | --- |
| **Inode number** | Unique file identifier | `stat`, `ls -i` | ✓ Yes |
| **File type** | Regular file, directory, link, etc. | `stat`, `file`, `ls -l` | ✓ Yes |
| **File size** | Size in bytes | `stat`, `ls -l`, `du` | ✓ Yes |
| **Hard link count** | Number of hard links | `stat`, `ls -l` | ✓ Yes |
| **Owner (UID)** | User ID of owner | `stat`, `ls -l`, `id` | ✓ Yes |
| **Group (GID)** | Group ID | `stat`, `ls -l` | ✓ Yes |
| **Permissions** | rwx permissions for owner/group/others | `stat`, `ls -l` | ✓ Yes |
| **Special permissions** | setuid, setgid, sticky bit | `stat`, `ls -l` | ✓ Yes |
| **Access time (atime)** | Last access timestamp | `stat` | ✓ Yes |
| **Modify time (mtime)** | Last content modification | `stat`, `ls -l` | ✓ Yes |
| **Change time (ctime)** | Last metadata change | `stat` | ✓ Yes |
| **Birth time** | Creation time (if supported) | `stat` | ✓ Yes |
| **Device ID** | Storage device identifier | `stat` | ✓ Yes |
| **Block size** | I/O block size | `stat` | ✓ Yes |
| **Blocks allocated** | Disk blocks used | `stat`, `du` | ✓ Yes |
| **Filename** | The actual file name | `ls`, `find` | ✗ No |
| **Directory path** | Full path to file | `pwd`, `realpath` | ✗ No |
| **Extended attributes** | ACLs, SELinux contexts, custom attrs | `getfacl`, `getfattr` | ✗ No |
| **File attributes** | chattr flags (immutable, append-only, etc.) | `lsattr` | ✗ No |
| **MIME type** | File format/content type | `file --mime-type` | ✗ No |
| **File content** | Actual data inside the file | `cat`, `less`, `head` | ✗ No |

---

## File Attributes

| Flag | Name | Effect | View | Modify |
| --- | --- | --- | --- | --- |
| i   | Immutable | Cannot modify, delete, rename, or link | `lsattr file` | `sudo chattr +i file` / `sudo chattr -i file` |
| a   | Append-only | Only append; no overwrite or delete | `lsattr file` | `sudo chattr +a file` / `sudo chattr -a file` |
| A   | No atime update | Reading file won’t update atime | `lsattr file` | `sudo chattr +A file` / `sudo chattr -A file` |
| d   | No dump | Excluded from dump backups | `lsattr file` | `chattr +d file` / `chattr -d file` |
| S   | Synchronous updates | Writes are flushed immediately | `lsattr file` | `sudo chattr +S file` / `sudo chattr -S file` |
| T   | Top directory | Hint for placement under dir trees | `lsattr dir` | `sudo chattr +T dir` / `sudo chattr -T dir` |
| D   | Synchronous dir updates | Dir updates written synchronously | `lsattr dir` | `sudo chattr +D dir` / `sudo chattr -D dir` |
| C   | NOCOW (btrfs) | Disable copy-on-write for file/dir | `lsattr file` | `sudo chattr +C file` / `sudo chattr -C file` |
| j   | Data journaling (ext) | Journal data as well as metadata | `lsattr file` | `sudo chattr +j file` / `sudo chattr -j file` |
| c   | Compressed (FS-dependent) | File stored compressed on-disk | `lsattr file` | `sudo chattr +c file` / `sudo chattr -c file` |
| u   | Undelete (legacy) | Try to keep data for undeletion | `lsattr file` | `sudo chattr +u file` / `sudo chattr -u file` |
| s   | Secure deletion (legacy) | Attempt to zero on delete | `lsattr file` | `sudo chattr +s file` / `sudo chattr -s file` |

---
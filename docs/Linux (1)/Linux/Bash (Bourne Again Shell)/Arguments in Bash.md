# Arguments in Bash

**Argument** in bash are values that can be passed to bash scripts or functions when they are executed

## Passing arguments to scripts

`./script argument1 argument2 argument3`

:::info
argument0 is `$0`

if i run `./script arg1` then `$0` is `./script`
:::

## Special Bash Variables

| Variable | Description |
| --- | --- |
| `$0` | Name of the script |
| `$1` to `$9` | First to ninth command-line arguments |
| `${10}`, `${11}`, ... | Arguments beyond the ninth (use curly braces) |
| `$#` | Number of arguments passed to the script |
| `$@` | All arguments as separate strings (preserves spaces) |
| `$*` | All arguments as a single string |
| `$$` | Process ID of the current shell |
| `$!` | Process ID of the last background command |
| `$?` | Exit status of the last executed command |
| `$-` | Current shell options (e.g., `-x`, `-v`) |
| `$IFS` | Internal Field Separator (default is space, tab, newline) |
| `$RANDOM` | Generates a random number between 0 and 32767 |
| `$UID` | User ID of the current user |
| `$EUID` | Effective User ID (useful for checking root privileges) |
| `$PWD` | Current working directory |
| `$OLDPWD` | Previous working directory |
| `$HOME` | Home directory of the current user |
| `$PATH` | Colon-separated list of directories for executable search |
| `$SHELL` | Path to the current shell |
| `$HOSTNAME` | Name of the host system |
| `$LINENO` | Current line number in the script |
| `$BASH_VERSION` | Version of Bash being used |
| `$BASH_SOURCE` | Array of source filenames for the current script |

## shift command

Shift command is used to run variable number of arguments

```bash
#!/usr/bin/env bash
while (( $# != 0 )); do
    echo "$1"
    shift
done
```

## getopts command

```bash
getopts 'al' option
```

In the above command, `a` and `l` are the options that will be stored in the `option` variable

`a` and `l` can be passed to the script in a way `-a` or `-l` or `-a -l` or `-al`

### Accepting multiple options

```bash
while getopts 'al' opt 2>/dev/null; do
   echo ${opt}
done
```

In the above bash commands, `a` and `l` options will be accepted, if anything else than a and l is used it will be considered as `?`

Using case command to make use of the options

```bash
while getopts 'al' opt 2>/dev/null; do
  case "${opt}" in
    a) echo "option a"
        ;;
    l) echo "option l"
        ;;
    ?) echo "Unknown Option"
        ;;
    esac
```

### Using Parameters for an option

```bash
#!/bin/bash

while getopts 'af:' opt; do
        case "${opt}" in
                a) echo ${opt}
                        ;;
                f) echo "${opt}: ${OPTARG}"
                        ;;
        esac
done
```
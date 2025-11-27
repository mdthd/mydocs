# Environment Management

Shell is outer layer

#### Env variables

written in upper case

List environment variables `env`

`PWD` , `OLDPWD`,

### Create new env variable

```bash
export VAR="VALUE"
```

Environment variable **PATH**

```bash
echo $PATH
```

`/home/azureuser/.local/bin:/home/azureuser/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin`

higher priority for left ones

| Path | Purpose |
| --- | --- |
| `/bin` | Essential Binaries, available always |
| `/sbin` | Essential root binaries, available for root always |
| `/usr/bin` | Non-essential, available for all users, shared with other computers |
| `/usr/sbin` | Non-essential, for root users, shared with other computers |
| `/usr/local/bin` | Non-essential, for all user on this hosts |
| `/usr/local/sbin` | Non-essential, for all root users on the host |

#### Modify the path

```bash
PATH="${PATH}:/opt/app/bin"
```

#### Find binaries

```bash
which <binary-name>
```

Environment variable **SHELL**

`echo $SHELL`, `chsh -s /bin/bash`, `cat /etc/shells`,

Persistant env variables

`~/.bashrc`, `~/.bash_profile`, `~/.profile`,

1.  interactive login shell (ssh/tty)
2.  interactive non login shell (terminal on gui/shell insde interactive shell)
3.  non interactive login shell ()
4.  non interactive non login shell ([script.sh](http://script.sh))

#### Bash startup files

login into interactive login shell

- /etc/profile
    - ~/.bash_profile
    - ~/.bash_login
    - ~/.profile

Login into interactive non-login shell

- ~/.bashrc

### Alias

```bash
alias gohome='cd ~'
```

### Configuring shell

enable feature `set -[feature]`

disable feature `set +[feature]`

```bash
set -x # enable debug feature in shell
```

```bash
set +x #disable debug feature in shell
```

List of features available at https://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html

enable configuration option

`shopt -s [optname]`

disable configuration option

`shopt -u [optname]`

[https://www.gnu.org/software/bash/manual/html_node/The-shopt-Builtin.html](https://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html)

---

### Bash Prompt customize

PS1 variable

In PS1

| Option | Use |
| --- | --- |
| \\u | Username |
| \\h | hostname |
| \\H | FQDN |
| \\w | Full Path |
| \\W | Current Directory |
| \\t | time in 24H |
| \\@ | time in 12H |

Put this `PS1` value in `.bashrc`

#### how color works in bash

`echo “${TERM}“`

`toe` or `toe -a`  

`infocmp`

##### `tput` command

`tput clear`, `tput cup 5 20`, `tput bold`, `tput sgr0`, `tput smul`, `tput setaf 4`, `tput setab 5`,

to list colors

```bash
for i in {0..15}; do echo "$(tput setab ${i}) color: ${i}$(tput sgr0)"; done
```

`tput lines`, `tput cols`, `tput colors`,

https://www.gnu.org/software/bash/manual/html_node/Controlling-the-Prompt.html

PS1

```bash
PS1='\n🖥️ \h | 👤 \u | 🕒 \A\n📁 $(pwd | sed "s|^/||; s|/| ➤ |g")\n\$ '
```

```bash
PS1='\n👤\u@🖥️\h:📁$(pwd | sed "s|^/||; s|/| ➤ |g") |  (🕒\A)\n\$ '
```

Shell expansions

`ls *` , `ls ?.txt`, `ls ~`,

Variable expansion

`$HOME`, `${HOME}`,

Print part of variable from starting point and length

`${VARIABLE:start:length}`

Print variable with replacing path

${VARIABLE/pattern/replace}

`cat $PWD/*.txt` will expand variable and regex

single quotes will not expand anything

double quotes will expand variables but not the eregex

Escaping in shell

brace expansion

echo data.{csv,txt} is equal to

no qutes for brace expansion
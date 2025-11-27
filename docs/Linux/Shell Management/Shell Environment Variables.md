# Shell Environment Variables

Environment variables in Linux are dynamic values used by the shell and applications to access system configurations and user settings.

| **Command / Syntax** | **Variable Type(s)** | **Action / Description** |
| --- | --- | --- |
| `VARIABLE=value` | Local (Shell) | Define or modify a local shell variable (not exported to child processes) |
| `export VARIABLE=value` | Environment (Exported) | Define & export a variable so it is available to child processes |
| `export VARIABLE` | Environment (Exported) | Export existing local variable to environment |
| `unset VARIABLE` | Local or Environment | Remove (unset) a variable, local or environment |
| `echo $VARIABLE` | Any | Display the value of a variable |
| `printenv` | Environment | List all environment variables |
| `printenv VARIABLE` | Environment | Display the value of a specific environment variable |
| `env` | Environment | Show environment variables, or run commands with modified environment |
| `set` | Local + Environment + Shell Internal | List all shell variables, environment variables, and shell functions |
| `export -p` | Environment | Print all exported variables in a reusable format |
| `declare -p` | Local (and Exported) | Print all local variables with attributes (use `declare -xp` for only exported) |
| `declare -x` | Environment | Print exported variables only |
| `compgen -v` | Local | List all local variable names |
| `compgen -e` | Environment | List all environment variable names |
| `typeset` (or `declare`) | Local + Environment | List variables and attributes |
| `env VARIABLE=value command` | Environment (Temporary) | Run a command with overridden temporarily environment variable |
| `PATH=$PATH:/new/path` | Local | Modify a local variable by appending to `PATH` (or other env var) |
| `export PATH` | Environment | Export a modified local variable to environment |
| `echo ${VARIABLE:-default}` | Any | Print variable or default value if variable is unset |

## Special Variable

| Variable | Meaning |
| --- | --- |
| `PATH` | Search paths for executable programs |
| `HOME` | User's home directory |
| `USER` | Current user |
| `PWD` | Present working directory |
| `LANG` | Locale and language settings |
| `LOGNAME` | Login name of the user |
| `TERM` | Terminal type |
| `IFS` | Internal Field Separator (Space, Tab, Newline) |
| `HISTCONTROL` |     |
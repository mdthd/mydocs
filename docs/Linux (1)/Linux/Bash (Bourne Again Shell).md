# Bash (Bourne Again Shell)

Text file containing sequence of commands

## Shebang

Shebang specifies which interpreter to be used to execute the script

`#` → sharp + `!` → bang = shebang

### Shebang example

```bash
#!/usr/bin/env bash
```

### Run Multiple Commands

| Symbol | Description | Syntax |
| --- | --- | --- |
| `&&` | Logical AND, If first command succeeds then next commands will get executed | `CMD1 && CMD2` |
| `\|` | Logical OR, if first command fails then next commands get executed | `CMD1 \| CMD2` |
| `;` | Command separator, All the commands will get executed in sequence irrespective of success or failures | `cmd1; cmd2; cmd3` |

### Testing Values and Strings

\[\[ … \]\]

\[\[ condition \]\]

Return 0 if condition is true

Return 1 if condition is false

#### Examples

| You want to check… | Use this |
| --- | --- |
| String is empty | `[ -z "$var" ]` |
| String is not empty | `[ -n "$var" ]` |
| Strings are the same | `[ "$a" = "$b" ]` |
| Strings are different | `[ "$a" != "$b" ]` |
| Numbers are equal | `[ "$a" -eq "$b" ]` |
| Numbers are different | `[ "$a" -ne "$b" ]` |
| Number is less than | `[ "$a" -lt "$b" ]` |
| Number is greater than | `[ "$a" -gt "$b" ]` |

### Testing Files

| Check Files | Syntax |
| --- | --- |
| is a file | `[ -e filename.txt ]` |
| is a regular file | `[ -f filename.txt ]` |
| is a directory | `[ -d directoryname ]` |
| is a executable | `[ -x filename ]` |
| is a readable file | `[ -r filename ]` |
| is a writable file | `[ -w filename ]` |

### Numeric Test

| Symbol | Description | Example | Equivalent forms |
| --- | --- | --- | --- |
| `-gt` | Greater than | `[[ “${num}“ -gt 29 ]]` | `(( num > 29 ))` |
| `-ge` | Greater than equals to | `[[ “${num}“ -ge 29 ]]` | `(( num >= 29 ))` |
| `-lt` | Lesser than | `[[ “${num}“ -gt 29 ]]` | `(( num < 29 ))` |
| `-le` | Lesser than equals to | `[[ “${num}“ -gt 29 ]]` | `(( num <= 29 ))` |
| `-eq` | Equals to | `[[ “${num}“ -eq 29 ]]` | `(( num == 29 ))` |
| `-ne` | Not Equals to | `[[ “${num}“ -ne 29 ]]` | `(( num != 29 ))` |

:::warning
Using `[[ expressions ]]` for comparing mathematical values sometimes may fail

That is trying

```bash
[[ "4" < "7" ]]; echo $?
[[ "40" < "7" ]]; echo $?
```

Both statements will return true, and exit codes will be 0
:::

### Complex conditions statements

#### Negating statements

If `file.txt` is not a file then the condition will be true

```bash
[[ ! -e file.txt ]]; echo $?
```

#### Using Logical And in conditions

To check if 2 conditions are true

```bash
[[ $num -gt 5 && $num -lt 10 ]]
```

## Statements in Bash

### `if` statement in bash

```bash
if command; then
# command to execute
fi
```

### `if` and `else` statement

```bash
if command; then
 # command to execute
else
 # command for else 
fi
```

### `elif` statement

```bash
if command1; then
# commands to execute
elif command2; then
# commands to execute
else
# commands to execute
fi
```

### Pattern Matching

`[[ “file.txt“ == *.txt ]]` will be true

`[[ “file.txt“ == “*.txt“ ]]` will be false

`[[ *.txt == “file.txt“ ]]` will be false

For more pattern matching refer https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html

### `case` statement

```bash
case "${variable}" in
    Pattern1)
        # commands for executing
        ;;
    Pattern2|Pattern3)
        # commands for executing
        ;;
    Pattern4)
        # Commands
        ;;
esac
```

## Loops in bash

### While loop

```bash
while command; do
  # commands to execute
done
```

```bash
while [[ condition ]]; do
  # commands to execute
done
```

```bash
counter=0
while (( counter < 10 )); do
  (( counter = counter + 1 ))
  echo "Counter = ${counter}"
done
```

#### Continue and break in while loop

By-passing a value while running `while` loop

```bash
counter=0
while (( counter < 10 )); do
  (( counter = counter + 1 ))
  if (( counter == 5 )); then
    continue
  fi
  echo "Counter = ${counter}"
done
```

This loop will print from 1 to 10 but bypass 5

```bash
counter=0
while (( counter < 10 )); do
  (( counter = counter + 1 ))
  if (( counter == 5 )); then
    break
  fi
  echo "Counter = ${counter}"
done
```

This loop will break at 5, means upto the value 5 it will run when the value is 5 loops will exit

### `for` loops

```bash
for [variable] in [elements]; do
  # commands
done
```

#### Example

```bash
for number in One Two; do
  echo $number
done
```

```bash
for number in 1 2 3 4 5 6 7 8 9; do
 echo ${number}
done
```

:::info
Continue and break will work in while loops and for loops
:::

#### Sequence statements

`{start..end}`

`{start..end..step}`

```
echo {1..9}
```

```bash
echo {5..1}
```

#### Command substitution in bash

```bash
for word in $(seq 1 9); do
echo ${word}
done
```

#### For Loop syntax `(( init; test; i++ ))`

- **init**: Executed one time at the beginning (Declaring Vaiable)
- **test**: Executed before each iteration (Evaluating condition)
- **after**: Executed after each iteration (Increment or decrement to variable)
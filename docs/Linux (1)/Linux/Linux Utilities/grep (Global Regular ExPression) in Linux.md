# grep (Global Regular ExPression) in Linux

## General user of grep

`[command with stdout] | grep pattern`

## Searching a file using grep

`grep -F [pattern] [file..]`

:::info
`-F` disables regular expressions
:::

`greo -F` is equivalent to `fgrep`

---

## Options for grep

### 🔍 **Basic Matching Options**

| Option | Purpose | Description | Example |
| --- | --- | --- | --- |
| `-i` | Case-insensitive search | Matches text regardless of case (e.g., "Hello" = "hello") | `grep -i "error" log.txt` |
| `-w` | Whole word match | Matches only whole words, not substrings | `grep -w "end" notes.txt` |
| `-x` | Exact line match | Matches lines that are exactly the same as the pattern | `grep -x "done" checklist.txt` |
| `-F` | Fixed string match | Treats pattern as a literal string (no regex interpretation) | `grep -F "a+b" file.txt` |
| `-E` | Extended regex | Enables extended regular expressions (like `egrep`) | `grep -E "cat \| dog” pets.txt` |

### 📁 **File and Directory Handling**

| Option | Purpose | Description | Example |
| --- | --- | --- | --- |
| `-r` / `-R` | Recursive search | Searches all files in a directory and its subdirectories | `grep -r "TODO" ./project` |
| `-l` | List matching files | Shows only filenames that contain matches | `grep -l "main" *.c` |
| `-L` | List non-matching files | Shows only filenames that do **not** contain matches | `grep -L "main" *.c` |

### 📊 **Output Formatting**

| Option | Purpose | Description | Example |
| --- | --- | --- | --- |
| `-n` | Show line numbers | Displays line numbers alongside matching lines | `grep -n "main" code.c` |
| `--color=auto` | Highlight matches | Highlights matched text in color (if supported by terminal) | `grep --color=auto "fail" log.txt` |
| `-c` | Count matches | Shows the number of matching lines per file | `grep -c "success" report.txt` |

### 🔄 **Context Control**

| Option | Purpose | Description | Example |
| --- | --- | --- | --- |
| `-A NUM` | Show lines after match | Displays NUM lines **after** each matching line | `grep -A 2 "error" log.txt` |
| `-B NUM` | Show lines before match | Displays NUM lines **before** each matching line | `grep -B 2 "error" log.txt` |
| `-C NUM` | Show lines around match | Displays NUM lines **before and after** each match | `grep -C 3 "error" log.txt` |

### 🔧 **Advanced Matching**

| Option | Purpose | Description | Example |
| --- | --- | --- | --- |
| `-v` | Invert match | Shows lines that **do not** match the pattern | `grep -v "debug" log.txt` |
| `-e` | Multiple patterns | Allows specifying multiple patterns to match | `grep -e "cat" -e "dog" pets.txt` |

---
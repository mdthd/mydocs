# Shell Expansion

## Types of Shell Expansions

1.  **Brace Expansion** `{}`
2.  **Tilde Expansion** `~`
3.  **Variable Expansion** `$VAR`
4.  **Command Substitution** `command` **or** `$(command)`
5.  **Arithmetic Expansion** `$((expression))`
6.  **Filename (Pathname) Expansion / Globbing** `* ? []`
7.  **Process Substitution** `<(command)` **and** `>(command)`

---

### 1\. Brace Expansion `{}`

| Use | Expression | Expands to |
| --- | --- | --- |
| Comma-Separated | {item1,item2,item3} | item1 item2 item3 |
| Number sequence | {1..5} | 1 2 3 4 5 |
| Character Sequence | {a..e} | a b c d e |
| Num Sequence with step | {1..10..2} | 1 3 5 7 9 |
| Reverse Num Sequence | {5..1} | 5 4 3 2 1 |
| Char Sequence with Step | {a..z..5} | a f k p u z |
| Nested brace expansion | {a,b}{1,2} | a1 a2 b1 b2 |
| Triple Nesting | {A,B}{1,2}{x,y} | A1x A1y A2x A2y B1x B1y B2x B2y |
| Combined brace expansion | file{1,2} | file1 file2 |
| Brace with Parenthesis | /home/{user1,user2}/docs | /home/user1/docs /home/user2/docs |

---

### **2\. Tilde Expansion** `~`

| Expression | Equivalent to | Expansion |
| --- | --- | --- |
| ~   | $HOME | /home/user |
| ~user |     | /home/user |
| ~root |     | /root |
| ~+  | $PWD |     |
| ~-  | $OLDPWD |     |
| ~user/Document |     | /home/user/Document |

---

### 3\. Variable Expansion `$VAR`

If Variable declared as `VAR='VALUE'`

| Variable Expression | Variable Expansion |     |
| --- | --- | --- |
| $VAR | VALUE |     |
| ${VAR} | VALUE |     |
| ${VAR:-NEWVAL} | NEWVAL | #( Variable value is not assigned) |
| ${VAR:=NEWVAL} | NEWVAL | #(Variable value will be assigned) |
| ${VAR:+NEWVAL} | NEWVAL | #(New Var value is printed if VAR is non empty) |
| ${VAR:?NEWVAL} | NEWVAL | #(New Var value is printed if var is empty prints to STD Err) |
| ${VAR:2} | LUE | Leaves first 2 chars and prints |
| ${VAR:2:2} | LU  | Leaves first 2 and prints next 2 |
| ${#VAR} | 5   | Prints VAR length |
| ${!VAR} |     | Prints variables variable |

Consider the variable `filename=archive.tar.gz`

| Var expression | VAR Expansion |     |
| --- | --- | --- |
| ${filename#\*.} | tar.gz | Remove shortest length of chars before pattern match |
| ${filename##\*.} | gz  | Remove longest length of chars before pattern match |
| ${filename%.\*} | archive.tar | Remove shortest char after the pattern match |
| ${filename%%.\*} | archive | Remove longest char after the pattern match |

---

### 4\. Command Execution `$(command)`

```bash
echo "This are home directory content: $(ls $HOME)"
```

---

### 5\. Arithmetic Expansion `$((arithmetic expressions))`

`a=2`, `b=3` , `c=5`

| Operation | Expression | Output |
| --- | --- | --- |
| Add | $((a+a)) | 5   |
| Sub | $((a-b)) | \-3 |
| Multiply | $((a\*b)) | 6   |
| Divide | $((a/b)) | 1   |
| Reminder | $((c%b)) | 2   |

---

### 6\. File Globbing

- `?(pattern)` → zero or one occurrence
- `*(pattern)` → zero or more
- `+(pattern)` → one or more
- `@(pattern)` → exactly one
- `!(pattern)` → anything except

| Pattern | Description |
| --- | --- |
| `*` | Matches any number of characters |
| `?` | Matches exactly one character |
| `[abc]` | Matches one of the characters `a`, `b`, `c` |
| `[a-z]` | Matches one character in range |
| `[!a]` | Matches anything except `a` |
| `{a,b,c}` | Expands to each item |
| `{1..5}` | Expands to range |
| `**` | Recursive match with `globstar` |
| `!(p)` | Anything but pattern |

---
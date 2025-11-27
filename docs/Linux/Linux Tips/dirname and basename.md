# dirname and basename

## `dirname` : Directory Name

This command will print the path of the directory in which file exists

```bash
dirname filename
```

## `basename` :

This command will print the filename that will not include the path

```bash
basename file-path
```

### To print the file extension only

```bash
filename='filename.txt'
```

Then run

```bash
echo "${filename#*.}"
```

### To print the file name without extension

```bash
filename='filename.txt'
```

```bash
echo "${filename%*.}"
```
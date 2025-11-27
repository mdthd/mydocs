# Math in Bash

## Calculating expression

Run `(( expression ))`

```bash
x=1
y=2
(( result = x + y ))
echo $result
```

### To evaluate the expression directly

```bash
echo "$((x+y)) is sum of x and y"
echo "$((x-y)) is the difference of x and y"
echo "$((x*y)) is the product of x and y"
echo "$((x/y)) is the quotient of x and y"
echo "$((x%y)) is the reminder of x and y"
```

### Declare integer type variable in bash

```bash
declare -i ivar
```

This command will make the `ivar` variable to hold only integer values

| Value assignment to `ivar` | Ivar will store |
| --- | --- |
| ivar=15 | `echo ${ivar}` → 15 |
| ivar=’15’ | `echo ${ivar}` → 15 |
| ivar=”15” | `echo ${ivar}` → 15 |
| ivar=15+x (if x is not defined) | `echo ${ivar}` → 15 |
| ivar=15+x (if x is defined as 12) | `echo ${ivar}` → 27 |
| ivar=’15+5’ | `echo ${ivar}` → 20 |

:::info
#### The Best Practice to write expression

`(( ivar = x + y ))` this is the best way

`ivar=$(( x + y ))`
:::

### Using read command to input integers

### Decimal number in bash

:::info
Bash does not know the decimals
:::

Using `bc` command bc = basic calculator

| Input | Output |
| --- | --- |
| `echo “5 + 6“ \| bc` | 11  |
| `echo “5.3 + 6.4“ \| bc` | 11.7 |
| `echo 'scale=4 15 / 13' \| bc` | 1.1538 |
| `echo “scale=2 $x / $y“ \| bc` |     |

## Using `awk` to evaluate expression

If we have a file like

```txt
2
3
4
4
5
3
4
5
6
```

Then to sum up the values

```bash
awk '{ sum += $1 } END { print sum}' file
```

### Print only first column

```bash
awk '{print $1}' filename
```

### Changing the delimiter using `-F`
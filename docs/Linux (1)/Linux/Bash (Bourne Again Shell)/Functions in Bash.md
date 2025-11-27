# Functions in Bash

Functions are code blocks that can be reused

### Define function

```bash
function_name() {
 # code blocks
}
```

```bash
function function_name {
 # code blocks
}
```

### Call function

```bash
function_name
```

### Variables in function

Variables are global

:::info
If a variable defined in function will be accessible outside the function

To define variable in a function that should only be accessible inside the function than

`local variable=value`
:::

### Get Data into function  

`echo “data“ | function_name`
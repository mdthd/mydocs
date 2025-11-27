# Arrays in Bash

Manage collection of entries

## Create Array

`array_name=value`

:::info
Every Bash variable is an array with single element
:::

`array_name=(val1 val2 val3 …)`

or

`declare -a fruits=(val1 val2 val3)`

## Access array

`echo ${fruit[0]}` or `echo ${fruit}`

## access last entries

`echo ${fruit[-1]}`

:::info
This will not work with array `echo $fruit[0]` always need to use `{` and `}`
:::

## Print the whole array

`echo ${fruit[@]}` or `echo ${fruit[*]}`

:::info
using variable `fruit[@]` is recommended  
This will print variables values with spaces as one string

But `fruit[*]` will print it as two different strings
:::

## Modifying values of array

`array[1]=’value’`

Modifying last element of array

`array[-1]=”value”`

## Array Operations

### Array Length

`echo "${#fruits[@]}"`

This will print the length of array

### Adding new element to array

`array+=(new_val)`

### Deleting element from array

`unset array[2]`

This will remove 3rd element; the next elements will not replace the removed element.

:::info
The deleted element will be empty and will not get replaced
:::

### Array slicing

IF array is `array=(value1 value2 value3 value4)`

Then printing a portion of array is array slicing

This can be done like this: `echo “${array[@]:1:2}“` this will print 2nd and 3rd element.

### Copy Array

`array_copy=(“${array[@]”)`

### Append an array

`array_append=(“${array[@]}” “val1” Val2” )`

### Append array in different position

`array_append=(“val1” val2 “${array[@]}” “val3”)`

### Copy Multiple arrays

`array_append=(“${array1[@]}” “${array2[@}}”)`

## Array in for loop

```bash
for element in "${array[@]}"; do
    echo "${element}"
done
```

## Array in select

```bash
select element in "${array[@]}" "quit"; do
    [[ "${fruit}" == "quit" ]] && break
    echo "${array}"
done
```
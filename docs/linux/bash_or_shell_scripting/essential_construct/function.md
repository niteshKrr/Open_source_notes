# Functions in Bash

Functions in Bash help in code reuse and modular programming. They allow for organizing scripts into manageable sections.

## 1. Defining and Calling a Function
A function is defined using the following syntax :-

```bash
function function_name() {
    # Commands
}
```
OR
```bash
function_name() {
    # Commands
}
```

### Example:
```bash
#!/bin/bash

function greet() {
    echo "Hello, ${1}!"
}

greet "World"
greet "User"
```
**Output:**
```
Hello, World!
Hello, User!
```

## 2. Function with Return Value
Bash functions can return values using `echo` or `return`.

### Example:
```bash
#!/bin/bash

add() {
    result=$(( ${1} + ${2} ))
    echo $result
}

sum=$(add 10 5)
echo "Sum: ${sum}"
```
**Output:**
```
Sum: 15
```

## 3. Function with Local Variables
Use `local` to declare function-specific variables.

### Example:
```bash
#!/bin/bash

demo_function() {
    local name="Bash"
    echo "This is a function in ${name}"
}

demo_function
```

## 4. Function with Return Statement
Functions can use `return` to provide an exit status (0 for success, non-zero for failure).

### Example:
```bash
#!/bin/bash

check_even() {
    if (( ${1} % 2 == 0 )); then
        return 0
    else
        return 1
    fi
}

check_even 4
if [ $? -eq 0 ]; then
    echo "Even number"
else
    echo "Odd number"
fi
```


## Summary
- Functions help organize and reuse code.
- Parameters are passed like script arguments: `${1}`, `${2}`, etc.
- Use `local` to limit variable scope.
- `return` can be used for exit codes, while `echo` returns values.
- Functions can be recursive for complex tasks.


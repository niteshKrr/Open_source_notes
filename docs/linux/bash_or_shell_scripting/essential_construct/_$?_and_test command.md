# Test command and $?


## 1. The `test` Command in Bash
The `test` command is used for evaluating conditions, such as checking file types, comparing values, and testing expressions.

### **Usage of `test` Command**
It can be used in three ways :-<br>

1. **Using `test` keyword:**  
   ```bash
   test condition
   ```
2. **Using `[ ]` (Square Brackets) - Equivalent to `test`:**  
   ```bash
   [ condition ]
   ```
3. **Using `[[ ]]` (Double Brackets) - Advanced version:**  
   ```bash
   [[ condition ]]
   ```

??? note "why we should use (Double Brackets) `[[ condition ]]` not (Square Brackets) `[ condition ]`"

    ```bash
    #! /bin/bash

    name1="lo ki"
    name2="lo ki"
    if [ ${name1} == ${name2} ]
    then
        echo "both strings are equal"
    fi
    ```
    > the above script gives you error like `too many arguments` after running.


    ```bash
    #! /bin/bash

    name1="lo ki"
    name2="lo ki"
    if [[ ${name1} == ${name2} ]]
    then
        echo "both strings are equal"
    fi
    ```
    > but the same code does not gives you error if you use (Double Brackets) `[[ condition ]]`

### **Examples**
#### **Testing Numbers**
```bash
#!/bin/bash
a=10
b=20

if [ ${a} -lt ${b} ]; then
    echo "${a} is less than ${b}"
fi
```

#### Numeric Comparison Operators
| Operator | Description |
|----------|------------|
| `-eq` | Equal to |
| `-ne` | Not equal to |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal to |
| `-le` | Less than or equal to |

#### **Testing Strings**
```bash
#!/bin/bash
str1="hello"
str2="world"

if [ "${str1}" = "${str2}" ]; then
    echo "Strings are equal"
else
    echo "Strings are not equal"
fi
```

#### String Comparison Operators
| Operator | Description |
|----------|------------|
| `=` | Strings are equal |
| `!=` | Strings are not equal |
| `-z` | String is empty |
| `-n` | String is not empty |


#### **Testing File Conditions**
```bash
#!/bin/bash
file="testfile.txt"

if [ -f "${file}" ]; then
    echo "${file} exists"
else
    echo "${file} does not exist"
fi
```

#### File Test Operators
| Operator | Description |
|----------|------------|
| `-f` | File exists and is a regular file |
| `-d` | File is a directory |
| `-e` | File exists |
| `-r` | File is readable |
| `-w` | File is writable |
| `-x` | File is executable |
| `-s` | File exists and is not empty |

---

## 2. The `$?` Variable in Bash
The `$?` variable holds the **exit status** of the last executed command.

### Exit Status Meaning
- `0` → Command executed **successfully** (true)
- `1-255` → Command **failed** (false)

### **Examples**
#### **Checking Success**
```bash
#!/bin/bash
ls /home
echo "Exit status: $?"
```
**Output (if successful):**
```
Exit status: 0
```

#### **Checking Failure**
```bash
#!/bin/bash
ls /nonexistent_directory
echo "Exit status: $?"
```
**Output (if the directory doesn’t exist):**
```
ls: cannot access '/nonexistent_directory': No such file or directory
Exit status: 2
```

#### **Using `$?` in an `if` Statement**
```bash
#!/bin/bash
mkdir test_directory

if [ $? -eq 0 ]; then
    echo "Directory created successfully"
else
    echo "Failed to create directory"
fi
```

#### **Checking Internet Connection**
```bash
#!/bin/bash
ping -c 1 google.com

if [ $? -eq 0 ]; then
    echo "Internet connection is working"
else
    echo "No internet connection"
fi
```

## Summary
- The `test` command (or `[ ]` and `[[ ]]`) is used for condition testing.
- `$?` stores the exit status of the last command.
- `0` means success, while non-zero values indicate failure.
- Useful for **error handling and debugging** in scripts.


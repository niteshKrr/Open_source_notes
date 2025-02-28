# Conditional Statements

Conditional statements in Bash allow scripts to make decisions based on conditions. They control the flow of execution depending on whether a condition evaluates to **true** or **false**.

---

## 1. `if` Statement
The `if` statement executes a block of code **only if** the condition is true.

### Syntax
```bash
if [ condition ]; then
    # Commands to execute if condition is true
fi
```

### Example
```bash
#!/bin/bash
num=10

if [ ${num} -gt 5 ]; then
    echo "Number is greater than 5"
fi
```

---

## 2. `if-else` Statement
The `if-else` statement allows executing an alternative block of code if the condition is false.

### Syntax
```bash
if [ condition ]; then
    # Commands if condition is true
else
    # Commands if condition is false
fi
```

### Example
```bash
#!/bin/bash
num=3

if [ ${num} -gt 5 ]; then
    echo "Number is greater than 5"
else
    echo "Number is less than or equal to 5"
fi
```

---

## 3. `if-elif-else` Statement
The `if-elif-else` statement is used when there are **multiple conditions** to check.

### Syntax
```bash
if [ condition1 ]; then
    # Commands if condition1 is true
elif [ condition2 ]; then
    # Commands if condition2 is true
else
    # Commands if no conditions are true
fi
```

### Example
```bash
#!/bin/bash
num=0

if [ ${num} -gt 0 ]; then
    echo "Number is positive"
elif [ ${num} -lt 0 ]; then
    echo "Number is negative"
else
    echo "Number is zero"
fi
```

---

## 4. `case` Statement
The `case` statement is used for **multiple-choice** conditions, similar to a `switch` statement in other languages.

### Syntax
```bash
case variable in
    pattern1)
        # Commands if pattern1 matches
        ;;
    pattern2)
        # Commands if pattern2 matches
        ;;
    *)
        # Default case if no pattern matches
        ;;
esac
```

### Example
```bash
#!/bin/bash
fruit="apple"

case ${fruit} in
    "apple")
        echo "You chose an apple"
        ;;
    "banana")
        echo "You chose a banana"
        ;;
    *)
        echo "Unknown fruit"
        ;;
esac
```

---

## 5. Ternary-Like `&&` and `||` Operators
Bash does not have a ternary operator (`condition ? true_value : false_value`), but you can use `&&` (AND) and `||` (OR) to achieve similar results.

### Syntax
```bash
[ condition ] && command_if_true || command_if_false
```

### Example
```bash
#!/bin/bash
num=10
[ ${num} -gt 5 ] && echo "Greater than 5" || echo "Less than or equal to 5"
```

---

## Summary
- `if`, `if-else`, and `if-elif-else` allow checking conditions.
- `case` is useful for multiple options.
- `&&` and `||` provide a shorthand for simple conditions.


# Loops in Bash Scripting

Loops in Bash allow executing a block of code multiple times until a certain condition is met. They are useful for automating repetitive tasks.

---

## 1. `for` Loop
The `for` loop iterates over a range, list, or command output.

### Syntax
```bash
for variable in list; do
    # Commands
done
```

### Example 1 :- Looping Through a List
```bash
#!/bin/bash

for fruit in apple banana cherry; do
    echo "Fruit: $fruit"
done
```

### Example 2 :- Looping Through a Range
```bash
#!/bin/bash

for i in {1..5}; do
    echo "Number: ${i}"
done
```

### Example 3 :- C-Style `for` Loop
```bash
#!/bin/bash

for ((i=1; i<=5; i++)); do
    echo "Iteration: ${i}"
done
```

---

## 2. `while` Loop
A `while` loop runs as long as a condition remains **true**.

### Syntax
```bash
while [ condition ]; do
    # Commands
done
```

### Example
```bash
#!/bin/bash

count=1
while [[ ${count} -le 5 ]]; do
    echo "Count: ${count}"
    ((count++))
done
```

---

## 3. `until` Loop
An `until` loop runs until a condition becomes **true** (opposite of `while`).

### Syntax
```bash
until [ condition ]; do
    # Commands
done
```

### Example
```bash
#!/bin/bash

num=1
until [[ ${num} -gt 5 ]]; do
    echo "Number: ${num}"
    ((num++))
done
```

---

## 4. `select` Loop (For Menus)
The `select` loop is used to create **interactive menus**.

### Syntax
```bash
select variable in list; do
    # Commands
done
```

### Example
```bash
#!/bin/bash

# PS3="Choose a fruit? "  # for replacing #?
echo "Choose a fruit:"
select fruit in Apple Banana Cherry; do
    case ${fruit} in
        Apple)
            echo "You chose Apple"
            break
            ;;
        Banana) 
            echo "You chose Banana"
            break
            ;;
        Cherry) 
            echo "You chose Cherry"
            break
            ;;
        *) 
            echo "Invalid option"
    esac
done
```

---

## Breaking and Continuing Loops
- `break` – Exits the loop entirely.<br>
- `continue` – Skips the current iteration and moves to the next.

### Example :- Using `break`
```bash
#!/bin/bash

for i in {1..10}; do
    if [[ ${i} -eq 5 ]]; then
        break
    fi
    echo "Number: ${i}"
done
```

### Example :- Using `continue`
```bash
#!/bin/bash

for i in {1..5}; do
    if [[ ${i} -eq 3 ]]; then
        continue
    fi
    echo "Number: ${i}"
done
```



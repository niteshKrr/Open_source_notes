# Nested Loops in Bash

**Nested loops** allow looping inside another loop, enabling complex iteration patterns in Bash scripting.

---

### Syntax
```bash
for var1 in list1; do
    for var2 in list2; do
        # Commands
    done
done
```

---

### Example :- Nested `for` Loops
```bash
#!/bin/bash

for i in {1..3}; do
    for j in {A..C}; do
        echo "Outer: ${i}, Inner: ${j}"
    done
done
```
**Output**
```
Outer: 1, Inner: A
Outer: 1, Inner: B
Outer: 1, Inner: C
Outer: 2, Inner: A
Outer: 2, Inner: B
Outer: 2, Inner: C
Outer: 3, Inner: A
Outer: 3, Inner: B
Outer: 3, Inner: C
```

---

### Example :- Nested `while` Loop
```bash
#!/bin/bash

outer=1
while [[ ${outer} -le 3 ]]; do
    inner=1
    while [[ ${inner} -le 2 ]]; do
        echo "Outer: ${outer}, Inner: ${inner}"
        ((inner++))
    done
    ((outer++))
done
```

---

### Combining `for` and `while` Loops
```bash
#!/bin/bash

for i in {1..2}; do
    count=1
    while [[ ${count} -le 3 ]]; do
        echo "For Loop: ${i}, While Loop: ${count}"
        ((count++))
    done
done
```

---


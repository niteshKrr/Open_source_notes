# Important To Know :flushed:

## Difference Between `$*` and `$#` in Bash

| Feature    | `$*`  | `$#`  |
|------------|------|------|
| Expands to | All arguments as a **single string** | Total **count** of arguments |
| Behavior when quoted (`"$*"`) | Treats all arguments as **one string** (`"arg1 arg2 arg3"`) | N/A |
| Example Output | `"arg1 arg2 arg3"` | `3` |

📌 **Use `$#`** when you need to check how many arguments were passed.  

---

## Difference Between `$*` and `$@` in Bash

| Feature    | `$*`  | `$@`  |
|------------|------|------|
| Expands to | All arguments as a **single string** when quoted (`"$*"`) | Each argument as **separate strings** when quoted (`"$@"`) |
| Behavior when unquoted | Expands arguments like `$1 $2 $3 ...` | Expands arguments like `$1 $2 $3 ...` |
| Behavior when quoted (`"$*"`) | Treats all arguments as **one string** (`"arg1 arg2 arg3"`) | Treats each argument as **separate strings** (`"arg1" "arg2" "arg3"`) |
| Use Case | Rarely used, can cause issues with argument separation | Preferred for iterating over arguments while maintaining individual argument boundaries |

📌 **Use `$@` in loops** instead of `$*` to preserve argument separation.


### Code Examples

### Using `$*`
```bash
#!/bin/bash
echo "Using \$*"
for arg in "$*"; do
    echo "Arg: $arg"
done
```
**Output:**
```
Arg: arg1 arg2 arg3
```

### Using `$@`
```bash
#!/bin/bash
echo "Using \$@"
for arg in "$@"; do
    echo "Arg: $arg"
done
```
**Output:**
```
Arg: arg1
Arg: arg2
Arg: arg3
```

🔹 **Notice** how `$*` treats all arguments as one, whereas `$@` preserves argument separation.


---



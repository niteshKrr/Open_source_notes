# Debugging Shell Scripts

## 1. Using `-x` Option (Execution Trace)
The `-x` option prints each command before execution, helping trace issues.

### **Enable Debugging**
```bash
#!/bin/bash
set -x  # Enable debugging

echo "Hello, World!"
ls /nonexistent_directory  # This will cause an error
set +x  # Disable debugging
```

### **Run the script:**
```bash
bash -x script.sh
```

---

## 2. Using `-v` Option (Verbose Mode)
The `-v` option prints each command **before execution**, but without expansion.

### **Enable Verbose Mode**
```bash
#!/bin/bash
set -v  # Enable verbose mode

echo "Running script..."
date
set +v  # Disable verbose mode
```

### **Run the script:**
```bash
bash -v script.sh
```

---

## 3. Using `set -e` (Exit on Error)
The `set -e` command forces the script to **exit immediately** if any command fails.

### **Example:**
```bash
#!/bin/bash
set -e  # Exit script if any command fails

echo "Starting..."
ls /nonexistent_directory  # Script will exit here

echo "This won't execute"
```

---

## 4. Using `trap` for Error Handling
`trap` allows running a custom command when the script encounters an error.

### **Example:**
```bash
#!/bin/bash
trap 'echo "Error on line $LINENO"' ERR

ls /nonexistent_directory  # Error occurs here
echo "This message might not be printed."
```

---

## 5. Checking Exit Status (`$?`)
Every command returns an **exit status**. `0` means success, any other number means failure.

### **Example:**
```bash
#!/bin/bash
echo "Checking command status..."
ls /nonexistent_directory

if [[ $? -ne 0 ]]; then
    echo "Command failed!"
fi
```

---

## Summary

✅ **`-x`** – Execution tracing  
✅ **`-v`** – Verbose mode  
✅ **`set -e`** – Exit on error  
✅ **`trap`** – Custom error handling  
✅ **`$?`** – Exit status check  



# Read Command & Command-Line Arguments

## 1. Read Command

The `read` command is used to take input from user in Bash scripts.

### **Basic Usage**
```bash
#!/bin/bash
echo "Enter your name: "
read name
echo "Hello, $name!"
```
- Prompts the user for input.
- Stores the input in the variable `name`.

### **Reading Multiple Values**
```bash
#!/bin/bash
echo "Enter two values: "
read var1 var2
echo "You entered: $var1 and $var2"
```
- Reads multiple values separated by spaces.

### **Silent Input (Password Entry)**
```bash
#!/bin/bash
echo "Enter password: "
read -s password
echo "Password received."
```
- The `-s` flag hides the input for secure password entry.

### **Using a Prompt in Read Command**
```bash
read -p "Enter your age: " age
echo "You entered: $age"
```
- The `-p` flag allows displaying a prompt message before input.

### **Setting a Timeout for Input**
```bash
read -t 5 -p "Enter your name within 5 seconds: " name
echo "Hello, $name!"
```
- The `-t` flag sets a timeout in seconds.

### **Providing a Default Value**
```bash
read -p "Enter your name (default: John): " name
name=${name:-John}
echo "Hello, $name!"
```
- Uses a default value if no input is given.

### **Restricting Input to a Single Character**
```bash
read -n 1 -p "Press any key to continue..." key
echo "You pressed: $key"
```
- The `-n` flag restricts input to a single character.

### **Reading from a File**
```bash
while read line; do
    echo "$line"
done < file.txt
```
- Reads each line from `file.txt` and prints it.


---


## 2. Command-Line Arguments

Command-line arguments allow users to pass data to a Bash script when executing it.

### **Basic Usage**
When running a script, arguments are passed after the script name:
```bash
./script.sh arg1 arg2 arg3
```

### **Accessing Command-Line Arguments**
Bash provides special variables to access arguments:

| Variable | Description |
|----------|-------------|
| `$0` | Script name like `./script.sh` |
| `$1, $2, ...` | Positional parameters (arguments) |
| `$#` | Number of arguments passed |
| `$@` | All arguments as separate strings |
| `$*` | All arguments as a single string |
| `$$` | Process ID of the script |
| `$?` | Exit status of the last executed command |

### **Example Script**
```bash
#!/bin/bash
echo "Script name: ${0}"
echo "First argument: ${1}"
echo "Second argument: ${2}"
echo "Total arguments: $#"
```
#### **Run the script:**
```bash
./script.sh Hello World
```
#### **Output:**
```
Script name: ./script.sh
First argument: Hello
Second argument: World
Total arguments: 2
```

### **Looping Through Arguments**
```bash
#!/bin/bash
echo "All arguments:"
for arg in "$@"; do
    echo "$arg"
done
```
#### **Output if run as:**
```bash
./script.sh apple banana cherry
```
```
All arguments:
apple
banana
cherry
```

### **Difference Between `$@` and `$*`**
- `$@` treats arguments as separate strings.
- `$*` treats all arguments as a single string.

Example:
```bash
#!/bin/bash
echo "Using \$@"
for arg in "$@"; do
    echo "$arg"
done

echo "Using \$*"
for arg in "$*"; do
    echo "$arg"
done
```
#### **Run the script:**
```bash
./script.sh "one two" three
```
#### **Output:**
```
Using $@
one two
three

Using $*
one two three
```





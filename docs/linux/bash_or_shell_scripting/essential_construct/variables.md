# Variables


A **variable** in Bash is a placeholder for storing data, which can be referenced and manipulated throughout a script.

## Types of Variables in Bash

### 1. **User-Defined Variables**
- Created by the user for storing values.
- No spaces around `=` when assigning values.
- Example:
  ```bash
  name="Alice"
  echo "Hello, $name!"
  ```

### 2. **System Variables**
- A system variable in Bash (or any Unix-like system) is a **predefined environment variable** that holds information about the system, user, or shell session. These variables are usually uppercase and are available globally in the shell environment.

**Common System Variables**

| Variable | Description |
|----------|-------------|
| `$HOME` | User's home directory |
| `$USER` | Current logged-in username |
| `$PATH` | Directories searched for executables |
| `$SHELL` | Default shell (e.g., `/bin/bash`) |
| `$PWD` | Current working directory |
| `$OLDPWD` | Previous working directory |
| `$UID` | User ID of the current user |
| `$HOSTNAME` | Name of the system (host) |
| `$LANG` | System language setting |
| `$LOGNAME` | Login name of the user |
| `$TERM` | Type of terminal in use |

- Example:
  ```bash
  echo "User: $USER"
  echo "Home Directory: $HOME"
  ```

### 3. **Special Variables**
- `$?` - Exit status of last command.
- `$$` - Process ID of the script.
- `$#` - Number of arguments passed.
- `$@` - All arguments as separate words.
- Example:
  ```bash
  echo "Script PID: $$"
  echo "Number of arguments: $#"
  ```

### 4. **Readonly Variables**
- Cannot be modified after assignment.
- Example:
  ```bash
  readonly PI=3.1415
  echo "Value of PI: $PI"
  ```

### 5. **Local Variables**
- Defined within a function and accessible only inside it.
- Example:
  ```bash
  my_function() {
      local local_var="I am local"
      echo "$local_var"
  }
  my_function
  ```

### 6. **Unsetting Variables**
- Removes a variable from memory.
- Example:
  ```bash
  name="Alice"
  unset name
  echo "Name: $name"  # Will print an empty value
  ```


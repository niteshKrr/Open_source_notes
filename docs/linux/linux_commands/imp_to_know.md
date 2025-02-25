# Important To Know

## 1.Environment Variables

**Environment variables** are key-value pairs that define system-wide or user-specific configurations. These variables influence how processes and applications behave in the shell.

### **Viewing Environment Variables**
```sh
printenv
```
> Displays all environment variables.


### **Common Environment Variables**
| Variable  | Description |
|-----------|------------|
| `$PATH`   | Directories where executables are searched for commands |
| `$USER`   | Current logged-in user |
| `$SHELL`  | Default shell being used |
| `$PWD`    | Current working directory |

### **Setting Environment Variables**

#### **Temporarily (valid for the session only)**
```sh
export MY_VAR="Hello World"
```
> Sets `MY_VAR` for the current session.

#### **Permanently (valid even after logout)**
Add the following line to `~/.bashrc`
```sh
export MY_VAR="Hello World"
```

---

## 2. Aliases

An **alias** is a shortcut for a command or a series of commands, allowing you to type less and work efficiently.

### **Creating an Alias**
```sh
alias ll="ls -lah"
```
> Now typing `ll` runs `ls -lah` (detailed directory listing).

### **Viewing Existing Aliases**
```sh
alias
```
> Displays all defined aliases.

### **Removing an Alias**
```sh
unalias ll
```
> Deletes the alias `ll`.

### **Making Aliases Permanent**

To keep an alias after logout, add it to `~/.bashrc`
```sh
echo 'alias ll="ls -lah"' >> ~/.bashrc
```
Then, apply the changes:
```sh
source ~/.bashrc
```

---

## 3.`$PATH` in Linux  


`$PATH` is an **environment variable** that stores a list of directories where the system searches for executable files when you enter a command in the terminal. It determines which programs can be run without specifying their full path.  

### **Viewing the `$PATH` Variable**  
To see your current `PATH`, run:  
```sh
echo $PATH
```
> This displays a colon-separated list of directories.  

#### **Example Output:**  
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```
Each directory in this list is checked in order when you type a command.  

### **How `$PATH` Works?**  
- If you type `ls`, the system looks in each directory listed in `$PATH` until it finds `/bin/ls`.  
- If the command is not in any of the directories, you'll see:  
  ```
  command not found
  ```

### **Temporarily Adding a Directory to `$PATH`**  
```sh
export PATH=$PATH:/home/user/my_scripts
```
> Adds `/home/user/my_scripts` to `$PATH` for the current session.  

### **Permanently Adding a Directory to `$PATH`**  
To make it permanent, add the line to `~/.bashrc`  
```sh
echo 'export PATH=$PATH:/home/user/my_scripts' >> ~/.bashrc
source ~/.bashrc
```

### **Key Points**  
✔ `$PATH` stores directories where the system looks for executable files.  
✔ Commands in `$PATH` can be run from anywhere.  
✔ You can modify `$PATH` to include custom directories.  

---

## 4. Cron Command in Linux

`cron` is a **time-based job scheduler** in Linux that allows users to **automate tasks** at scheduled intervals. It is useful for running scripts, backups, system maintenance, and more.

### What is `crontab`?
`crontab` (cron table) is a file that stores scheduled jobs for a user or system.

### **Viewing the Current Cron Jobs**
```sh
crontab -l
```
> Displays the list of scheduled jobs for the current user.

### **Editing the Cron Jobs**
```sh
crontab -e
```
> Opens the cron editor to add or modify scheduled tasks.

### Cron Job Syntax
A cron job follows this format:
```sh
MIN HOUR DOM MON DOW COMMAND
```

| Field | Description |
|--------|-------------|
| `MIN`  | Minute (0 - 59) |
| `HOUR` | Hour (0 - 23) |
| `DOM`  | Day of Month (1 - 31) |
| `MON`  | Month (1 - 12) |
| `DOW`  | Day of the Week (0 - 7, where 0 and 7 = Sunday) |
| `COMMAND` | The script or command to execute |

---

### Examples

```sh
0 2 * * * /home/user/myscript.sh
```
> Run a Script Every Day at 2 AM

```sh
*/5 * * * * echo "Hello, World!" >> /home/user/log.txt
```
> Run a Command Every 5 Minutes

```sh
0 10 * * 1 /home/user/weekly_report.sh
```
> Run a Task Every Monday at 10 AM

```sh
0 0 1 * * /home/user/monthly_cleanup.sh
```
> Run a Task on the 1st of Every Month at Midnight

```sh
crontab -r
```
> Deletes all scheduled jobs for the current user.


---

### Cron Special Keywords

| Keyword  | Equivalent To |
|----------|--------------|
| `@reboot`  | Runs once at system startup |
| `@hourly`  | Runs every hour (`0 * * * *`) |
| `@daily`   | Runs once a day (`0 0 * * *`) |
| `@weekly`  | Runs once a week (`0 0 * * 0`) |
| `@monthly` | Runs once a month (`0 0 1 * *`) |
| `@yearly`  | Runs once a year (`0 0 1 1 *`) |

---



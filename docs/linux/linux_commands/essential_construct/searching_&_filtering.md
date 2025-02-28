# Searching and filtering Commands

## 1. `grep` Command in Linux

### Description
The `grep` command is used to **search for patterns** within files or output. It scans each line and prints matching results, making it useful for filtering text data.

### Syntax
```sh
grep [options] pattern [file]
```
- `pattern` – The text or regular expression to search for.<br>
- `file` – The file where the search is performed (optional).

### Common Options
| Option | Description |
|--------|------------|
| `-i`   | Ignore case sensitivity |
| `-r`   | Recursively search directories |
| `-n`   | Show line numbers with matching lines |
| `-c`   | Count the number of matching lines |

### Examples

```sh
grep "error" logfile.txt
```
> Searches for the word "error" in `logfile.txt` and displays matching lines.

```sh
grep -i "warning" logfile.txt
```
> Searches for "warning" in `logfile.txt`, ignoring case differences.

```sh
grep -v "success" logfile.txt
```
> Shows all lines that **do not** contain "success".

```sh
grep "hello" *.txt
```
> Searches for "hello" in all `.txt` files in the directory.

```sh
grep -c "error" logfile.txt
```
> Counts the number of lines containing "error" in `logfile.txt`.

```sh
grep -r "TODO" /home/user/projects
```
> Searches for "TODO" in all files within `/home/user/projects`.

---


## 2. `find` Command in Linux

### Description
The `find` command is used to **search for files and directories** in a directory hierarchy based on various criteria such as name, size, type, and permissions.

### Syntax
```sh
find [path] [expression] [actions]
```
- `path` – The directory where the search begins.<br>
- `expression` – Search criteria (e.g., name, type, size).<br>
- `actions` – What to do with matching files (e.g., delete, print).

### Common Options
| Option | Description |
|--------|------------|
| `-name` | Search by file name (case-sensitive) |
| `-iname` | Search by file name (case-insensitive) |
| `-type` | Search by file type (`f` for file, `d` for directory) |
| `-size` | Search by file size (e.g., `+100M` for files larger than 100MB) |
| `-exec` | Execute a command on found files |
| `-delete` | Delete matching files |

### Examples

```sh
find /home/user -name "document.txt"
```
> Searches for `document.txt` inside `/home/user` and its subdirectories.

```sh
find /home/user -iname "document.txt"
```
> Searches for `document.txt` without case sensitivity.

```sh
find /home/user -type d
```
> Lists all directories inside `/home/user`.

```sh
find /var/log -size +100M
```
> Finds all files in `/var/log` larger than 100MB.

```sh
find /home/user -name "*.log" -exec rm {} \;
```
> Finds and deletes all `.log` files inside `/home/user`.

```sh
find /home/user -type f -empty -delete
```
> Deletes all empty files inside `/home/user`.

---

💡 **Tip:** Use `find` with `grep` to refine searches!
```sh
find /etc -type f | grep "config"
```
> Finds files containing "config" in their path.

---

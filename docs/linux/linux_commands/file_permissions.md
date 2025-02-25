# File Permissions Commands

## 1. `chmod` Command

### Description
The `chmod` command is used to **change file and directory permissions** in Linux. It allows users to modify read, write, and execute permissions for the owner, group, and others.

### Syntax
```sh
chmod [options] mode file
```
- `mode` – Specifies the permission change (symbolic or numeric).<br>
- `file` – The file or directory to modify.

### Permission Types
| Permission | Symbol | Numeric Value |
|------------|--------|---------------|
| Read       | `r`    | `4`           |
| Write      | `w`    | `2`           |
| Execute    | `x`    | `1`           |

### Modes of Using `chmod`

### 1️. Numeric Mode
Permissions are set using a three-digit octal number:
```sh
chmod 755 file.txt
```
> Sets `rwxr-xr-x` (Owner: read, write, execute; Group: read, execute; Others: read, execute).

### 2️. Symbolic Mode
Modify permissions using `+`, `-`, or `=` operators:
```sh
chmod u+x file.sh
```
> Adds execute (`x`) permission for the owner (`u`).

```sh
chmod g-w file.txt
```
> Removes write (`w`) permission for the group (`g`).

```sh
chmod o=r file.txt
```
> Sets read (`r`) permission only for others (`o`).

### Special Permissions
| Special Bit | Symbol | Description |
|-------------|--------|-------------|
| Set UID     | `u+s`  | Execute as the file owner |
| Set GID     | `g+s`  | Execute as the group owner |
| Sticky Bit  | `o+t`  | Restricts deletion in shared directories |

### 3️. Applying Special Permissions
```sh
chmod u+s script.sh
```
> Sets **Set UID** (runs as file owner).

```sh
chmod g+s shared_folder
```
> Sets **Set GID** (files inherit group ownership).

```sh
chmod o+t /tmp
```
> Enables the **sticky bit** (only owners can delete their files).

### Examples

### 4️. Grant Full Permissions to Owner, Read/Execute to Others
```sh
chmod 750 script.sh
```

### 5. Give Everyone Full Permissions
```sh
chmod 777 public_file
```

---
💡 **Tip:** Use `chmod -R` to change permissions recursively!
```sh
chmod -R 755 my_folder
```
> Sets `755` permissions for all files and directories inside `my_folder`.


---

## 2. `chown`Command

### Description
The `chown` command in Linux is used to **change the ownership** of files and directories. It allows administrators or users with the necessary permissions to modify the owner and group associated with a file.

### Syntax
```sh
chown [OPTIONS] [OWNER][:GROUP] FILE
```
- `OWNER` – New owner of the file.<br>
- `GROUP` – New group of the file (optional, prefixed with `:`).<br>
- `FILE` – Target file or directory.

### Common Options
| Option | Description |
|--------|------------|
| `-R`   | Recursively change ownership of directories and files inside them |
| `-c`   | Show output only for changed files |
| `-v`   | Display details of the ownership change |
| `--reference=FILE` | Use the owner of another file as a reference |

### Examples

```sh
chown user1 file.txt
```
> Changes the owner of `file.txt` to `user1`.

```sh
chown user1:group1 file.txt
```
> Changes the owner to `user1` and group to `group1`.

```sh
chown :group1 file.txt
```
> Assigns `group1` as the group owner of `file.txt`.

```sh
chown -R user1:group1 /home/user1
```
> Changes ownership of `/home/user1` and all files inside it.

```sh
chown --reference=existing_file new_file
```
> Assigns `new_file` the same ownership as `existing_file`.


## Related Commands
- **`ls -l`** – View file permissions.
- **`umask`** – Set default permissions for new files.


---
💡 **Tip:** Use `sudo` before `chown` if you need administrative privileges!
```sh
sudo chown user1:group1 file.txt
```
> Runs the command with root privileges to avoid permission errors.


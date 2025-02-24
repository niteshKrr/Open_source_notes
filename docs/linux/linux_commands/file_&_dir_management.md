# File & Directory Management Commands

## 1. `man` - Manual Pages

### Syntax
```sh
man [command_name]
```

### Description
The `man` command displays the manual (help documentation) for a specified Linux command. It provides detailed information, including syntax, options, examples, and descriptions.

### Example Usage
```sh
man ls
```
> Shows documentation for the `ls` command.

---

## 2. `ls` - List Directory Contents

### Syntax
```sh
ls [options] [directory]
```

### Description
The `ls` command lists files and directories in the current or specified directory.

### Common Options
| Option | Description |
|--------|------------|
| `-a`   | Show all files, including hidden ones |
| `-l`   | Display detailed file information |
| `-h`   | Show file sizes in human-readable format |
| `-t`   | Sort files by modification time |
| `-r`   | Reverse the order of output |

### Examples
```sh
ls -lh
```
> Lists files with human-readable sizes.


---

## 3. `pwd` - Print Working Directory

### Syntax
```sh
pwd
```

### Description
The `pwd` command prints the full path of the current working directory.

### Example
```sh
pwd
```
> Outputs: `/home/user/documents`

---

## 4. `cd` - Change Directory

### Syntax
```sh
cd [directory]
```

### Description
The `cd` command is used to navigate between directories.

### Common Usage
| Command | Description |
|---------|------------|
| `cd /path/to/directory` | Moves to the specified directory |
| `cd ..` | Moves to the previous directory |
| `cd ~` | Moves to the home directory |
| `cd /` | Moves to the root directory |

### Examples
```sh
cd /var/log
```
> Changes to the `/var/log` directory.

```sh
cd ..
```
> Moves to the previous directory.

---

## 5. `mkdir` - Create Directories

### Syntax
```sh
mkdir [options] directory_name
```

### Description
The `mkdir` command creates new directories.

### Common Options
| Option | Description |
|--------|------------|
| `-p`   | Create parent directories if they don’t exist |

### Examples
```sh
mkdir my_folder
```
> Creates a directory named `my_folder`.

```sh
mkdir -p parent/child
```
> Creates `parent` and `child` directories if they do not exist.

---

## 6. `touch` - Create or Update Files

### Syntax
```sh
touch [options] filename
```

### Description
The `touch` command creates an empty file or updates the timestamp of an existing file.

### Example Usage
```sh
touch myfile.txt
```
> Creates an empty file named `myfile.txt`.


---

## 7. `file` - Determine File Type

### Syntax
```sh
file [options] filename
```

### Description
The `file` command determines the type of a file based on its content, rather than its extension.

### Example Usage
```sh
file myfile.txt
```
> Outputs something like `ASCII text` if it's a text file.

---


## 8. `rm` - Remove Files and Directories

### Syntax
```sh
rm [options] [file/directory]
```

### Description
The `rm` command is used to **delete files and directories**.

### Common Options
| Option | Description |
|--------|------------|
| `-r`   | Remove directories and their contents recursively |
| `-f`   | Force delete files without confirmation |

### Example Usage
```sh
rm file.txt
```
> Deletes `file.txt`.

```sh
rm -rf my_folder
```
> Deletes `my_folder` and all its contents recursively and forcefully.

---

## 9. `mv` - Move or Rename Files and Directories

### Syntax
```sh
mv [source] [destination]
```

### Description
The `mv` command is used to **move or rename** files and directories.

### Example Usage
```sh
mv oldname.txt newname.txt
```
> Renames `oldname.txt` to `newname.txt`.

```sh
mv file.txt /home/user/Documents/
```
> Moves `file.txt` to the `/home/user/Documents/` directory.

---

## 10. `cp` - Copy Files and Directories

### Syntax
```sh
cp [options] [source] [destination]
```

### Description
The `cp` command is used to **copy files and directories**.


### Example Usage
```sh
cp file.txt backup.txt
```
> Copies `file.txt` to `backup.txt`.

```sh
cat abc.txt >> pqr.txt
```
> Copies `abc.txt` to `pqr.txt` without replacing the content inside `pqr.txt`.

```sh
cp -r my_folder/ backup_folder/
```
> Copies `my_folder` and its contents to `backup_folder`.

---

## Related Commands
- **`tree`** – Display directory structure in a tree format
- **`find`** – Search for files and directories



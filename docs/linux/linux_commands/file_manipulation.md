# File Manipulation Commands


## 1. `cat` - Concatenate and Display Files

### Syntax
```sh
cat [options] [file]
```

### Description
The `cat` command is used to **view, create, and concatenate** files.


### Example Usage

```sh
cat file.txt
```
> Displays the content of `file.txt`.

```sh
cat file1.txt file2.txt
```
> Displays the content of both `file1.txt` and `file2.txt` sequentially.

```sh
cat > newfile.txt
Hello, world!
CTRL + D
```
> Creates `newfile.txt` and writes text into it. Press `CTRL + D` to save and exit.

```sh
cat >> existingfile.txt
New content here.
CTRL + D
```
> Adds new content at the end of `existingfile.txt` without deleting the existing data.

```sh
cat file1.txt > file2.txt
```
> Copies `file1.txt` content into `file2.txt`, overwriting it.

```sh
cat file1.txt >> file2.txt
```
> Appends `file1.txt` content to `file2.txt` without overwriting.



---

## 2. `nano` - Text Editor

### Syntax
```sh
nano [filename]
```

### Description
The `nano` is a simple, **user-friendly text editor** used for modifying text files.

### Basic Controls
| Shortcut | Function |
|----------|----------|
| `CTRL + O` | Save file |
| `CTRL + X` | Exit editor |
| `CTRL + K` | Cut a line |
| `CTRL + U` | Paste a line |

### Example Usage
```sh
nano myfile.txt
```
> Opens `myfile.txt` with `nano` for editing.


---

## Related Commands
- **`vim`** – A more advanced text editor
- **`echo`** – Prints text to the terminal or file
- **`less`** – View file content one page at a time
- **`head`** – Display the first few lines of a file
- **`tail`** – Show the last few lines of a file

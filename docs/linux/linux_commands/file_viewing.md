# File Viewing Commands


## 1. `head` - Display First Few Lines of a File

### Syntax
```sh
head [options] [file]
```

### Description
The `head` command **displays the first 10 lines of a file by default**.

### Examples
```sh
head file.txt
```
> Displays the first 10 lines of `file.txt`.

```sh
head -n 5 file.txt
```
> Displays the first 5 lines of `file.txt`.

---

## 2. `tail` - Display Last Few Lines of a File

### Syntax
```sh
tail [options] [file]
```

### Description
The `tail` command **displays the last 10 lines of a file by default**.

### Examples
```sh
tail file.txt
```
> Displays the last 10 lines of `file.txt`.

```sh
tail -n 5 file.txt
```
> Displays the last 5 lines of `file.txt`.


---

## 3. `less` - View Large Files with Scrolling

### Syntax
```sh
less [file]
```

### Description
The `less` command allows **viewing large files page by page**.

### Examples
```sh
less file.txt
```
> Opens `file.txt` for viewing with scrolling.

```sh
less +G file.txt
```
> Opens `file.txt` at the end (like `tail`).

---

## 4. `more` - View File Content Page by Page

### Syntax
```sh
more [file]
```

### Description
The `more` command is used to **view file content one page at a time**.

### Examples
```sh
more file.txt
```
> Displays `file.txt` page by page.

---

## 6. `nl` - Number Lines in a File

### Syntax
```sh
nl [file]
```

### Description
The `nl` command **displays a file with numbered lines**.

### Examples
```sh
nl file.txt
```
> Displays `file.txt` with line numbers.

---

## Related Commands
- **`find`** – Search for files and directories
- **`locate`** – Find files by name
- **`tac`** – Display file content in reverse order
- **`wc`** – Count words, lines, and characters in a file


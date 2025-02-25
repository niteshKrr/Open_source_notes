# Pipe Operator

The **pipe operator (`|`)** in Linux is used to pass the output of one command as input to another command. This allows **chaining multiple commands** together to perform complex operations efficiently.

## Syntax
```sh
command1 | command2
```
`command1` produces output, the output of `command1` is passed as input to `command2`.

## Examples

```sh
sort file.txt | head -n 5
```
> Sorts `file.txt` and then displays only the first 5 lines.

```sh
ls -1 | wc -l
```
> Lists files (`ls -1`), then counts the lines (`wc -l`), giving the total number of files.

```sh
cat file.txt | grep "keyword"
```
> Displays only the lines containing "keyword" from `file.txt`.


## Benefits of Using Pipes
✅ Avoids creating temporary files  
✅ Increases efficiency by combining commands  
✅ Simplifies complex tasks  


---

💡 **Tip:** Use multiple pipes to chain more than two commands together!

```sh
ls -l | grep "txt" | wc -l
```
> Finds and counts the number of `.txt` files in a directory.

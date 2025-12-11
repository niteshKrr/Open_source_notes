# Conditions & Loops

## 1. Conditions

Conditions let your program make decisions.

Syntax

```python
if condition:
    # code
elif another_condition:
    # code
else:
    # code
```

✔ Example

```python
age = 18

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

### Short-hand If-Else (Ternary Operator)

You can write an entire if-else in one line.

✔ Example

```python
x = 10
result = "Positive" if x > 0 else "Negative"
print(result)
```

### pass statement

- `if` statements cannot be empty, but `if` you for some reason have an `if` statement with no content, put in the pass statement to avoid getting an error.

- The `pass` statement is a null operation - nothing happens when it executes. It serves as a placeholder.


```python
a = 33
b = 200

if b > a:
  pass
```

### Match Statement

- Instead of writing **many** `if..else` statements, you can use the `match` statement.
- The `match` statement selects one of many code blocks to be executed.

Syntax

```python
match expression:
  case x:
    code block
  case y:
    code block
  case z:
    code block
```

✔ Example

```python
day = 4
match day:
  case 1:
    print("Monday")
  case 2:
    print("Tuesday")
  case 3:
    print("Wednesday")
  case 4:
    print("Thursday")
  case 5:
    print("Friday")
  case 6:
    print("Saturday")
  case 7:
    print("Sunday")
```

---

## 2. Loops

Loops repeat a block of code multiple times.

### 1. For Loop

- Used when you know how many times to repeat.


```python
for i in range(5):
    print(i)
```

Output:

```python
0 1 2 3 4
```

- A for loop is used for iterating over a sequence (that is either a list, a tuple, a dictionary, a set, or a string).

```python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
  print(x)
```

### ✔ range, enumerate, and zip

??? "range()"

    `range()` is used to generate a sequence of numbers.

    ```python
    for i in range(10):
        print(i)
    ```


??? "enumerate()"

    `enumerate()` gives you both index and value when looping through a list.

    ```python
    for i, j in enumerate(['a', 'b', 'c']):
        print(i, j)
    ```


??? "zip()"

    `zip()` combines 2 (or more) lists element-by-element.

    ```python
    for i, j in zip(['a', 'b', 'c'], ['x', 'y', 'z']):
        print(i, j)
    ```

    So the loop runs like:

    - i='a', j='x'
    - i='b', j='y'
    - i='c', j='z'

    Output:

    ```python
        a x
        b y
        c z
    ```


### 2. while Loop

Runs until the condition becomes false.

```python
count = 1
while count <= 5:
    print(count)
    count += 1
```

Output:

```python
1 2 3 4 5
```
# Input/Output

## 1. Input

Input is taken as a string by default.

👉 `input()` always returns a string

- No matter what the user types, Python treats it as text (string).

Example :-

```python
name = input("Enter name: ")

```

If you type:

```python
Nitesh
```

Then:

```python
name = "Nitesh"   # string

```

🟦 Input an integer:

```python
num = int(input("Enter number: "))

```

🟩 Input a float:

```python
price = float(input("Enter price: "))

```

### Taking multiple inputs in one line

Example input:
```python
10 20
```

🟧 Use split()

```python
a, b = input().split()

```

Result:

```python
a = "10"
b = "20"

```

If you want them as integers:

```python
a, b = map(int, input().split())

```

Now:

```python
a = 10  # int
b = 20  # int

```

🎯 Summary Table


| Want to take      | How to take                          |
| ----------- | ------------------------------------ |
| Single string       |      `s = input()`  |
| Single integer       | `x = int(input())` |
| Single float    | `x = float(input())` |
| Two integers    | `a, b = map(int, input().split())` |
| List of integers    | `arr = list(map(int, input().split()))` |
| List of strings    | `arr = input().split()` |


---


## 2. Output

Use `print()` function.

```python
print("Hello World")

name = "Nitesh"
print("Hello", name)

```

✔ Print without new line

```python
print("Hello", end=" ")
print("World")

```
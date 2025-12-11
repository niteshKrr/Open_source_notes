# Functions

- A function is a block of code which only runs when it is called.
- A function helps avoiding code repetition.
- A function can return data as a result.


Syntax

```python
def function_name(parameters):
    # code
    return value
```

✔ Example

```python
def add(a, b):
    return a + b

print(add(3, 4))   # Output: 7
```

---

## ⭐ *args and **kwargs

### 1. *args → many positional arguments

- `args` means arguments
- `*` means collect all extra positional arguments
- Inside the function, `args` becomes a tuple containing all the passed arguments

✔ Example

```python
def add(*args):
    print(args)

add(1, 2, 3)
```

Output:

```python
(1, 2, 3)
```


### 2. **kwargs → many keyword arguments

- `kwargs` means keyword arguments
- `**` means collect all extra named arguments
- Inside the function, `kwargs` becomes a dictionary containing all the keyword arguments

✔ Example

```python
def details(**kwargs):
    print(kwargs)

details(name="Nitesh", age=21)
```

Output:

```python
{'name': 'Nitesh', 'age': 21}
```

---

### ⭐ Lambda Function (Anonymous Function)

- A lambda function is a small, one-line function in Python that does not need a name.
- It is mainly used when you need a quick, temporary function.

Syntax

```python
lambda arguments: expression
```

Example

```python
square = lambda x: x * x
print(square(5))
```

Output

```python
25
```
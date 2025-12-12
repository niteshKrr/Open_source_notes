# Map, Filter, Reduce

## 1. `map()`

Applies a function to every item in an iterable.

Syntax

```python
map(function, iterable)

# Returns: a map object (you must convert it to list/tuple to see results)
```

✔ Example

```python
nums = [1, 2, 3, 4]

result = list(map(lambda x: x*2, nums))
print(result)
```

Output

```python
[2, 4, 6, 8]

# The lambda function doubles each number.
```


✔ `map()` with a normal function

```python
def square(x):
    return x*x

result = list(map(square, [1, 2, 3]))
print(result)
```

Output

```python
[1, 4, 9]
```


---

## 2. `filter()`

Filters items based on a condition (keeps only True values).

Syntax

```python
filter(function, iterable)

# Returns: filter object (convert to list to view)
```

✔ Example

```python
nums = [1, 2, 3, 4, 5]

result = list(filter(lambda x: x % 2 == 0, nums))
print(result)
```

Output

```python
[2, 4]

# Keeps only even numbers.
```


✔ `filter()` with function

```python
def is_positive(x):
    return x > 0

result = list(filter(is_positive, [-1, 0, 2, 3]))
print(result)
```

Output

```python
[2, 3]
```

---

## 3. `reduce()`

Applies a function cumulatively to all items (reduces list to a single value).

- `reduce()` is NOT built-in, it is in functools.

Syntax

```python
from functools import reduce
reduce(function, iterable)
```

✔ Example: Sum of list

```python
from functools import reduce

nums = [1, 2, 3, 4]

result = reduce(lambda a, b: a + b, nums)
print(result)
```

Output

```python
10
```

This works like:

- Step 1: 1 + 2 = 3
- Step 2: 3 + 3 = 6
- Step 3: 6 + 4 = 10

✔ Another example: Find maximum

```python
from functools import reduce

nums = [10, 5, 20, 7]

result = reduce(lambda a, b: a if a > b else b, nums)
print(result)
```

Output

```python
20
```

---

### 📌 Summary Table

| Function      | Purpose                          | Returns          | Example  |
| ----------- | ------------------------------------ | ------------ | ------------- |
|   `map()`     |      Transform all  |          map object          |     Double all numbers     |
| `filter()`       |  Keep only items matching condition  |         filter object      |        Keep even numbers             |
| `reduce()`       |      Reduce list to one value  |         single value               |        Sum of list             |


### ⭐ When to Use What ?


| Use      | Best Function     |
| ----------- | --------------- |
|   Modify all items     |      `map()`  |
| Choose some items       |      `filter()`  |
| Combine all items       |      `reduce()`  |



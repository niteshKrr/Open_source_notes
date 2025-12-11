# Lists & Tuples

## 1. List

A list is a collection of items that is :-

- Ordered
- Mutable (can be changed)
- Allows duplicate elements
- Can store different data types


Example

```python
my_list = [10, 20, 30, "hello", 4.5]
```

Creating Lists

```python
lst = [1, 2, 3]
lst = list([1, 2, 3])
lst = []   # empty list
```

Accessing List Elements

Indexing

```python
lst[0]   # first element
lst[-1]  # last element
```

Slicing

```python
lst[1:4]   # from index 1 to 3
lst[:3]    # from start to 2
lst[2:]    # from index 2 to end
lst[::-1]  # reverse list
```

✅ Useful List Methods

| Method      | Description                          |
| ----------- | ------------------------------------ |
| `append(x)`       |      Add item at end  |
| `insert(i, x)`       |      Insert at index  |
| `remove(x)`       |      Remove first occurrence  |
| `pop(i)`       |      Remove & return element  |
| `clear()`       |      Remove all items  |
| `sort()`       |      Sort list (ascending)  |
| `reverse()`       |      Reverse list  |
| `count(x)`       |      Count frequency  |


---


## 2. Tuple

A tuple is :-

- Ordered
- Immutable (cannot be changed)
- Allows duplicates
- Faster than lists
- Used for constant / fixed data


Example

```python
my_tuple = (1, 2, 3)
```

Creating Tuples

```python
t = (1, 2, 3)
t = tuple([1, 2, 3])
t = ()              # empty tuple
t = (5,)            # single-element tuple must end with comma
```

Accessing Tuple Elements

Same as list:

```python
t[0]
t[-1]
t[1:3]
```

✅ Tuple Methods

| Method      | Description                          |
| ----------- | ------------------------------------ |
| `count(x)`       |      Counts occurrences  |
| `index(x)`       |      Returns index  |


---


## 🎯 When to Use What?

| Feature      | List                          | Tuple          |
| ----------- | ------------------------------------ | ------------ |
|   Mutability     |      Mutable  |          Immutable          |
| Performance       |      Slower  |         Faster               |
| Memory Usage       |      More  |         Less               |
| Use Case       |      Dynamic Data  |         Fixed Data               |


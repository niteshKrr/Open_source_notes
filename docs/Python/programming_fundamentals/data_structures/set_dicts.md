#  Sets & Dictionaries 

## 1. Dictionary (dict)

- A dictionary is a collection of key–value pairs.
- It is used when you want to store data in pairs and access it using a key instead of an index.


✔ Features :-

- Mutable (you can change it)
- Unordered (Python 3.7+ keeps insertion order)
- Keys must be unique
- Values can be duplicate
- Keys must be immutable types (str, int, tuple, etc.)

Creating a Dictionary

```python
my_dict = {
    "name": "Nitesh",
    "age": 25,
    "city": "Delhi"
}
```

Or

```python
my_dict = dict(name="Nitesh", age=25)
```

Accessing Values

```python
print(my_dict["name"])
print(my_dict.get("age"))      # safer (doesn't give error)
```

Adding / Updating

```python
my_dict["age"] = 30
my_dict["country"] = "India"
```

Removing Items

```python
my_dict.pop("age")        # removes key
my_dict.popitem()         # removes last inserted pair
del my_dict["city"]       # deletes key
my_dict.clear()           # empties dictionary
```

Important Dictionary Methods <br>
`keys()`, `values()`, `items()`

```python
print(my_dict.keys())     # all keys
print(my_dict.values())   # all values
print(my_dict.items())    # (key, value) pairs
```

📌 Looping Through Dictionary

```python
for key in my_dict:
    print(key, my_dict[key])

for key, value in my_dict.items():
    print(key, value)
```

---

## 2. Set (set)

A set is a collection of unique, unordered items.

✔ Features :-

- No duplicates allowed
- Unordered (order not guaranteed)
- Mutable
- Only immutable items can be added (e.g., numbers, strings, tuples)


Creating a Set

```python
my_set = {1, 2, 3, 4}
```

Or

```python
my_set = set([1, 2, 3])
```

⚠️ `{}` creates an empty dictionary, due to which use below syntax to create empty set

```python
empty_set = set()
```


Adding & Removing Items

```python
my_set.add(5)
my_set.remove(3)   # error if not present
my_set.discard(10) # no error if not present
my_set.pop()       # removes random element
my_set.clear()
```

---

## 🎯 Summary Table


| Feature      | Dictionary                          | Set          |
| ----------- | ------------------------------------ | ------------ |
| Stores       |      Key → Value pairs  |         Unique values               |
|   Mutable     |      Yes  |          Yes          |
| Ordered       |      Yes (since Python 3.7)  |         No               |
| Duplicate Values       |      Yes  |         No               |
| Access       |      By key  |         By membership               |



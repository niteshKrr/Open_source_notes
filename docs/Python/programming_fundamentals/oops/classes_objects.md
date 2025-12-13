# Classes & Objects

## What is a Class?

A **class** is a blueprint or template used to create objects.

👉 It defines :-

- What data an object will have (variables)
- What actions it can perform (functions)

💡 Think of a **class** as a design, not a real thing.


## What is an Object?

An **object** is a real instance of a class.

👉 If class is a blueprint of a house,<br>
✔ object is the actual house built from it.

Real-life Example

- **Class** → Car
- **Objects** → BMW, Audi, Tesla

Each car has :-

- **Properties** → color, speed
- **Actions** → `drive()`, `brake()`


### Defining a Class in Python

```python
class Student:
    pass
```

- **class** → keyword
- **Student** → class name
- **pass** → empty class (placeholder)

### Creating an Object

```python
s1 = Student()

# s1 is an object of class Student
```


### Class with Variables (Attributes)

```python
class Student:
    name = "Rahul"
    age = 20


s1 = Student()
print(s1.name)
print(s1.age)
```

## The `__init__()` Method (Constructor)

`__init__()` is called automatically when an object is created.The `__init__()` method is used to assign values to object properties, or to perform operations that are necessary when the object is being created.


```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age


s1 = Student("Rahul", 20)
s2 = Student("Amit", 22)

print(s1.name)   # Rahul
print(s2.age)    # 22
```


??? info "What is self?"

    - The self parameter is a reference to the current instance of the class.
    - It is used to access properties and methods that belong to the class.

    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age

        def greet(self):
            print("Hello, my name is " + self.name)


    p1 = Person("Emil", 25)
    p1.greet()
    ```

    **Note :-** The **self** parameter must be the first parameter of any method in the class.


## Instance Variables vs Class Variables


### Instance Variable

- Belongs to object
- Different for each object

```python
self.name
```

### Class Variable

- Shared by all objects

```python
class Student:
    college = "ABC College"
```

✔ Example

```python
class Student:
    college = "ABC College"

    def __init__(self, name):
        self.name = name


s1 = Student("Rahul")
s2 = Student("Amit")

print(s1.college)
print(s2.college)
```

Modifying Object Data

```python
s1.age = 25
print(s1.age)
```

Deleting Object Properties

```python
del s1.age
```

Deleting object

```python
del s1
```



# Abstract Base Class (ABC)

## 1. What is an Abstract Base Class?

An **Abstract Base Class (ABC)** is a class that :-

- Cannot be instantiated (you can’t create its object)
- Is used to define a common structure (rules) for child classes
- Forces child classes to implement certain methods

👉 Think of it as a **blueprint**.


## 2. Why do we need ABC?

**Without ABC :-**

- A child class may forget to implement important methods
- No strict enforcement of structure

**With ABC :-**

- You guarantee that child classes follow a contract
- Helps in clean design and maintainability


## 3. How to create an Abstract Base Class?

Python provides the `abc` module.

Required imports:

```python
from abc import ABC, abstractmethod
```

✔ Basic Syntax

```python
from abc import ABC, abstractmethod
import math

class Shape(ABC):

    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius**2

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height
```


```python
# Creating instances of Circle and Rectangle
circle = Circle(5)
rectangle = Rectangle(4, 6)

# Calculating and printing areas
print("Circle Area:", circle.area())        # Output: 78.54
print("Rectangle Area:", rectangle.area())   # Output: 24
```

- **`ABC` →** makes the class abstract
- **`@abstractmethod` →** method must be implemented by child class
- **`pass` →** placeholder



---

## Key Rules (Very Important)

**Abstract class :-**

- Can have abstract + normal methods
- Cannot create object

**Child class :-**

- Must implement all abstract methods

**Used mainly for :-**

- Design consistency
- Polymorphism



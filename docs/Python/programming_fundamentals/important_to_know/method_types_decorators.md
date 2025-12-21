# Method Types & Decorators

## Method Decorators in Python Classes

In **Python**, decorators modify how a method behaves.
Inside a class, the most common method decorators are :-


1. `@instance` method (default)
2. `@classmethod`
3. `@staticmethod`
4. `@property`


### 1️⃣ Instance Method (Default)

👉 What it is

- Normal method inside a class
- Uses **self**
- Can access **instance variables** and other **instance methods**

✔ Example

```python
class Student:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print("Hello", self.name)


s = Student("Nitesh")
s.greet()
```

**Key points**

- `self` refers to the **current object**
- Can access :-

    - instance variables
    - other instance methods


**Remember**

➡️ Most commonly used<br>
➡️ Default method type<br>
➡️ Needs object to call


---


### 2️⃣ `@classmethod`

👉 What it is

- Method that works with the **class, not object**
- Uses `cls` instead of `self`


✔ Example

```python
class Student:
    college = "ABC College"

    @classmethod
    def get_college(cls):
        return cls.college


print(Student.get_college())
```

**Key points**

- `cls` refers to the **class itself**

- Can access:

    - class variables

- Cannot directly access instance variables


**Use case**

✔ Factory methods<br>
✔ When logic is related to class, not individual object


---


### 3️⃣ `@staticmethod`


👉 What it is

- **Normal function** inside a class
- No **self**, no **cls**


✔ Example

```python
class Math:
    @staticmethod
    def add(a, b):
        return a + b


print(Math.add(3, 4))
```

**Key points**

- Does **not** access :-

    - instance variables
    - class variables (directly)

- Just grouped inside class for **logical organization**


**Use case**

✔ Utility/helper functions<br>
✔ Logic related to class conceptually


---


### 4️⃣ `@property`


👉 What it is

- Used to access a **method like a variable**
- Makes code **clean and safe**


✔ Example

```python
class Student:
    def __init__(self, marks):
        self._marks = marks

    @property
    def marks(self):
        return self._marks


s = Student(90)
print(s.marks)   # no brackets!
```

**Why use it?**

✔ Read-only variables<br>
✔ Validation<br>
✔ Encapsulation


---

??? info "🧠 Easy Memory Trick"

    - **self → object**
    - **cls → class**
    - **static → helper**
    - **property → looks like variable**



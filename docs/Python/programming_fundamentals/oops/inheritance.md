# Inheritance

## Inheritance in Python

**Inheritance** is an **OOP** concept where one class **(child / derived class)** acquires the properties and methods of another class **(parent / base class)**.

👉 It helps in :-

- Code reuse
- Better organization
- Easier maintenance


✔ Simple Example

```python
class Animal:
    def speak(self):
        print("Animal makes a sound")

class Dog(Animal):
    def bark(self):
        print("Dog barks")

d = Dog()
d.speak()   # inherited method
d.bark()    # own method
```

Output:

```python
Animal makes a sound
Dog barks
```


---


## Types of Inheritance

1️⃣ Single Inheritance

    ➡ One parent → one child

2️⃣ Multilevel Inheritance

    ➡ Parent → Child → Grandchild

3️⃣ Multiple Inheritance

    ➡ One child inherits from multiple parents

4️⃣ Hierarchical Inheritance

    ➡ One parent → multiple children

5️⃣ Hybrid Inheritance

    ➡ Combination of two or more inheritance types


---

## `__init__` in Python (Constructor)

- `__init__` is a special method
- It is called automatically when an object is created
- Used to initialize (set up) object data


✔ Example

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

s1 = Student("Nitesh", 21)
print(s1.name)  # Nitesh
print(s1.age)   # 21
```

👉 When **Student("Nitesh", 21)** is called,<br>
👉 `__init__` runs automatically.




---


## `super()` Keyword

`super()` Keyword is used to call parent class method or constructor.


✔ Example

```python
# Parent Class: Animal
class Animal:
    def __init__(self, name):
        self.name = name

    def info(self):
        print("Animal name:", self.name)

# Child Class: Dog
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)   # Call parent constructor
        self.breed = breed

    def details(self):
        print(self.name, "is a", self.breed)

d = Dog("Buddy", "Golden Retriever")
d.info()      # Parent method
d.details()   # Child method
```

Output

```python
Animal name: Buddy
Buddy is a Golden Retriever
```



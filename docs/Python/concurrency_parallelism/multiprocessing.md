# Multiprocessing_


## ⚙️ Multiprocessing_

**Multiprocessing** means **running multiple processes at the same time**.

- Each **process has its own memory**
- Each process has its **own Python interpreter**
- Each process has its **own GIL**

✔ True parallel execution<br>
✔ Uses multiple CPU cores


??? info "Process"

    A **process** is an independent instance of a running program managed by the operating system, with its own dedicated memory space and resources.

    👉 This is distinct from a thread, which shares memory with other threads within the same process.


✔ Example

```python
import time
from multiprocessing import Process

def calc_square(numbers):
    for n in numbers:
        time.sleep(0.5)
        print(f'Square of {n}: {n*n}')

def calc_cube(numbers):
    for n in numbers:
        time.sleep(0.5)
        print(f'Cube of {n}: {n*n*n}')
        
def main():
    arr = [2,3,8]
    p1 = Process(target=calc_square, args=(arr,))
    p2 = Process(target=calc_cube, args=(arr,))

    p1.start()
    p2.start()
    p1.join()
    p2.join()

    print("Done!")

if __name__ == "__main__":
    main()
```

✔ **Both processes(p1 & p2)** run on different CPU cores.


---

## `ProcessPoolExecutor`

`ProcessPoolExecutor` is a **high-level API for multiprocessing** provided by the
`concurrent.futures` module.


```python
import time
from concurrent.futures import ProcessPoolExecutor
import os

def calc_square(n):
    time.sleep(0.2)
    print(f"Square of {n}: {n*n}")
    print(f"Process ID for square calculation: {os.getpid()}")


def main():
    arr = [2, 3, 4, 5]

    with ProcessPoolExecutor(max_workers=4) as executor:
        # map applies function to EACH element
        executor.map(calc_square, arr)

    print("Done!")

if __name__ == "__main__":
    main()
```


### Why Use ProcessPoolExecutor?

**Without it :-**

- You manually create `Process`
- Handle `start()` and `join()`

**With it :-**

- Cleaner code
- **Automatic process management**
- Easier to scale


??? info "ProcessPoolExecutor Methods"

    1️⃣ `submit()` – Submit One Task

    What it does

    - Submits **one function call**
    - Runs it in a **separate process**
    - Returns a **Future object**

    Syntax

    ```python
    future = executor.submit(fn, *args)
    ```

    Example

    ```python
    future = executor.submit(square, 4)
    result = future.result()
    ```

    When to use

    ✔ Tasks are different<br>
    ✔ Need fine control<br>
    ✔ Want async behavior

    ---

    2️⃣ `map()` – Submit Multiple Tasks

    What it does

    - Applies **same function** to **multiple inputs**
    - Returns results in **input order**
    - Blocks until all tasks finish

    Syntax

    ```python
    executor.map(fn, iterable)
    ```

    Example

    ```python
    results = executor.map(square, [1, 2, 3, 4])
    print(list(results))
    ```

    When to use

    ✔ Same function, many inputs<br>
    ✔ Order matters<br>
    ✔ Clean code

    ---


    3️⃣ `shutdown()` – Stop Executor

    What it does

    - Stops accepting new tasks
    - Waits for running tasks to finish (default)

    Syntax

    ```python
    executor.shutdown(wait=True)
    ```

    Example

    ```python
    executor.shutdown()
    ```

    📌 Automatically called when using `with`


---

## `multiprocessing.Pool` (Older Style)

A **pool** is a **group of worker threads or processes** that are **created once** and **reused** to execute multiple tasks.

Using Pool

```python
from multiprocessing import Pool
import os

def square(n):
    return n * n

def main():
    with Pool(processes=4) as p:
        result = p.map(square, [1, 2, 3, 4, 5])
        print(result)

if __name__ == "__main__":
    main()
```

✔ Similar to ThreadPoolExecutor

---


## 🔁 Sharing Data Between Two Processes

❗ Important Rule (First)

- Each process has its **own memory space**
- Normal variables **cannot be shared**

```python
x = 10   # ❌ Not shared between processes
```

✅ Ways to Share Data Between Processes

1. `Queue` (Most common)
2. `Pipe`
3. `Value`
4. `Array`
5. `Manager`

---


### 1️⃣ `Queue`

👉 Best & Most used

**What is it?**

- A **FIFO** data structure
- Safe for multiple processes
- Used for **sending messages or data**


✔ Example

```python
from multiprocessing import Process, Queue

def sender(q):
    q.put("Hello from Process 1")

def receiver(q):
    msg = q.get()
    print("Received:", msg)

if __name__ == "__main__":
    q = Queue()

    p1 = Process(target=sender, args=(q,))
    p2 = Process(target=receiver, args=(q,))

    p1.start()
    p2.start()
    p1.join()
    p2.join()
```

Output

```python
Received: Hello from Process 1
```

- Safe
- Simple
- Most commonly used


---


### 2️⃣ Pipe

👉 `Two-Way` Communication

**What is it?**

- A **direct connection** between two processes
- Faster than Queue
- Best for **two processes only**


✔ Example

```python
from multiprocessing import Process, Pipe

def process1(conn):
    conn.send("Hello from P1")
    conn.close()

def process2(conn):
    print("Received:", conn.recv())
    conn.close()

if __name__ == "__main__":
    parent_conn, child_conn = Pipe()

    p1 = Process(target=process1, args=(child_conn,))
    p2 = Process(target=process2, args=(parent_conn,))

    p1.start()
    p2.start()

    p1.join()
    p2.join()
```

- Faster
- Not good for many processes


---


### 3️⃣ Value

👉 Share a Single Variable

**What is it?**

- Used to share **a single value**
- Stored in shared memory


✔ Example

```python
from multiprocessing import Process, Value

def increment(val):
    val.value += 1

if __name__ == "__main__":
    num = Value('i', 0)   # 'i' = DataType(int-'i', float-'f')

    p1 = Process(target=increment, args=(num,))
    p2 = Process(target=increment, args=(num,))

    p1.start()
    p2.start()

    p1.join()
    p2.join()

    print("Final value:", num.value)
```

⚠ Race condition possible → use Lock if needed


---


### 4️⃣ Array

👉 Share a List of Fixed Size

**What is it?**

- Shared **memory array**
- Faster than Manager list


✔ Example

```python
from multiprocessing import Process, Array

def modify(arr):
    arr[0] = 100

if __name__ == "__main__":
    arr = Array('i', [1, 2, 3])  # 'i' = DataType(int-'i', float-'f')

    p = Process(target=modify, args=(arr,))
    p.start()
    p.join()

    print(arr[:])
```


---


### 5️⃣ Manager

👉 Share Complex Objects (Easy but Slower)

**What is it?**

- Allows sharing :-

    - list
    - dict
    - set

- Uses a **server process**


✔ Example

```python
from multiprocessing import Process, Manager

def add_item(shared_list):
    shared_list.append(10)

if __name__ == "__main__":
    with Manager() as manager:
        shared_list = manager.list()

        p1 = Process(target=add_item, args=(shared_list,))
        p2 = Process(target=add_item, args=(shared_list,))

        p1.start()
        p2.start()

        p1.join()
        p2.join()

        print(shared_list)
```


---

### 🔑 Which One Should You Use?

**Use :-**

- **Queue →** general data sharing
- **Pipe →** 2 processes only
- **Value / Array →** shared memory
- **Manager →** shared dict/list/set



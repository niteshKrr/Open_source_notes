# Multithreading_


## 🧵 Multithreading_

**Multithreading** means running multiple **threads** within the same process.

✔ Faster execution<br>
✔ Better CPU utilization<br>
✔ Ideal for I/O-bound tasks<br>


??? info "thread"

    **A thread is a smallest unit of execution inside a program.**

    - **A program → can have multiple threads**
    - **All threads share the same memory**
    - **Threads run concurrently (appear to run at the same time)**

✔ Example

```python
from threading import Thread
import time

def calculate_square(nums):
    for n in nums:
        time.sleep(0.5)
        print(f'Square of {n}: {n*n}')

def calculate_cube(nums):
    for n in nums:
        time.sleep(0.5)
        print(f'Cube of {n}: {n*n*n}')

def main():

    nums = [1, 2, 3, 4, 5]
    t1 = Thread(target=calculate_square, args=(nums,))
    t2 = Thread(target=calculate_cube, args=(nums,))

    t1.start()
    t2.start()
    t1.join()
    t2.join()

    print("Done!")

if __name__ == "__main__":
    main()
```

**Since both threads** (t1 and t2) run **concurrently**, the order of execution is not fixed.


---


## `ThreadPoolExecutor`

**ThreadPoolExecutor** makes it easier to manage multiple threads without manually creating them.

```python
from concurrent.futures import ThreadPoolExecutor
import time
import os

def calculate_square(n):
    time.sleep(0.5)
    print(f'Square of {n}: {n*n}')
    print(f'Process ID: {os.getpid()}')

def main():
    nums = [1, 2, 3, 4, 5]
    # Create a thread pool with 2 workers
    with ThreadPoolExecutor(max_workers=2) as executor:
        # Submit two tasks to run in parallel
        executor.map(calculate_square, nums)

    print("Done!")

if __name__ == "__main__":
    main()
```

👉 **Important to know?**

- `Thread Pool` = group of reusable threads
- `max_workers=2` → only 2 threads will run at a time
- `submit()` → sends a task to thread pool
- `with` block :-

    - Automatically starts threads
    - Automatically waits for all threads to finish
    - Automatically closes the pool
    - 📌 No need for `start()` or `join()` manually


---

## 🔒 GIL (Global Interpreter Lock)

The **Global Interpreter Lock (GIL)** in Python is a **mutex** (lock) used in the default interpreter (CPython) that ensures **only one thread can execute Python bytecode at a time**, even on **multi-core** processors. 


✔ Example to Understand GIL


Single Thread
```python
import time

COUNT = 50_000_000

def countdown(n):
    while n > 0:
        n -= 1

start = time.time()
countdown(COUNT)

print("Time taken:", time.time() - start)
```


Multithreading (Still Slow)
```python
import time
from threading import Thread

COUNT = 50_000_000

def countdown(n):
    while n > 0:
        n -= 1

t1 = Thread(target=countdown, args=(COUNT//2,))
t2 = Thread(target=countdown, args=(COUNT//2,))

start = time.time()
t1.start(); t2.start()
t1.join(); t2.join()

print("Time taken:", time.time() - start)
```

❗ Observation

⏱ Time `≈` same or **slightly worse**

👉 Why?
Because :-

- Only **one thread holds GIL at a time**
- Threads take turns (context switching)
- No real parallel execution


### I/O-Bound Programs

**Programs that wait for I/O :-** downloading files, reading files, database queries, API calls. Here, GIL does not slow you down because:

- When a thread waits for I/O -> it releases the GIL.
- Other threads can run during that time.

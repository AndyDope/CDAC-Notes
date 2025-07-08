### **Sessions 28 & 29: Synchronization, Deadlock, and Inter-thread Communication**

Welcome. In our last session, we learned how to create multiple threads. The real challenge of multithreading isn't creating threads, but managing their interaction. Because threads share the same [[Java Session 6 - Constructors, Pass by value, Heap and Stack#3. Heap and Stack Memory|heap memory]], they can interfere with each other when accessing the same object, leading to data corruption. **Synchronization** is the mechanism used to prevent this. We will also explore the dangerous state of **deadlock** and the `wait/notify` mechanism for coordinating threads.

---

#### **1. The Problem: Race Conditions**

When two or more threads try to access and manipulate the same shared resource (like an object's field) concurrently, and the result of the operation depends on the timing of their execution, this is called a **race condition**.

**Classic Example: A Shared Counter**
Imagine two threads are both trying to execute `count++`. This single line is not atomic; it's actually three steps:
1.  Read the current value of `count`.
2.  Add 1 to the value.
3.  Write the new value back to `count`.

**Race Condition Scenario:**
1.  `Thread A` reads `count` (value is 10).
2.  The OS pauses `Thread A` and runs `Thread B`.
3.  `Thread B` reads `count` (value is still 10).
4.  `Thread B` increments it to 11 and writes 11 back to `count`.
5.  `Thread A` resumes. It still has the old value it read (10), increments it to 11, and writes 11 back to `count`.

**Result:** Two increment operations were performed, but the final value is 11 instead of the correct value of 12. This is data corruption.

---

#### **2. Synchronization**

Synchronization is a mechanism that ensures only one thread can access a shared resource or execute a critical section of code at a time. It enforces mutual exclusion.

In Java, synchronization is achieved using an intrinsic **lock** (also called a monitor lock) that every object has.

##### **a) `synchronized` Method**
When you declare a method as `synchronized`, a thread must acquire the object's lock before it can execute the method. While the thread is inside the method, the lock is held, and no other thread can enter *any* `synchronized` method on the *same object*.
```java
class Counter {
    private int count = 0;

    // Only one thread can execute this method on a given Counter object at a time.
    public synchronized void increment() {
        count++;
    }
    public int getCount() { return count; }
}
```

##### **b) `synchronized` Block**
Sometimes you don't need to lock the entire method, only a small, critical section of it. This can improve performance. You can specify which object's lock to acquire.
```java
public void someMethod() {
    // Non-critical code can be run by multiple threads concurrently...

    synchronized(this) { // 'this' refers to the current object's lock
        // Critical section: only one thread can be in here at a time.
    }
    
    // More non-critical code...
}
```

> **Quick Question:** If an object has two `synchronized` methods, `methodA()` and `methodB()`, and `Thread-1` is currently executing `methodA()`, can `Thread-2` execute `methodB()` on the same object?
> **Answer:** No. `Thread-1` holds the object's lock. `Thread-2` must wait until `Thread-1` releases the lock (by exiting `methodA()`) before it can acquire the lock to enter `methodB()`.

---

#### **3. Deadlock**

Deadlock is a catastrophic situation where two or more threads are blocked forever, each waiting for a resource that the other thread holds.

**Classic Deadlock Scenario (Dining Philosophers):**
*   `Thread A` acquires the lock for `Resource 1`.
*   `Thread B` acquires the lock for `Resource 2`.
*   `Thread A` now tries to acquire the lock for `Resource 2` but must wait because `Thread B` holds it.
*   `Thread B` now tries to acquire the lock for `Resource 1` but must wait because `Thread A` holds it.

Both threads are now stuck in a permanent waiting state. The program hangs.

```java
// Simplified Deadlock Example
public class DeadlockDemo {
    public static final Object lock1 = new Object();
    public static final Object lock2 = new Object();

    public static void main(String[] args) {
        new Thread(() -> {
            synchronized(lock1) {
                System.out.println("Thread 1: Holding lock 1...");
                try { Thread.sleep(100); } catch (Exception e) {}
                System.out.println("Thread 1: Waiting for lock 2...");
                synchronized(lock2) {
                    System.out.println("Thread 1: Holding lock 1 & 2");
                }
            }
        }).start();

        new Thread(() -> {
            synchronized(lock2) {
                System.out.println("Thread 2: Holding lock 2...");
                try { Thread.sleep(100); } catch (Exception e) {}
                System.out.println("Thread 2: Waiting for lock 1...");
                synchronized(lock1) {
                    System.out.println("Thread 2: Holding lock 1 & 2");
                }
            }
        }).start();
    }
}
```
**How to Avoid Deadlock:** The most common strategy is to ensure that all threads acquire locks in the **same fixed order**. If both threads tried to get `lock1` first and then `lock2`, deadlock would not occur.

---

#### **4. Inter-thread Communication: `wait()`, `notify()`, `notifyAll()`**

These methods from the `Object` class are used to coordinate threads. They allow a thread to pause its execution (`wait`) until some condition is met, at which point another thread can wake it up (`notify`).

*   **Rule:** These methods **must** be called from within a `synchronized` block on the object whose lock is held.
*   **`wait()`**: Causes the current thread to release the lock and go into a waiting state.
*   **`notify()`**: Wakes up a *single* thread that is waiting on this object's lock.
*   **`notifyAll()`**: Wakes up *all* threads that are waiting on this object's lock. The awakened threads will then compete to re-acquire the lock.

**The Producer-Consumer Problem:**
This is a classic problem solved using `wait/notify`. A "producer" thread adds items to a shared queue, and a "consumer" thread removes them.
*   The producer must wait if the queue is full.
*   The consumer must wait if the queue is empty.

```java
// Simplified Logic
class SharedQueue {
    // ...
    public synchronized void produce(Item item) {
        while (isFull()) {
            wait(); // Release the lock and wait if queue is full
        }
        // ... add item to queue ...
        notifyAll(); // Notify waiting consumers that an item is available
    }

    public synchronized Item consume() {
        while (isEmpty()) {
            wait(); // Release the lock and wait if queue is empty
        }
        // ... remove item from queue ...
        notifyAll(); // Notify waiting producers that space is available
        return item;
    }
}
```
**Why use `while` loops with `wait()`?** This is crucial to guard against "spurious wakeups". A thread can sometimes wake up from `wait()` without having been `notify()`'d. The `while` loop ensures the condition is re-checked before proceeding.

---

### **Topic Summary & Revision**

*   **Race Condition:** When multiple threads access a shared resource, leading to unpredictable results based on timing.
*   **`synchronized`:** A keyword to create a mutually exclusive block of code (critical section). It can be applied to methods or blocks.
*   **Lock:** Every Java object has an intrinsic lock (monitor). `synchronized` works by acquiring and releasing this lock.
*   **Deadlock:** A state where two or more threads are blocked forever, each waiting for the other. Avoid by acquiring locks in a consistent order.
*   **`wait()`:** Releases the lock and puts the thread into a waiting state.
*   **`notify()` / `notifyAll()`:** Wakes up one or all waiting threads.
*   **`wait/notify` Rule:** Must be called from within a `synchronized` block. Always use `wait()` inside a `while` loop that checks the condition.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A method is declared as `public static synchronized void doWork()`. Which lock is acquired when a thread calls this method?**
    (A) The lock of the `this` object instance.
    (B) No lock is acquired because the method is static.
    (C) The intrinsic lock of the `Class` object associated with the class (`MyClass.class`).
    (D) A new lock is created each time the method is called.
    **Answer:** ||(C) For 'static synchronized' methods, the lock acquired is on the '.class' object itself, not on any instance ('this'). This means only one thread can be inside any static synchronized method of that class at a time, across all instances.||
<br>

2.  **Which of the following is NOT a required condition for a deadlock to occur?**
    (A) Mutual Exclusion (resources cannot be shared).
    (B) Hold and Wait (a thread holds a resource while waiting for another).
    (C) High Thread Priority (one thread runs more often than another).
    (D) Circular Wait (a circular chain of threads waiting for each other's resources).
    **Answer:** ||(C) Thread priority has nothing to do with deadlock. The four necessary and sufficient conditions for deadlock are: Mutual Exclusion, Hold and Wait, No Preemption (a resource cannot be forcibly taken), and Circular Wait.||
<br>

3.  **Why is it critical to call `wait()` inside a `while` loop instead of an `if` statement?**
    (A) To prevent the program from compiling.
    (B) To guard against "spurious wakeups," where a thread can wake up without being notified.
    (C) To ensure the `notify()` call is not missed.
    (D) To improve the performance of the lock acquisition.
    **Answer:** ||(B) The JVM specification allows for a thread to wake up from 'wait()' for no apparent reason (a spurious wakeup). If you use an 'if', the thread will proceed incorrectly. A 'while' loop ensures that the condition is re-checked upon waking, making the code robust against this phenomenon.||
<br>

4.  **A thread calls `notifyAll()` on an object. What happens to the threads that were waiting on that object's monitor?**
    (A) They all resume execution immediately and concurrently.
    (B) One thread is chosen at random to resume execution.
    (C) They all move from the "waiting" state to the "blocked" (or "runnable") state and will compete to acquire the object's lock. Only one will succeed at a time.
    (D) It throws an `IllegalMonitorStateException` if more than one thread is waiting.
    **Answer:** ||(C) 'notifyAll()' does not grant the lock to anyone. It simply wakes up all waiting threads. These threads then behave like any other thread trying to enter a 'synchronized' block: they all compete for the lock, and only one will win and be allowed to proceed.||
<br>

5.  **Thread A is inside a `synchronized` method of object `X`. Thread B is inside a non-`synchronized` method of the same object `X`. Which statement is true?**
    (A) Thread B will be blocked until Thread A finishes.
    (B) Thread A will be blocked until Thread B finishes.
    (C) Both threads can execute concurrently without blocking each other.
    (D) A deadlock will occur.
    **Answer:** ||(C) The 'synchronized' keyword only protects other 'synchronized' blocks/methods on the same object. A thread entering a non-synchronized method does not need to acquire the object's lock, so it can run concurrently with a thread that holds the lock inside a synchronized method.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** "Explain deadlock and how to prevent it." Describe the four conditions (Mutual Exclusion, Hold and Wait, No Preemption, Circular Wait) and explain that breaking the Circular Wait by enforcing a strict lock acquisition order is the most common prevention strategy.
*   **Modern Alternatives:** The `wait/notify` mechanism is powerful but low-level and hard to use correctly. The modern `java.util.concurrent` package provides higher-level abstractions that are much safer and easier to use, such as `BlockingQueue` (which handles the producer-consumer logic for you) and `Lock` objects (`ReentrantLock`), which are a more flexible alternative to the `synchronized` keyword.
*   **`volatile` keyword:** A related concept is the `volatile` keyword. When a variable is declared `volatile`, it guarantees that any write to it by one thread is immediately visible to other threads. It does not provide mutual exclusion like `synchronized`, but it is crucial for ensuring visibility of shared variables in certain lock-free algorithms.

**🔗Links:** [[Java Session 30 - Generics and Reflection API]]
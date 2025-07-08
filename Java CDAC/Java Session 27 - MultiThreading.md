### **Session 27: MultiThreading**

Welcome to Session 27. So far, all our programs have run in a single, sequential path of execution. This is known as a single-threaded application. **Multithreading** is the ability of a program to execute multiple parts (threads) concurrently. This allows for better utilization of modern multi-core CPUs, leading to more responsive user interfaces and higher throughput for background tasks.

---

#### **1. Introduction to Threads**

*   **Process:** An instance of a program running on a computer (e.g., your browser, a music player). Each process has its own dedicated memory space.
*   **Thread:** A single, sequential flow of control within a process. A process can have multiple threads, all sharing the same memory space. Each thread has its own **stack**, but they share the **heap**. This shared heap is what makes communication between threads easy, but it's also a major source of complexity and bugs.

**Analogy: The Restaurant**
*   **Process:** The restaurant itself, with its kitchen, tables, and food inventory (shared memory/heap).
*   **Thread:** A single chef working in that kitchen.
    *   **Single-threaded:** One chef does everything: takes orders, cooks, serves, and cleans. If the chef is busy cooking a complex dish, no new orders can be taken.
    *   **Multi-threaded:** Multiple chefs work in the same kitchen. One can be chopping vegetables while another is grilling meat. They can work on different orders at the same time, increasing the restaurant's overall efficiency. However, they must coordinate to avoid bumping into each other or using the same pan at the same time (concurrency issues).

---

#### **2. Creating Threads: `Thread` class and `Runnable` Interface**

There are two primary ways to create a thread in Java:

##### **a) Extending the `Thread` Class**
1.  Create a class that `extends java.lang.Thread`.
2.  Override the `public void run()` method. This method contains the code that the thread will execute.
3.  Create an instance of your class and call its `start()` method. **Never call `run()` directly!** Calling `start()` tells the JVM to create a new thread and have that new thread execute the `run()` method.

```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Executing thread: " + Thread.currentThread().getName());
    }
}

// In main:
MyThread t1 = new MyThread();
t1.start(); // This starts a new thread of execution
```

##### **b) Implementing the `Runnable` Interface**
1.  Create a class that `implements java.lang.Runnable`.
2.  Implement the `public void run()` method.
3.  Create an instance of your `Runnable` class.
4.  Create an instance of the `Thread` class, passing your `Runnable` object to its constructor.
5.  Call the `start()` method on the `Thread` object.

```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Executing runnable: " + Thread.currentThread().getName());
    }
}

// In main:
MyRunnable myTask = new MyRunnable();
Thread t2 = new Thread(myTask);
t2.start();
```

**Which approach is better?**
**Implementing `Runnable` is almost always the preferred approach.** Java does not support multiple inheritance for classes ([[Java Session 7 - Inheritance, Association, Aggregation and Composition|Session 7]]). If you extend `Thread`, you cannot extend any other class. By implementing `Runnable`, your task class is free to extend another class if needed. It also promotes better design by separating the task (`Runnable`) from the execution mechanism (`Thread`).

> **Quick Question:** What is the difference between calling `t.start()` and `t.run()` on a `Thread` object `t`?
> **Answer:** `t.start()` creates a new thread and has that new thread execute the `run()` method concurrently. `t.run()` simply executes the `run()` method in the *current* thread, just like any other method call. No new thread is created.

---

#### **3. The `Thread` Class and its Methods**

The `Thread` class provides several methods for controlling a thread's execution.

*   **`sleep(long millis)`**: A `static` method that causes the **currently executing thread** to pause for the specified number of milliseconds. It throws a checked `InterruptedException`.
*   **`join()`**: A method that makes the current thread wait until the thread it is called on (`t.join()`) has finished its execution. This is used to ensure that a task is complete before the main program proceeds.
*   **`yield()`**: A `static` method that is a hint to the thread scheduler that the current thread is willing to yield its current use of a processor. The scheduler is free to ignore this hint. It's rarely used.
*   **`setPriority(int newPriority)` / `getPriority()`**: Sets or gets the thread's priority (a number from 1 to 10). Higher priority threads are given preference by the scheduler, but this is highly platform-dependent and should not be used for program correctness.
*   **`Thread.currentThread()`**: A `static` method that returns a reference to the currently executing `Thread` object.

---

#### **4. `ThreadGroup` Class**

A `ThreadGroup` represents a set of threads. It provides a way to manage a group of threads together. You can, for example, interrupt all threads in a group with a single command. In modern Java, `ThreadGroup` is rarely used. More advanced and flexible mechanisms for managing groups of tasks are available in the `java.util.concurrent` package (like Executor services), which are beyond the scope of this session but are the modern standard.

---

### **Topic Summary & Revision**

*   **Thread:** A single path of execution within a process. Threads in the same process share the heap but have their own stack.
*   **Creating Threads:**
    1.  **Extend `Thread`**: Simple but less flexible.
    2.  **Implement `Runnable`**: Preferred approach. Separates the task from the runner.
*   **`start()` vs. `run()`**: `start()` creates a new thread. `run()` executes in the current thread. **Always use `start()`**.
*   **Key Methods:**
    *   `sleep()`: Pauses the current thread.
    *   `join()`: Waits for another thread to die.
*   **`Runnable` is Preferred:** It allows your task class to extend other classes and promotes better object-oriented design.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A developer writes the following code. How many new threads are created, and what is the output?**
    ```java
    class MyTask implements Runnable {
        public void run() { System.out.print("Task "); }
    }
    public class Test {
        public static void main(String[] args) {
            Thread t = new Thread(new MyTask());
            t.run();
            t.run();
            t.start();
            System.out.print("Main ");
        }
    }
    ```
    (A) 3 threads are created. Output is unpredictable.
    (B) 1 new thread is created. Output is "Task Task Main Task ".
    (C) 1 new thread is created. Output is unpredictable but will contain "Task " three times and "Main " once.
    (D) 1 new thread is created. The output will be "Task Task " followed by an unpredictable interleaving of "Main " and "Task ".
    **Answer:** ||(D) Only one new thread is created by the call to 't.start()'. The first two calls to 't.run()' execute the run method sequentially in the 'main' thread. Therefore, "Task Task " will always print first. After 't.start()', the 'main' thread and the new 't' thread run concurrently, so "Main " and the final "Task " can appear in any order relative to each other.||
<br>

2.  **What is the most significant advantage of implementing `Runnable` over extending `Thread`?**
    (A) `Runnable` instances can be started using the `run()` method directly.
    (B) Implementing `Runnable` allows the class to extend another class, which is not possible if it extends `Thread`.
    (C) `Runnable` provides more methods for thread management, like `sleep()` and `join()`.
    (D) `Runnable` tasks run at a higher priority than `Thread` tasks.
    **Answer:** ||(B) Since Java does not support multiple class inheritance, extending 'Thread' uses up your class's only "extends" slot. Implementing 'Runnable' allows for more flexible object-oriented design, as your class can still inherit from a different parent. Management methods like 'sleep' and 'join' belong to the 'Thread' class, not 'Runnable' (C is wrong).||
<br>

3.  **What is the purpose of the `t.join()` method?**
    (A) To merge thread `t` with the main thread, creating a single thread.
    (B) To cause the currently executing thread to pause until thread `t` has completed its execution.
    (C) To make thread `t` wait for the current thread to complete.
    (D) To give thread `t` a higher priority in the scheduler.
    **Answer:** ||(B) Calling 'join()' on a thread reference forces the caller to wait for the callee to finish. It's a way of synchronizing tasks, ensuring one doesn't proceed until another is done.||
<br>

4.  **A thread is currently executing. What happens when it calls the static method `Thread.sleep(1000)`?**
    (A) The thread object is destroyed and garbage collected.
    (B) The thread moves to a "waiting" or "timed waiting" state and will likely not be scheduled for execution by the OS for at least 1000 milliseconds.
    (C) The thread immediately stops and can only be restarted by calling `start()` again.
    (D) The entire program (all threads) pauses for 1000 milliseconds.
    **Answer:** ||(B) 'sleep()' affects only the thread that calls it. It enters a non-runnable state for a designated period. It does not destroy the thread, and you cannot call 'start()' on a thread more than once.||
<br>

5.  **Which statement about threads in Java is FALSE?**
    (A) Each thread has its own call stack.
    (B) All threads within a process share the same heap memory.
    (C) A thread can be restarted by calling `start()` after its `run()` method has completed.
    (D) The `main` method of a Java application runs in a thread.
    **Answer:** ||(C) A thread's lifecycle is one-way. Once a thread has completed execution (is in the 'TERMINATED' state), it cannot be restarted. Attempting to call 'start()' a second time on the same 'Thread' object will throw an 'IllegalThreadStateException'.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The `start()` vs. `run()` question is the most fundamental multithreading interview question. Be ready to explain it clearly. The second most common question is about the benefits of `Runnable` over `Thread`.
*   **Modern Concurrency:** While understanding the basic `Thread` and `Runnable` model is essential, modern high-performance Java applications rarely create and manage threads manually. They use the **Executor Framework** (`java.util.concurrent` package), which manages a pool of threads for you. This is much more efficient and robust. Think of it as hiring a professional restaurant manager (Executor) to handle your chefs (threads) instead of trying to coordinate them all yourself.
*   **GUI Applications:** Multithreading is critical for desktop and mobile applications. A long-running task (like a network download or complex calculation) should **never** be run on the main UI thread (like the Event Dispatch Thread in Swing). Doing so will freeze the user interface. Such tasks must be offloaded to a background worker thread.

**🔗Links:** [[Java Sessions 28 & 29 - Synchronization and Deadlock]]
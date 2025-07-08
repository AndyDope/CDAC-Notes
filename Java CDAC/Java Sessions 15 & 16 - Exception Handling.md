### **Sessions 15 & 16: Exception Handling**

Welcome. So far, our programs have assumed a "happy path" where everything works as expected. But in reality, errors are common: a file might not exist, a network connection could drop, or a user might enter invalid data. **Exception Handling** is Java's powerful and structured mechanism for managing these runtime errors, allowing you to create resilient applications that can recover from unexpected situations gracefully instead of crashing.

---

#### **1. Exception Hierarchy, Errors, and Exception Types**

In Java, all exception and error types are subclasses of the `Throwable` class. The hierarchy has two main branches:

*   **`Error`**: Represents serious problems that a reasonable application should not try to catch. These are typically unrecoverable issues with the JVM itself, such as `OutOfMemoryError` or `StackOverflowError`. Your program will usually crash.

*   **`Exception`**: Represents conditions that a reasonable application *might* want to catch. This is the category we will focus on. The `Exception` class is further divided into two types:

    1.  **Checked Exceptions**: These are exceptions that a well-written application should anticipate and recover from. The Java compiler **checks** at compile-time that you have handled them. If a method can throw a checked exception, it must either handle it with a `try-catch` block or declare it with the `throws` keyword.
        *   **Examples:** `IOException` (e.g., file not found), `SQLException` (database error).

    2.  **Unchecked Exceptions (Runtime Exceptions)**: These are exceptions that typically result from programming errors, such as bugs in your code logic. The compiler does **not** force you to handle them.
        *   They are subclasses of `RuntimeException`.
        *   **Examples:** `NullPointerException` (accessing a `null` reference), `ArrayIndexOutOfBoundsException` (using an invalid array index), `ArithmeticException` (e.g., division by zero).

**Analogy:**
*   **`Error`:** The foundation of your house collapses. There's nothing you can do; it's a disaster.
*   **Checked Exception:** You try to unlock your front door, but you have the wrong key (`FileNotFoundException`). This is a foreseeable problem. You should have a plan: check your pockets for the right key (`try-catch`) or tell someone you don't have it (`throws`).
*   **Unchecked Exception:** You walk into a wall in your own house (`NullPointerException`). This is a silly mistake (a bug) that you shouldn't have made in the first place. There's no "plan" for this; you should just fix the bug.

> **Quick Question:** What is the fundamental difference between a checked and an unchecked exception regarding the compiler?
> **Answer:** The compiler forces you to handle checked exceptions, either by catching them or declaring that your method throws them. It does not enforce any handling for unchecked exceptions.

---

#### **2. `try`, `catch`, `finally`, `throw`, `throws`**

These five keywords are the building blocks of Java exception handling.

*   **`try`**: The `try` block encloses the code that might throw an exception.
*   **`catch`**: The `catch` block contains the code to handle the exception. It is executed only if an exception of the specified type (or its subclass) occurs in the `try` block. You can have multiple `catch` blocks for different exception types.
*   **`finally`**: The `finally` block contains code that **always** executes, whether an exception was thrown or not. It is used for cleanup activities, like closing files or network connections, to ensure resources are not leaked.
*   **`throw`**: The `throw` keyword is used to manually throw an exception. You can throw an instance of any `Throwable` class.
*   **`throws`**: The `throws` keyword is used in a method signature to declare that the method might throw one or more checked exceptions. This passes the responsibility of handling the exception up to the calling method.

**Example:**
```java
import java.io.FileReader;
import java.io.IOException;

public class ExceptionDemo {
    // This method DECLARES that it might throw an IOException
    public static void readFile(String fileName) throws IOException {
        FileReader reader = null;
        try {
            // 1. TRY block: Code that might fail
            reader = new FileReader(fileName);
            System.out.println("File opened successfully.");
            // ... code to read the file ...

        } finally {
            // 3. FINALLY block: Always runs for cleanup
            System.out.println("Finally block executed.");
            if (reader != null) {
                reader.close(); // Ensure the reader is always closed
            }
        }
    }

    public static void main(String[] args) {
        try {
            readFile("nonexistent.txt");
        } catch (IOException e) {
            // 2. CATCH block: Handles the exception thrown by readFile
            System.err.println("An error occurred: " + e.getMessage());
        }
    }
}
```

---

#### **3. Creating User-Defined Exceptions**

You can create your own custom exception classes to represent problems specific to your application's domain.

*   To create a **checked** exception, extend the `Exception` class.
*   To create an **unchecked** exception, extend the `RuntimeException` class.

It's good practice to provide at least two constructors: a default constructor and one that accepts a message `String`.

**Example:**
```java
// A custom checked exception
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message); // Pass the message to the parent Exception class
    }
}

class BankAccount {
    private double balance;

    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            // Manually THROW our custom exception
            throw new InsufficientFundsException("Withdrawal amount exceeds balance.");
        }
        balance -= amount;
        System.out.println("Withdrawal successful.");
    }
}
```

---

### **Topic Summary & Revision**

*   **Hierarchy:** `Throwable` -> `Error` (unrecoverable) and `Exception`.
*   **Exception Types:**
    *   **Checked:** Must be handled (`try-catch`) or declared (`throws`). For predictable, recoverable errors (e.g., `IOException`).
    *   **Unchecked (Runtime):** Not enforced by the compiler. For programming bugs (e.g., `NullPointerException`).
*   **Keywords:**
    *   `try`: Code that might throw an exception.
    *   `catch`: Code that handles an exception.
    *   `finally`: Code that always runs (for cleanup).
    *   `throw`: To manually fire an exception.
    *   `throws`: To declare that a method might pass an exception up.
*   **Custom Exceptions:** Create your own by extending `Exception` (checked) or `RuntimeException` (unchecked).

---

### **MCQs for Exam Preparation (Tricky)**

1.  **What is the output of the following code?**
```java
public class Test {
	public static int getNumber() {
		try {
			return 1;
		} catch (Exception e) {
			return 2;
		} finally {
			return 3;
		}
	}
	public static void main(String[] args) {
		System.out.println(getNumber());
	}
}
```
(A) 1
(B) 2
(C) 3
(D) Compilation Error
**Answer:** ||(C) 3. This is a classic trick question. If a 'finally' block contains a 'return' statement, it will override any 'return' statement from the 'try' or 'catch' blocks. The 'finally' block is always executed just before the method exits, so its return value takes precedence.||
<br>

2.  **A method attempts to parse a string to an integer using `Integer.parseInt(str)`. This can throw a `NumberFormatException`. `NumberFormatException` is a subclass of `RuntimeException`. Which of the following statements is true?**
    (A) The method must include a `try-catch` block for `NumberFormatException`.
    (B) The method must be declared with `throws NumberFormatException`.
    (C) The compiler will not force the developer to handle the exception.
    (D) The `finally` block is the only place to handle this exception.
    **Answer:** ||(C) Since 'NumberFormatException' is a 'RuntimeException' (an unchecked exception), the compiler does not enforce handling. While it is good practice to handle it if the input string is untrusted, it is not a compile-time requirement.||
<br>

3.  **Which of the following exception types would be most appropriate for a situation where a user tries to create an account with a username that already exists in the database?**
    (A) A built-in `IllegalArgumentException`.
    (B) A custom checked exception like `UsernameAlreadyExistsException extends Exception`.
    (C) A built-in `RuntimeException`.
    (D) A built-in `Error`.
    **Answer:** ||(B) This is a predictable, application-specific business rule violation, not a low-level programming error. Creating a custom checked exception makes the API clear and forces the caller to handle this specific, foreseeable scenario. 'IllegalArgumentException' (A) is plausible but less specific.||
<br>

4.  **What happens if an exception is thrown in a `try` block, and there is no matching `catch` block in the method?**
    (A) The `finally` block is skipped, and the program crashes.
    (B) The program terminates immediately.
    (C) The `finally` block (if present) is executed, and then the exception propagates up the call stack to the calling method.
    (D) It results in a compilation error.
    **Answer:** ||(C) The 'finally' block's guarantee is very strong. It will execute, and then the exception handling mechanism will continue its search for a suitable 'catch' block in the calling methods, moving up the call stack. If it reaches the top of the 'main' thread without being caught, the program will terminate.||
<br>

5.  **Which statement about the `Error` class hierarchy is correct?**
    (A) Errors are a type of checked exception that must always be handled.
    (B) Applications are encouraged to catch `Error` objects to attempt recovery.
    (C) An `Error` typically signifies a critical failure in the JVM or system resources, from which an application cannot realistically recover.
    (D) `StackOverflowError` is a common `Exception` that should be caught.
    **Answer:** ||(C) 'Error's like 'OutOfMemoryError' or 'StackOverflowError' indicate that something has gone fundamentally wrong with the environment the application is running in. They are not meant to be caught or handled by application logic. 'StackOverflowError' is an 'Error', not an 'Exception' (D is wrong).||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A great follow-up question to "What is a checked vs. unchecked exception?" is **"When would you choose to create one over the other?"** The answer: "Create a **checked exception** for recoverable conditions that are part of the business logic and you want to force the calling API to handle (e.g., `InsufficientFundsException`). Create an **unchecked exception** for programming errors that indicate a bug that should be fixed, not handled (e.g., passing a `null` argument where it's not allowed)."
*   **Clean Code:** Avoid catching the generic `Exception` class (`catch (Exception e)`) whenever possible. Always catch the most specific exception type you can. This prevents you from accidentally catching unexpected exceptions and makes the code's intent clearer.
*   **Modern Resource Management:** As mentioned in [[Java Session 12 - Garbage collection|Session 12]], the `try-with-resources` statement is the best way to handle resources that need to be closed. It implicitly uses a `finally` block to guarantee the resource is closed, resulting in cleaner and safer code.

**🔗Links:** [[Java Session 17 - java.io & java.nio Package]]
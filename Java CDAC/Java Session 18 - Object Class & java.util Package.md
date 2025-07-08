### **Session 18: Object Class & java.util Package**

Welcome to Session 18. This session covers two fundamental topics. First, we'll explore the `java.lang.Object` class, which sits at the very top of the class hierarchy; every class in Java is its descendant. Understanding its core methods is key to understanding how all objects behave. Second, we'll get an introduction to the `java.util` package, a treasure trove of utility classes, focusing on those for handling dates and times.

---

#### **1. The `Object` Class**

In Java, every class, whether you write it or it comes from the standard library, implicitly or explicitly extends the `Object` class. It is the root of the class hierarchy. This means every object in Java inherits the methods of the `Object` class.

Three of the most important methods to know and often override are:

##### **a) `toString()`**
*   **Default Behavior:** Returns a `String` representation of the object, which is typically the class name followed by `@` and the object's hash code in hexadecimal (e.g., `Employee@1f32e575`). This is usually not very useful.
*   **Overriding:** You should override `toString()` in your classes to provide a meaningful, human-readable string representation of the object's state. This is invaluable for logging and debugging.

```java
class Employee {
    String name;
    int id;
    // constructor...

    @Override
    public String toString() {
        return "Employee[ID=" + id + ", Name=" + name + "]";
    }
}
// System.out.println(myEmployeeObject); // Prints "Employee[ID=101, Name=Ravi]"
```

##### **b) `equals(Object obj)`**
*   **Default Behavior:** In the `Object` class, `equals()` behaves exactly like the `==` operator. It checks for **reference equality** (do two references point to the exact same object in memory?).
*   **Overriding:** You must override `equals()` to define **logical equality** (do two different objects have the same state or value?). When you override `equals()`, you should always override `hashCode()` as well.

##### **c) `hashCode()`**
*   **Default Behavior:** Returns an integer hash code value for the object, typically based on its memory address.
*   **The `equals()` and `hashCode()` Contract:**
    1.  If two objects are equal according to the `equals()` method, then they **must** have the same hash code.
    2.  If two objects have the same hash code, they are **not** required to be equal. (This is called a hash collision).
*   **Why?** This contract is essential for the correct functioning of hash-based collections like `HashMap` and `HashSet`. These collections use `hashCode()` to quickly find the "bucket" where an object should be, and then use `equals()` to find the object within that bucket. If you break this contract, you will get strange and incorrect behavior when using these collections.

---

#### **2. `java.util` Package**

The `java.util` package contains the collections framework, legacy collection classes, event model, date and time facilities, internationalization, and miscellaneous utility classes. We will focus on the Date and Time classes here.

---

#### **3. Legacy Date and Time Classes**

These are the older date/time classes that you will frequently encounter in legacy code. They are generally considered poorly designed and have been superseded by the `java.time` API in Java 8.

*   **`java.util.Date`**: Represents a specific instant in time, with millisecond precision. It is mutable, which is a major design flaw.
*   **`java.util.Calendar`**: An abstract class for converting between a `Date` object and a set of integer fields like `YEAR`, `MONTH`, `DAY_OF_MONTH`. It is complex and difficult to use correctly.
*   **`java.text.SimpleDateFormat`**: A class for formatting and parsing dates in a specific format (e.g., "dd/MM/yyyy"). It is notoriously not thread-safe.

**Example: Converting String to Date**
```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class LegacyDateDemo {
    public static void main(String[] args) {
        String dateString = "25/12/2023";
        // Define the format that matches the string
        SimpleDateFormat formatter = new SimpleDateFormat("dd/MM/yyyy");
        
        try {
            Date date = formatter.parse(dateString); // Parsing: String -> Date
            System.out.println(date);

            String formattedString = formatter.format(date); // Formatting: Date -> String
            System.out.println(formattedString);
            
        } catch (ParseException e) {
            System.err.println("Failed to parse date: " + e.getMessage());
        }
    }
}
```

---

#### **4. Modern Date and Time API (Java 8+) - `java.time`**

Introduced in Java 8, the `java.time` package is a much-improved API for handling dates and times.

**Key Advantages:**
*   **Immutability:** All classes in `java.time` are immutable, just like `String`, making them thread-safe and predictable.
*   **Clarity:** It separates concepts clearly. `LocalDate` for a date, `LocalTime` for a time, and `LocalDateTime` for both.
*   **Fluent API:** The API is easy to read and use.

**Core Classes:**
*   `LocalDate`: Represents a date without time or timezone (e.g., `2023-12-25`).
*   `LocalTime`: Represents a time without a date or timezone (e.g., `10:15:30`).
*   `LocalDateTime`: A combination of date and time without a timezone.
*   `DateTimeFormatter`: The modern, thread-safe way to format and parse dates and times.

**Example: Using `java.time`**
```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

public class ModernDateDemo {
    public static void main(String[] args) {
        String dateString = "25/12/2023";
        
        // Define the formatter
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        
        // Parsing: String -> LocalDate
        LocalDate date = LocalDate.parse(dateString, formatter);
        System.out.println(date); // Prints in standard ISO format: 2023-12-25
        
        // Formatting: LocalDate -> String
        String formattedString = date.format(formatter);
        System.out.println(formattedString); // Prints: 25/12/2023
        
        // Performing operations returns a new object
        LocalDate nextDay = date.plusDays(1);
        System.out.println("Next day is: " + nextDay);
    }
}
```

---

### **Topic Summary & Revision**

*   **`Object` Class:** The ultimate ancestor of all Java classes.
*   **`toString()`:** Override to provide a meaningful string representation of an object.
*   **`equals()`:** Override to check for logical equality (same state). By default, it checks for reference equality (`==`).
*   **`hashCode()`:** Override to produce a hash code based on an object's state.
*   **`equals()`/`hashCode()` Contract:** If `a.equals(b)` is true, then `a.hashCode()` must equal `b.hashCode()`.
*   **Legacy Date/Time:** `Date`, `Calendar`, `SimpleDateFormat`. They are mutable and complex; avoid in new code.
*   **Modern Date/Time (`java.time`):** `LocalDate`, `LocalTime`, `LocalDateTime`, `DateTimeFormatter`. They are immutable, clear, and thread-safe. **Always prefer these for new development.**

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A `HashSet` is used to store `Employee` objects. The `Employee` class has correctly overridden the `equals()` method but has NOT overridden the `hashCode()` method. What will happen when you add two `Employee` objects that are logically equal?**
    (A) The `HashSet` will contain only one `Employee` object, as expected.
    (B) The `HashSet` will contain two `Employee` objects, incorrectly treating them as distinct.
    (C) A `RuntimeException` will be thrown when adding the second object.
    (D) The code will fail to compile.
    **Answer:** ||(B) This breaks the 'equals() / hashCode()' contract. Because 'hashCode()' is not overridden, it uses the default implementation from 'Object', which usually relies on memory address. The two logically equal objects are at different addresses, so they produce different hash codes. The 'HashSet' places them in different "buckets" and never even calls 'equals()' to compare them. Thus, the set incorrectly contains duplicates.||
<br>

2.  **You have a `Map<Employee, String>`. To use the `Employee` object as a key, which method(s) are essential to override correctly in the `Employee` class?**
    (A) Only `equals(Object obj)`
    (B) Only `hashCode()`
    (C) Both `equals(Object obj)` and `hashCode()`
    (D) `toString()`
    **Answer:** ||(C) For any hash-based collection ('HashMap', 'HashSet', 'Hashtable'), both 'equals()' and 'hashCode()' must be correctly implemented according to their contract. 'hashCode()' is used to find the bucket quickly, and 'equals()' is used to handle collisions within that bucket.||
<br>

3.  **Which statement is true about the legacy `java.util.Date` class?**
    (A) It is immutable, and its methods are thread-safe.
    (B) It is mutable, which is a major design flaw that can lead to bugs.
    (C) It can only represent a date, not a time.
    (D) It has been completely removed in Java 8 and replaced by `LocalDate`.
    **Answer:** ||(B) The 'Date' class has methods like 'setTime()' which can change the state of the object after creation. This mutability makes it difficult to use safely in a multi-threaded environment or as a key in a map. It has not been removed (D is wrong) for backward compatibility.||
<br>

4.  **What is the result of calling `System.out.println(new Object());`?**
    (A) "Object"
    (B) `null`
    (C) A `String` containing the class name, an `@` sign, and the object's hash code.
    (D) An empty string.
    **Answer:** ||(C) This invokes the default 'toString()' method inherited from the 'Object' class, which produces a representation like 'java.lang.Object@1f32e575'.||
<br>

5.  **Which class from the `java.time` API would you use to represent a recurring event like a birthday, without a specific year?**
    (A) `LocalDate`
    (B) `YearMonth`
    (C) `MonthDay`
    (D) `Instant`
    **Answer:** ||(C) 'MonthDay' is specifically designed to represent a day of a month without a year, making it perfect for recurring annual events. 'LocalDate' requires a year. 'Instant' represents a specific point on the timeline.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The `equals()` and `hashCode()` contract is a deeply fundamental Java topic. Interviewers love it. Be prepared to not only state the contract but also explain *why* it's important (for hash-based collections).
*   **Best Practice:** When you create a new entity class (like `Employee`, `Student`, `Product`), get into the habit of immediately overriding `toString()`, `equals()`, and `hashCode()`. Modern IDEs like IntelliJ and Eclipse can automatically generate correct and robust implementations for you.
*   **Date/Time:** For any new code, forget that `java.util.Date` and `Calendar` exist. Start directly with the `java.time` API. If you have to interact with a legacy API that returns a `Date` object, convert it to a modern `java.time` object immediately, do your work, and then convert it back only if you have to.

**🔗Links:** [[Java Sessions 19, 20, 21 & 22 - Collections]]
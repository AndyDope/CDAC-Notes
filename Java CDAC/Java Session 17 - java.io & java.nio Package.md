### **Session 17: java.io & java.nio Package**

Welcome to Session 17. So far, our programs have mostly interacted with the console. To build real applications, we need to read from and write to external sources like files. Java provides a rich and flexible set of APIs for this, primarily located in the `java.io` and `java.nio` packages. We will also explore the powerful concept of **Serialization**, which allows us to convert objects into a byte stream to be stored or transmitted.

---

#### **1. Brief Introduction to I/O Streams**

In Java, I/O is based on the concept of **streams**. A stream is a sequence of data flowing from a source to a destination.

*   **Input Stream:** Reads data from a source (e.g., a file, the network, the keyboard).
*   **Output Stream:** Writes data to a destination (e.g., a file, the network, the console).

Java's I/O streams are divided into two main hierarchies:
1.  **Byte Streams:** Used for reading and writing binary data (streams of bytes). Their abstract base classes are `InputStream` and `OutputStream`.
2.  **Character Streams:** Used for reading and writing text data (streams of characters). They automatically handle character encoding. Their abstract base classes are `Reader` and `Writer`.

**Rule of Thumb:** Use character streams for text files (`.txt`, `.java`, `.html`) and byte streams for everything else (`.jpg`, `.zip`, `.exe`).

---

#### **2. `java.io` Package and Decorator Pattern**

The `java.io` package uses the **Decorator Pattern** extensively. This means you "wrap" a basic stream with other streams to add more functionality.

**Example: Reading a text file efficiently.**
You don't just use one class; you combine them.

1.  **`FileInputStream` (a byte stream):** This is the basic stream that connects directly to the file on the disk.
2.  **`InputStreamReader`:** This "wraps" or "decorates" the `FileInputStream` to convert the raw bytes into characters.
3.  **`BufferedReader`:** This "wraps" the `InputStreamReader` to add buffering. Buffering makes reading much more efficient by reading large chunks of the file into memory at once, instead of one character at a time.

```java
import java.io.*;

public class FileReaderExample {
    public static void main(String[] args) {
        // Modern approach using try-with-resources to ensure the file is closed
        try (BufferedReader reader = new BufferedReader(new FileReader("mydata.txt"))) {
            String line;
            // The readLine() method is a convenient feature of BufferedReader
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.err.println("Error reading file: " + e.getMessage());
        }
    }
}
```
*   `FileReader` is a convenience class that combines `FileInputStream` and `InputStreamReader`.
*   The `try-with-resources` statement automatically calls the `close()` method on the `reader` object, which is the best practice for handling I/O resources.

> **Quick Question:** Why is it more efficient to wrap a `FileReader` in a `BufferedReader`?
> **Answer:** Because `BufferedReader` reads data in large blocks (buffers) from the disk, which significantly reduces the number of slow disk I/O operations compared to reading one character at a time.

---

#### **3. `java.nio` Package**

Introduced in Java 1.4, `java.nio` (New I/O) provides a more modern and higher-performance alternative to `java.io`. It is based on three core concepts:

*   **Channels:** Analogous to streams, a channel is a connection to an I/O source.
*   **Buffers:** A block of memory into which data is read or from which data is written. You interact directly with the buffer, not the channel.
*   **Selectors:** A mechanism for non-blocking I/O, allowing a single thread to manage multiple channels. (This is an advanced topic, mainly used in high-performance networking).

While `java.nio` can be more complex, it offers performance advantages, especially for large files and network applications. The `java.nio.file` package (Java 7+) provides a much-improved API for file system operations (`Files`, `Paths`).

---

#### **4. Serialization and Deserialization**

**Serialization** is the process of converting a Java object's state into a byte stream. This byte stream can then be saved to a file, stored in a database, or sent across a network.
**Deserialization** is the reverse process: converting a byte stream back into a copy of the original object.

**How to make a class serializable:**
A class must implement the `java.io.Serializable` interface. This is a **marker interface**—it has no methods to implement. It simply "marks" the class to the JVM as being eligible for serialization.

*   **`ObjectOutputStream`**: Used to serialize (write) an object.
*   **`ObjectInputStream`**: Used to deserialize (read) an object.
*   **`transient` keyword**: If you have a field in your class that you **do not** want to be serialized (e.g., a password or a temporary value), you can mark it as `transient`.

**Example:**
```java
import java.io.*;

// 1. The class MUST implement Serializable
class User implements Serializable {
    private static final long serialVersionUID = 1L; // Version UID for the class
    String username;
    transient String password; // This field will NOT be serialized

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }
}

public class SerializationDemo {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        User user = new User("admin", "pa$$w0rd");

        // --- Serialization ---
        FileOutputStream fos = new FileOutputStream("user.dat");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(user);
        oos.close();
        System.out.println("User object serialized. Password will be null.");

        // --- Deserialization ---
        FileInputStream fis = new FileInputStream("user.dat");
        ObjectInputStream ois = new ObjectInputStream(fis);
        User deserializedUser = (User) ois.readObject();
        ois.close();

        System.out.println("Username: " + deserializedUser.username); // "admin"
        System.out.println("Password: " + deserializedUser.password); // null
    }
}
```
The `serialVersionUID` is a unique ID used to verify that the sender and receiver of a serialized object have loaded classes for that object that are compatible with respect to serialization.

> **Quick Question:** What is the purpose of the `transient` keyword?
> **Answer:** To prevent a field from being included in the serialization process.

---

#### **5. Shallow Copy and Deep Copy**

This concept is related to object duplication.
*   **Shallow Copy:** Copies the top-level fields. If a field is a reference to another object, only the **reference is copied**, not the object itself. Both the original and the copy will point to the *same* nested object.
*   **Deep Copy:** Creates a completely independent copy of the object and all objects it refers to. The original and the copy are fully decoupled.

Serialization is one of the easiest ways to perform a **deep copy** of a complex object graph.

---

### **Topic Summary & Revision**

*   **Streams:** Java I/O is based on streams, which are sequences of data. Use **Character Streams** (`Reader`/`Writer`) for text and **Byte Streams** (`InputStream`/`OutputStream`) for binary data.
*   **`java.io`:** Uses a decorator pattern. Wrap basic streams (like `FileReader`) in more functional ones (like `BufferedReader`) for efficiency and convenience.
*   **`try-with-resources`:** The standard, safe way to handle I/O resources to ensure they are always closed.
*   **Serialization:** The process of converting an object to a byte stream. A class must implement the `Serializable` marker interface.
*   **`transient`:** A keyword to exclude a field from serialization.
*   **`ObjectOutputStream` / `ObjectInputStream`:** The primary classes for serializing and deserializing objects.
*   **Shallow vs. Deep Copy:** Shallow copy duplicates references; deep copy duplicates the objects themselves.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A developer needs to read a large text file that contains non-English characters (e.g., Unicode). Which combination of classes from `java.io` is most appropriate and efficient?**
    (A) `FileInputStream`
    (B) `FileInputStream` wrapped in a `BufferedInputStream`
    (C) `FileReader` wrapped in a `BufferedReader`
    (D) `DataInputStream`
    **Answer:** ||(C) 'FileReader' handles the conversion from bytes to characters (necessary for Unicode text), and 'BufferedReader' adds efficient buffered reading. 'FileInputStream' (A and B) deals with raw bytes and does not correctly handle character encodings. 'DataInputStream' (D) is for reading primitive Java data types, not text lines.||
<br>

2.  **A class `Employee` implements `Serializable`. It contains a field `private Address address;`. The `Address` class does NOT implement `Serializable`. What happens when you try to serialize an `Employee` object?**
    (A) The `Employee` object is serialized, but the `address` field is skipped, similar to a `transient` field.
    (B) The code fails to compile.
    (C) A `java.io.NotSerializableException` is thrown at runtime.
    (D) The `address` object's `toString()` method is serialized instead.
    **Answer:** ||(C) For an object to be serialized, all of its non-transient instance fields must also be serializable. Since the 'Address' object is not serializable, the JVM will throw a 'NotSerializableException' at runtime when it attempts to serialize the 'Employee' object.||
<br>

3.  **What is the primary role of the `Serializable` interface?**
    (A) It provides the `serialize()` method that all implementing classes must override.
    (B) It is a marker interface that signals to the JVM that a class can be serialized.
    (C) It contains constants that define the serialization protocol.
    (D) It provides default methods for performing deep and shallow copies.
    **Answer:** ||(B) 'Serializable' is a classic example of a marker interface. It has no methods. Its presence simply acts as a 'tag' or 'marker' to tell the serialization mechanism that the developer has opted-in this class to the serialization process.||
<br>

4.  **A `try-with-resources` block is used to manage a `FileOutputStream`. Which statement is true?**
    ```java
    try (FileOutputStream fos = new FileOutputStream("out.txt")) {
        // ... write data ...
    }
    ```
    (A) The `fos.close()` method is guaranteed to be called only if the `try` block completes successfully.
    (B) The developer must explicitly call `fos.close()` in a `finally` block.
    (C) The `fos.close()` method is guaranteed to be called when the `try` block is exited, whether it completes normally or with an exception.
    (D) The `FileOutputStream` object will be closed by the Garbage Collector.
    **Answer:** ||(C) This is the entire purpose of 'try-with-resources'. The compiler generates the necessary 'finally' block behind the scenes to ensure 'close()' is called, making the code cleaner and safer than manual 'finally' blocks.||
<br>

5.  **You serialize an object of class `Person` to a file. Later, you add a new non-transient field to the `Person` class and recompile it. What happens when you try to deserialize the old file?**
    (A) It works perfectly, and the new field is initialized to its default value.
    (B) A `NullPointerException` is thrown.
    (C) A `java.io.InvalidClassException` is thrown because the `serialVersionUID`s do not match.
    (D) It works, but you get a compiler warning.
    **Answer:** ||(C) When a class structure changes, its default 'serialVersionUID' also changes. During deserialization, the JVM compares the 'serialVersionUID' of the class in the stream with the 'serialVersionUID' of the current class definition. If they don't match, it throws an 'InvalidClassException' to prevent data corruption. This is why explicitly defining a 'serialVersionUID' is important for long-term persistence.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The `Serializable`/`transient` question (MCQ #2) is a classic. A good follow-up is, "What if you really must serialize the `Employee` but the `Address` class is from a third-party library and cannot be changed?" The answer: "You would have to mark the `address` field as `transient` and then manually implement the `writeObject()` and `readObject()` methods to handle the serialization and deserialization of the address fields yourself."
*   **Security:** Be very cautious when deserializing data from untrusted sources. A malicious payload can be crafted to exploit vulnerabilities in the deserialization process, leading to remote code execution. This is a well-known security risk.
*   **Modern I/O:** For new file I/O code, prefer the `java.nio.file` API (`Files` and `Paths` classes). It provides a much more powerful and intuitive way to work with files and directories than the old `java.io.File` class. For example: `Files.readAllLines(Paths.get("myfile.txt"))`.

**🔗Links:** [[Java Session 18 - Object Class & java.util Package]]
### **Sessions 23, 24, 25 & 26: Collections Continued (Map, Stream API)**

Welcome back. In our previous lesson, we explored the `Collection` hierarchy (`List`, `Set`, `Queue`). Now, we turn to the other major part of the framework: the **`Map` interface**. Maps are indispensable for storing key-value associations. We will also cover one of the most significant additions to Java in the last decade: the **Stream API** (introduced in Java 8), which provides a powerful, declarative way to process collections of data.

---

#### **1. The `Map` Interface: Key-Value Pairs**

A `Map` is an object that maps keys to values. Each key can map to at most one value. It does not allow duplicate keys.

*   **Structure:** A `Map` is a collection of `Map.Entry` objects, where each entry contains a key and a value.
*   **Relationship to `Collection`:** A `Map` is **not** a subtype of the `Collection` interface because it has a different structure. However, it is a core part of the Collections Framework.
*   **Key Uniqueness:** Like a `Set`, a `Map` relies on the `hashCode()` and `equals()` methods of its keys to ensure uniqueness.

**Core Methods:**
*   `V put(K key, V value)`: Associates the specified value with the specified key. If the map previously contained a mapping for the key, the old value is replaced.
*   `V get(Object key)`: Returns the value to which the specified key is mapped, or `null` if the map contains no mapping for the key.
*   `V remove(Object key)`: Removes the mapping for a key if it is present.
*   `boolean containsKey(Object key)`: Returns `true` if the map contains a mapping for the specified key.
*   `Set<K> keySet()`: Returns a `Set` view of the keys contained in the map.
*   `Collection<V> values()`: Returns a `Collection` view of the values.
*   `Set<Map.Entry<K, V>> entrySet()`: Returns a `Set` view of the key-value mappings. This is the most efficient way to iterate over a map.

##### **a) `HashMap`**
*   **Underlying Data Structure:** A hash table.
*   **Performance:** **Excellent**. `put()`, `get()`, and `remove()` are, on average, O(1) constant-time operations.
*   **Order:** Makes **no guarantees** about the iteration order.
*   **Keys/Values:** Allows one `null` key and multiple `null` values.
*   **When to use:** The default choice for a map. Use whenever you need fast key-based lookups and don't care about order.

```java
Map<String, Integer> studentScores = new HashMap<>();
studentScores.put("Ravi", 95);
studentScores.put("Priya", 98);
studentScores.put("Amit", 87);

int priyasScore = studentScores.get("Priya"); // 98

// Efficient iteration using entrySet
for (Map.Entry<String, Integer> entry : studentScores.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

##### **b) `LinkedHashMap`**
*   **Underlying Data Structure:** A hash table and a linked list.
*   **Key Difference:** Maintains **insertion order**. When you iterate, entries appear in the order they were added.
*   **When to use:** Use when you need the speed of a `HashMap` but also require predictable, insertion-ordered iteration.

##### **c) `TreeMap`**
*   **Underlying Data Structure:** A red-black tree.
*   **Key Difference:** Stores entries in **sorted order** based on the natural ordering of the keys (or a `Comparator` provided at creation).
*   **Requirements:** Keys must implement `Comparable` or a `Comparator` must be supplied.
*   **When to use:** Use when you need a map that is always sorted by its keys.

##### **d) `Hashtable` (Legacy)**
*   **Key Difference:** `Hashtable` is **synchronized** (thread-safe), whereas `HashMap` is not.
*   **Keys/Values:** Does **not** allow `null` keys or `null` values.
*   **Status:** `Hashtable` is a legacy class. For new, thread-safe map implementations, you should use `ConcurrentHashMap` which offers much better performance.

---

#### **2. Introduction to the Stream API (Java 8+)**

The Stream API provides a new, powerful way to process sequences of elements. A stream is **not** a data structure that stores elements; it is a pipeline through which data flows and is processed.

**Key Characteristics of Streams:**
*   **Declarative:** You describe *what* you want to do, not *how* to do it (e.g., "filter out the even numbers," not "create a new list, loop through the old list, check if a number is even, then add it to the new list").
*   **Pipelining:** Most stream operations return another stream, allowing you to chain operations together into a pipeline.
*   **Lazy Evaluation:** Intermediate operations (like `filter` or `map`) are not executed until a terminal operation (like `collect` or `forEach`) is invoked.
*   **Non-interfering:** A stream does not modify its underlying data source (the original collection).

**Structure of a Stream Pipeline:**
1.  **Source:** Create a stream from a collection (e.g., `myList.stream()`).
2.  **Intermediate Operations (0 or more):** Transform the stream into another stream. These are lazy.
    *   `filter(predicate)`: Filters elements based on a condition.
    *   `map(function)`: Transforms each element into another element.
    *   `sorted()`: Sorts the elements.
    *   `distinct()`: Returns a stream with unique elements.
3.  **Terminal Operation (1):** Produces a result or a side-effect. This triggers the execution of the entire pipeline.
    *   `collect(collector)`: Gathers the stream elements into a collection (e.g., `ToList`, `ToSet`).
    *   `forEach(consumer)`: Performs an action for each element.
    *   `count()`: Returns the number of elements in the stream.
    *   `reduce()`: Combines stream elements into a single summary result.

**Example: Processing a list of numbers**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// Goal: Find the sum of the squares of all the even numbers.

// --- The old way (imperative) ---
int sum = 0;
for (int n : numbers) {
    if (n % 2 == 0) {
        int square = n * n;
        sum += square;
    }
}
System.out.println("Imperative sum: " + sum);


// --- The new way (declarative with Streams) ---
int streamSum = numbers.stream()                       // 1. Source
    .filter(n -> n % 2 == 0)             // 2. Intermediate Op: only even numbers
    .mapToInt(n -> n * n)                // 2. Intermediate Op: square each one
    .sum();                              // 3. Terminal Op: sum them up

System.out.println("Declarative sum: " + streamSum);
```

> **Quick Question:** What is the difference between an intermediate and a terminal stream operation?
> **Answer:** An intermediate operation returns a new stream and is lazily executed. A terminal operation produces a final result (like a value or a collection) or a side-effect, and it triggers the processing of the entire stream pipeline.

---

#### **3. Generics and Wildcards**

Generics allow us to create type-safe collections. Wildcards add flexibility.

*   **`? extends SomeClass` (Upper Bounded Wildcard):**
    *   Represents an unknown type that is a subtype of `SomeClass` (or `SomeClass` itself).
    *   Use when you want to **read** from a generic structure (Producer). You can safely get a `SomeClass` object from it. `List<? extends Number>` can hold `List<Integer>` or `List<Double>`. You can get a `Number` from it, but you cannot `add` anything to it (except `null`).
*   **`? super SomeClass` (Lower Bounded Wildcard):**
    *   Represents an unknown type that is a supertype of `SomeClass`.
    *   Use when you want to **write** to a generic structure (Consumer). You can safely add an object of type `SomeClass` (or its subtypes) to it. `List<? super Integer>` can hold `List<Integer>`, `List<Number>`, or `List<Object>`. You can `add` an `Integer` to it.
*   **`?` (Unbounded Wildcard):**
    *   Represents an unknown type. `List<?>` means "a list of something." It is mostly useful when the type does not matter.

**PECS Principle:** **P**roducer **E**xtends, **C**onsumer **S**uper.

---

### **Topic Summary & Revision**

*   **`Map`:** Stores key-value pairs. Not part of the `Collection` hierarchy but a core part of the JCF.
    *   `HashMap`: Fastest, unordered. The default choice.
    *   `LinkedHashMap`: Maintains insertion order.
    *   `TreeMap`: Maintains sorted order by key.
*   **Stream API:** A declarative, functional-style API for processing collections.
    *   **Pipeline:** Source -> Intermediate Ops -> Terminal Op.
    *   **Intermediate Ops:** Lazy operations like `filter()`, `map()`.
    *   **Terminal Ops:** Eager operations like `collect()`, `forEach()`, `sum()`.
*   **Generics & Wildcards:**
    *   `? extends T`: Upper bound, for reading (Producer).
    *   `? super T`: Lower bound, for writing (Consumer).

---

### **MCQs for Exam Preparation (Tricky)**

1.  **You need a collection to store country codes (like "IN") and their corresponding full names (like "India"). You will be performing frequent lookups by country code. Which is the most appropriate collection?**
    (A) `ArrayList<String>`
    (B) `HashMap<String, String>`
    (C) `HashSet<String>`
    (D) `TreeMap<String, String>`
    **Answer:** ||(B) This is a classic key-value mapping problem. A 'HashMap' provides the fastest possible lookup (O(1) average time) based on the key (the country code).||
<br>

2.  **What is the output of this code snippet?**
```java
List<String> words = Arrays.asList("a", "b", "c", "d");
words.stream()
	 .filter(s -> s.length() > 0)
	 .map(s -> s.toUpperCase());
	 
System.out.println(words.get(0));
```
(A) A
(B) a
(C) An exception is thrown.
(D) The code does not compile.
**Answer:** ||(B) a. This is a trick question about stream execution. The stream pipeline is defined but never executed because it lacks a terminal operation (like 'collect()' or 'forEach()'). Streams do not modify the source collection. Therefore, the original 'words' list remains completely unchanged.||
<br>
3.  **A method signature is `public void process(List<? extends Number> list)`. Which of the following lines of code would be INVALID inside this method?**
    (A) `Number n = list.get(0);`
    (B) `list.add(new Integer(5));`
    (C) `int size = list.size();`
    (D) `list.clear();`
    **Answer:** ||(B) This is the core rule of 'Producer Extends'. Because the list could be a 'List\<Double>', you cannot \`sd` safely add an 'Integer' to it. The compiler forbids adding anything (except 'null') to a '? extends' collection to preserve type safety. You can only read from it (get).||
<br>

4.  **You want to get a list of all unique, uppercase names from a `List<String> names`. Which stream pipeline is correct?**
    (A) `names.stream().map(String::toUpperCase).collect(Collectors.toList());`
    (B) `names.stream().distinct().map(String::toUpperCase).collect(Collectors.toList());`
    (C) `names.stream().map(String::toUpperCase).distinct().collect(Collectors.toList());`
    (D) `names.stream().filter(s -> s.isUpperCase()).collect(Collectors.toList());`
    **Answer:** ||(C) This pipeline correctly converts all names to uppercase first ('map'), then finds the unique ones among the uppercase results ('distinct'), and finally collects them into a list. (B) would find unique names in their original case first, which is incorrect if "ravi" and "Ravi" should be treated as one.||
<br>

5.  **Which statement accurately describes a key difference between `HashMap` and `Hashtable`?**
    (A) `HashMap` allows null keys and values, while `Hashtable` does not.
    (B) `Hashtable` is faster than `HashMap` due to better hashing algorithms.
    (C) `HashMap` is a legacy class, while `Hashtable` is the modern replacement.
    (D) `HashMap` is ordered by key, while `Hashtable` is unordered.
    **Answer:** ||(A) This is a fundamental difference. 'HashMap' is more flexible and allows one 'null' key and any number of 'null' values. 'Hashtable' is strict and throws a 'NullPointerException' if you attempt to use a 'null' key or value. Also, 'Hashtable' is the legacy, synchronized class.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** "Explain the stream pipeline." Be ready to describe the three stages (Source, Intermediate Ops, Terminal Op) and give examples of methods for each stage. Emphasize that intermediate operations are lazy. This demonstrates a solid understanding of how streams work.
*   **Method References:** In the stream examples, you'll often see `String::toUpperCase`. This is a **method reference**, a shorthand for the lambda `s -> s.toUpperCase()`. Using method references makes your stream pipelines even more concise and readable when you are simply calling an existing method.
*   **Choosing a Map:** The decision process is identical to choosing a `Set`: `HashMap` for speed, `LinkedHashMap` for insertion order, `TreeMap` for sorted order. The choice depends entirely on your requirements for key ordering.

**🔗Links:** [[Java Session 27 - MultiThreading]]
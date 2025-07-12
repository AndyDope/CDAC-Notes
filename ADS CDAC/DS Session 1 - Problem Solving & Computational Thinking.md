### **Session 1: Problem Solving & Computational Thinking**

Welcome to your first session on Algorithms and Data Structures. Before we dive into specific data structures like stacks or queues, we must first build the most important skill for any programmer: a structured approach to problem-solving. This session is about learning **how to think** like a computer scientist before writing a single line of code.

---

#### **1. What is Computational Thinking?**

Computational thinking is not about thinking like a computer; it's about breaking down problems in a way that a computer *could* solve them. It's a systematic approach that involves four key pillars:

*   **Decomposition:** Breaking down a large, complex problem into smaller, more manageable sub-problems.
*   **Pattern Recognition:** Identifying similarities, trends, or recurring patterns among the sub-problems. This helps in creating reusable solutions.
*   **Abstraction:** Focusing on the essential details and ignoring irrelevant information. We define *what* we need, not *how* it's done. (This is the core idea behind Abstract Data Types, or ADTs, which we will see soon).
*   **Algorithm Design:** Developing a step-by-step set of instructions to solve each sub-problem.

**Analogy: Assembling a piece of furniture.**
1.  **Decomposition:** You don't just "build it." You break it down: (1) Unpack and check parts, (2) Assemble the frame, (3) Attach the drawers, (4) Fix the handles.
2.  **Pattern Recognition:** You notice that all four legs attach in the exact same way. You don't need four different sets of instructions.
3.  **Abstraction:** You just need a "screwdriver"; you don't need to know its brand, color, or the physics of how a screw works.
4.  **Algorithm:** The instruction manual is your algorithm—a step-by-step guide to follow.

> **Quick Question:** Which pillar of computational thinking involves breaking a large problem into smaller, manageable parts?
> **Answer:** Decomposition.

---

#### **2. A Four-Step Problem-Solving Process**

A structured process ensures you don't miss critical steps. We can model problem-solving in four main stages.

##### **Step 1: Understand the Problem (Define & Identify)**
This is the most crucial step. Rushing this leads to solving the wrong problem. You must be able to answer:
*   **What is the input?** (e.g., A list of numbers, a string of text)
*   **What is the desired output?** (e.g., The largest number in the list, the string in reverse)
*   **What are the constraints or rules?** (e.g., "The numbers are integers," "Memory usage must be low," "Time to solve must be fast.")

**Example:**
*   **Problem:** Find the largest number in a list of unsorted positive integers.
*   **Input:** A list of positive integers, `L`.
*   **Output:** A single integer, `max_value`, which is the largest number in `L`.
*   **Constraint:** The list can be empty. If it is, what should we do? (Let's decide to return an error or a special value like -1).

##### **Step 2: Devise a Plan (Algorithm Design)**
Create a step-by-step plan to get from the input to the output. This plan is your **algorithm**. It should be written in a simple, language-agnostic way first. This is called **pseudocode**.

*   **Pseudocode for "Find Largest Number":**
    1.  If the list is empty, return -1.
    2.  Create a variable `max_value` and initialize it with the first number in the list.
    3.  Loop through the rest of the list, from the second number to the end.
    4.  For each number, compare it with `max_value`.
    5.  If the current number is greater than `max_value`, update `max_value` to this number.
    6.  After the loop finishes, `max_value` holds the largest number. Return it.

##### **Visual Representation: Flowchart**
A flowchart is a visual representation of an algorithm.

```bash
                  +-----------------+
                  |      Start      |
                  +-----------------+
                         |
                         V
              +--------------------+
              | Is the list empty? | --Yes--+
              +--------------------+        |
                         |                  V
                        No           +---------------+
                         |           |  Return -1    |
                         V           +---------------+
            +---------------------------+         |
            | max_value = list[0]       |         |
            | i = 1                     |         |
            +---------------------------+         |
                         |                        V
		                 V                    +-----------+
            +------------------------+        |   End     |
+---------> | Is i < list.length?    |---No-->+-----------+
|           +------------------------+
|                      |
|                     Yes
|                      |
|                      V
|         +--------------------------------+
|         | Is list[i] > max_value?        |
|         +--------------------------------+
|                |               |
|               Yes              No
|                |               |
|                V               V
|      +---------------------+   |
|      | max_value = list[i] |   |
|      +---------------------+   |
|                |_______________|
|                      |
|                      V
|            +-----------------+
|            |    i = i + 1    |
|            +-----------------+
|                      |
+----------------------+
```

##### **Step 3: Carry out the Plan (Implementation)**
Translate your pseudocode or flowchart into actual code in your chosen programming language (in our case, Java).

```java
public class ProblemSolver {
    public int findLargest(int[] numbers) {
        if (numbers == null || numbers.length == 0) {
            return -1; // Or throw an exception
        }

        int maxValue = numbers[0]; // Step 2 of pseudocode
        for (int i = 1; i < numbers.length; i++) { // Step 3
            if (numbers[i] > maxValue) { // Step 4
                maxValue = numbers[i]; // Step 5
            }
        }
        return maxValue; // Step 6
    }
}
```

##### **Step 4: Look Back (Review and Refactor)**
Once you have a working solution, review it.
*   **Is it correct?** Test it with different inputs (e.g., `[1, 5, 2]`, `[5, 1, 2]`, `[1, 2, 5]`).
*   **Does it handle edge cases?** What about an empty list? A list with one number? A list with all same numbers?
*   **Can it be improved?** Is there a more efficient way to solve it? Is the code clean and readable?

> **Quick Question:** What is the main purpose of the "Look Back" or "Review" step in problem-solving?
> **Answer:** To verify the solution's correctness, test it against edge cases, and look for opportunities to improve its efficiency or readability (refactoring).

---

### **Topic Summary & Revision**

*   **Computational Thinking:** A methodical approach to problem-solving involving **Decomposition**, **Pattern Recognition**, **Abstraction**, and **Algorithm Design**.
*   **Problem-Solving Process:** A reliable 4-step method:
    1.  **Understand:** Define inputs, outputs, and constraints.
    2.  **Plan:** Design an algorithm using pseudocode or flowcharts.
    3.  **Implement:** Write the code based on your plan.
    4.  **Review:** Test for correctness, handle edge cases, and refactor.
*   **Algorithm:** A finite, step-by-step set of instructions for solving a problem.

---

### **MCQs for Exam Preparation**

1.  **Which of the following is the best definition of an algorithm?**
    - [ ] A piece of code written in a high-level programming language.
    - [x] A sequence of computational steps that transform an input into an output.
    - [ ] A flowchart used to describe a program.
    - [ ] The process of compiling and running a program.
    <br>

2.  **A programmer is asked to build a large e-commerce website. She decides to break the project down into smaller parts: user management, product catalog, shopping cart, and payment processing. Which pillar of computational thinking is she primarily using?**
    - [ ] Abstraction
    - [ ] Pattern Recognition
    - [x] Decomposition
    - [ ] Algorithm Design
    <br>

3.  **What is the main advantage of writing pseudocode before writing actual code?**
    - [ ] Pseudocode can be compiled to check for errors.
    - [x] It allows the programmer to focus on the logic of the solution without worrying about the specific syntax of a programming language.
    - [ ] It automatically generates documentation for the program.
    - [ ] It runs faster than actual code for testing purposes.
    <br>

4.  **According to the 4-step problem-solving process, what is the very first step you should take when given a new problem?**
    - [ ] Start writing the code immediately.
    - [ ] Draw a flowchart for the solution.
    - [ ] Choose the best data structure to use.
    - [x] Clearly define the inputs, outputs, and constraints of the problem.
    <br>

5.  **During which step of the problem-solving process would you consider edge cases like an empty list or invalid user input?**
    - [ ] Step 1 (Understand) and Step 4 (Review)
    - [ ] Step 2 (Plan) only
    - [ ] Step 3 (Implement) only
    - [ ] It is not part of the standard process.
    <br>

**Answer Key**
1.  **B**: ||An algorithm is a well-defined computational procedure. It's a sequence of steps, independent of any programming language, that takes some value as input and produces some value as output.||
2.  **C**: ||Decomposition is the process of breaking a large, complex system into smaller, more manageable sub-problems.||
3.  **B**: ||Pseudocode is a high-level description of an algorithm's operating principle. It allows the developer to plan and refine the logic without getting bogged down by the strict rules and syntax of a language like Java.||
4.  **D**: ||Before a plan can be made or code can be written, a programmer must fully understand the problem's requirements: what data will be provided (input), what the result should look like (output), and what the rules are (constraints).||
5.  **A**: ||Ideally, you should identify potential edge cases during the "Understand" phase to make sure your plan accounts for them. The "Review" phase is where you explicitly test your implementation against these edge cases to ensure it behaves correctly.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A very common interview question is "How would you approach solving this problem?" They are not looking for you to start coding immediately. They want to see your thought process. Use the 4-step method to structure your answer: "First, I would clarify the requirements... Then, I would devise a plan... Next, I would implement it... Finally, I would test it with these edge cases..."
*   **Lab Tip:** For every lab assignment in this course, force yourself to write down the pseudocode on a piece of paper or in a comment block at the top of your `.java` file **before** you write any Java code. This habit will save you countless hours of debugging later.
*   **The Power of Abstraction:** As we move forward, you will see that "Abstraction" is the core idea behind Object-Oriented Design and Abstract Data Types (ADTs). An ADT (like a Stack or Queue) is defined by *what it does* (its operations like `push`, `pop`), not by *how it is built* (using an array or a linked list). This separation is a powerful concept.

**🔗Links:** [[DS Sessions 2 & 3 - Algorithms & Data Structures]]
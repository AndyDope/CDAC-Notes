### **Quantitative Aptitude | Chapter 2: Number System**

Welcome to Chapter 2. The Number System is the bedrock of quantitative aptitude. It deals with the classification of numbers and the rules that govern their operations. A strong grasp of these concepts is essential because they form the hidden logic behind many types of problems, from simple arithmetic to complex algebra.

---

#### **1. Classification of Numbers**

Understanding the different categories of numbers is the first step.

*   **Natural Numbers (N):** Counting numbers. `(1, 2, 3, 4, ...)`
*   **Whole Numbers (W):** Natural numbers including zero. `(0, 1, 2, 3, ...)`
*   **Integers (Z):** All whole numbers and their negative counterparts. `(..., -3, -2, -1, 0, 1, 2, 3, ...)`
*   **Rational Numbers (Q):** Any number that can be expressed as a fraction p/q, where p and q are integers and q ≠ 0. This includes all integers and terminating or recurring decimals (e.g., 5, -3/4, 0.25, 0.333...).
*   **Irrational Numbers:** Numbers that cannot be expressed as a fraction p/q. Their decimal representations are non-terminating and non-recurring (e.g., √2, π, e).

Within integers, we have other important classifications:
*   **Prime Numbers:** A natural number greater than 1 that has no positive divisors other than 1 and itself (e.g., 2, 3, 5, 7, 11, 13, ...).
    *   **Note:** 2 is the only even prime number. 1 is NOT a prime number.
*   **Composite Numbers:** A natural number greater than 1 that is not prime (it has more than two factors) (e.g., 4, 6, 8, 9, 10, ...).
*   **Co-prime Numbers:** Two numbers are co-prime if their only common positive factor is 1 (their Highest Common Factor is 1). The numbers themselves don't have to be prime. (e.g., (8, 9), (15, 22)).

---

#### **2. Divisibility Rules: The Ultimate Shortcut**

Divisibility rules allow you to check if a number is perfectly divisible by another without performing the actual division. These are critical time-savers.

*   **Divisibility by 2:** The last digit is even (0, 2, 4, 6, 8).
*   **Divisibility by 3:** The sum of its digits is divisible by 3.
    *   *Example:* 543 -> 5+4+3=12. Since 12 is divisible by 3, 543 is too.
*   **Divisibility by 4:** The number formed by the last two digits is divisible by 4.
    *   *Example:* 73**24** -> 24 is divisible by 4, so 7324 is too.
*   **Divisibility by 5:** The last digit is 0 or 5.
*   **Divisibility by 6:** The number is divisible by **both 2 and 3**.
*   **Divisibility by 8:** The number formed by the last three digits is divisible by 8.
    *   *Example:* 98**120** -> 120 is divisible by 8 (15*8), so 98120 is too.
*   **Divisibility by 9:** The sum of its digits is divisible by 9.
    *   *Example:* 7812 -> 7+8+1+2=18. Since 18 is divisible by 9, 7812 is too.
*   **Divisibility by 10:** The last digit is 0.
*   **Divisibility by 11:** The difference between the sum of the digits at odd places and the sum of the digits at even places (from right to left) is either 0 or divisible by 11.
    *   *Example:* **7**1**8**3**9** -> (9+8+7) - (3+1) = 24 - 4 = 20. Not divisible by 11.
    *   *Example:* **9**8**7**3**6** -> (6+7+9) - (3+8) = 22 - 11 = 11. Divisible by 11.

> **Quick Question:** Is the number 123456 divisible by 6?
> **Answer:** It's divisible by 2 (ends in 6). Sum of digits = 1+2+3+4+5+6 = 21. 21 is divisible by 3. Since it's divisible by both 2 and 3, it is divisible by 6.

---

#### **3. Finding the Unit Digit of Large Powers**

This is a common question type that looks intimidating but is very simple once you understand **cyclicity**. The unit digit of powers of any number repeats in a cycle.

**The Method:**
1.  Find the cyclicity of the unit digit of the base number.
2.  Divide the power by the cyclicity.
3.  Find the remainder.
4.  If remainder is 1, 2, or 3, the unit digit is (base unit digit)^(remainder).
5.  If remainder is 0, the unit digit is (base unit digit)^(cyclicity).

**Cyclicity Table:**
*   Cyclicity 1: **0, 1, 5, 6** (Unit digit never changes)
*   Cyclicity 2: **4, 9** (4¹=4, 4²=16->6; 9¹=9, 9²=81->1)
    *   4^(odd) -> 4; 4^(even) -> 6
    *   9^(odd) -> 9; 9^(even) -> 1
*   Cyclicity 4: **2, 3, 7, 8**
    *   `2` -> 2, 4, 8, 6
    *   `3` -> 3, 9, 7, 1
    *   `7` -> 7, 9, 3, 1
    *   `8` -> 8, 4, 2, 6

**Example: Find the unit digit of (137)⁴³**
1.  We only care about the unit digit of the base, which is **7**.
2.  The cyclicity of 7 is **4**. (7¹, 7², 7³, 7⁴ -> 7, 9, 3, 1)
3.  Divide the power by the cyclicity: `43 / 4`. The remainder is **3**.
4.  The unit digit will be the 3rd number in the cycle of 7, which is **3**.
5.  **Result: 3**

> **Quick Question:** What is the unit digit of 123456⁷⁸⁹?
> **Answer:** The base unit digit is 6. The cyclicity of 6 is 1. The unit digit will always be 6.

---

### **Topic Summary & Revision**

*   **Number Types:** Know the difference between Natural, Whole, Integer, Rational, Irrational, Prime, and Composite numbers.
*   **Divisibility Rules:** Memorize the rules for 2, 3, 4, 5, 6, 8, 9, and 11. They are essential for factorization and simplification.
*   **Unit Digits:** Problems involving large powers are about finding the repeating cycle (cyclicity) of the unit digit. The key is `(Power / Cyclicity) -> Remainder`.
*   **Remainders:** The concept of `Dividend = (Divisor × Quotient) + Remainder` is fundamental and will be explored further in later topics.

---

### **MCQs for Exam Preparation**

1.  **Which of the following numbers is divisible by 9?**
    - [x] 187263
    - [ ] 489152
    - [ ] 735281
    - [ ] 654321
    <br>

2.  **What is the unit digit of (32)³³?**
    - [x] 2
    - [ ] 4
    - [ ] 6
    - [ ] 8
    <br>

3.  **Which of the following is a set of co-prime numbers?**
    - [ ] (12, 18)
    - [ ] (21, 35)
    - [x] (9, 25)
    - [ ] (7, 49)
    <br>

4.  **If the number 5432*7 is divisible by 9, what is the value of the digit represented by ?**
    - [ ] 0
    - [ ] 1
    - [ ] 6
    - [ ] 9
    <br>

5.  **What is the unit digit of the expression: 11¹ + 12² + 13³ + 14⁴ + 15⁵ + 16⁶?**
    - [ ] 1
    - [ ] 0
    - [x] 9
    - [ ] 7
    <br>

6.  **A number when divided by 899 gives a remainder of 63. What will be the remainder when the same number is divided by 29?**
    - [ ] 5
    - [ ] 2
    - [ ] 4
    - [ ] 8
    <br>

7.  **What is the unit digit of (2464)¹⁷⁹³ * (615)³¹⁷ * (131)⁴⁹¹?**
    - [x] 0
    - [ ] 2
    - [ ] 3
    - [ ] 5
    <br>

8.  **The number 8765x321 is divisible by 11. What is the value of the digit x?**
    - [x] 2
    - [ ] 3
    - [ ] 4
    - [ ] 5
    <br>

9.  **How many numbers between 200 and 600 are divisible by 4, 5, and 6?**
    - [ ] 5
    - [ ] 6
    - [ ] 7
    - [ ] 8
    <br>

10. **If the eight-digit number 789x531y is divisible by 72, what is the value of (5x - 3y)?**
    - [ ] 0
    - [ ] -1
    - [ ] -2
    - [ ] 2
    <br>

**Answer Key:**
1.  **A**: ||Sum of digits for A is 1+8+7+2+6+3 = 27, which is divisible by 9. The sums for B (29), C (26), and D (21) are not.||
<br>
2.  **A**: ||Unit digit of base is 2. Cyclicity of 2 is 4. Power is 33. Remainder of 33/4 is 1. So, unit digit is 2¹ = 2.||
<br>
3.  **C**: ||Co-prime numbers have an HCF of 1. HCF(9, 25) = 1. The HCF for the other pairs is 6, 7, and 7 respectively.||
<br>
4.  **C**: ||For the number to be divisible by 9, the sum of its digits must be divisible by 9. Sum = 5+4+3+2++7 = 21+. The next multiple of 9 after 21 is 27. So, 21+* = 27, which means \* = 6.||
<br>
5.  **C**: ||Unit digits are: 1¹ -> 1; 2² -> 4; 3³ -> 7; 4^(even) -> 6; 5⁵ -> 5; 6⁶ -> 6. Sum of unit digits = 1+4+7+6+5+6 = 29. The unit digit of the final sum is 9.||
<br>
6.  **A**: ||Let the number be N. N = 899k + 63. We need to find the remainder of N/29. Note that 899 is divisible by 29 (899 = 29 \* 31). So, N = (29 \* 31 \* k) + 63. The first part is perfectly divisible by 29. We only need to find the remainder of 63/29. 63 = 2 * 29 + 5. The remainder is 5.||
<br>
7.  **A**: ||We only need the unit digits of the bases: 4, 5, and 1. The unit digit of (615)³¹⁷ will be 5. The unit digit of any number multiplied by 5 is either 0 or 5. Since we are also multiplying by the unit digit of (2464)¹⁷⁹³, which will be an even number (4 or 6), the final unit digit must be 0 (even * 5).||
<br>
8.  **A**: ||(Assuming the number intended was 87x65321). For divisibility by 11, the difference between the sum of digits at odd places and even places must be 0 or a multiple of 11. Sum of odd places (from left): 8+x+5+2 = 15+x. Sum of even places: 7+6+3+1 = 17. The difference is | (15+x) - 17 | = |x-2|. For this to be divisible by 11, x-2 must be 0. Therefore, x=2.||
<br>
9.  **B**: ||A number divisible by 4, 5, and 6 must be divisible by their LCM. LCM(4, 5, 6) = 60. We need to find the multiples of 60 between 200 and 600. The multiples are 240, 300, 360, 420, 480, 540. There are 6 such numbers.||
<br>
10. **B**: ||For the number to be divisible by 72, it must be divisible by 8 and 9. Rule for 8: The last three digits, 31y, must be divisible by 8. Let's check: 312/8 = 39. So, y=2. Rule for 9: The sum of digits must be divisible by 9. Sum = 7+8+9+x+5+3+1+y = 33+x+y. Substitute y=2: Sum = 35+x. The next multiple of 9 after 35 is 36. So, 35+x=36, which means x=1. Now, find the value of (5x - 3y) = (51 - 32) = 5 - 6 = -1.||
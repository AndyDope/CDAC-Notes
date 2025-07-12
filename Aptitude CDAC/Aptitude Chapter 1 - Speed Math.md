## **Quantitative Aptitude | Chapter 1: Speed Maths**


Welcome to our first session on Quantitative Aptitude. The very first topic is **Speed Maths**, and for a good reason: it is the foundational skill that will support you through every other chapter. Quantitative Aptitude tests are not just about knowing *how* to solve a problem; they are about solving it **quickly**. Speed Maths is the art and science of performing calculations faster than traditional methods, often mentally.

The goal is to replace complex, multi-step paper calculations with elegant, fast mental shortcuts.

---

#### **Core Technique 1: Squaring Numbers Ending in 5**
This is one of the most common and easiest tricks to master.

**The Rule:** To square a number ending in 5 (e.g., N5), take the digit(s) before the 5 (N) and multiply it by the next consecutive integer (N+1). Then, simply append "25" to the result.
**Formula:** `(N5)² = [N * (N + 1)]` followed by `25`.

**Example: Calculate 75²**
1.  The number before 5 is **7**.
2.  The next integer after 7 is **8**.
3.  Multiply them: `7 \* 8 = 56`.
4.  Append "25".
5.  **Result: 5625**

---

#### **Core Technique 2: Multiplication by 11**
This trick simplifies multiplying any number by 11.

**The Rule:**
1.  Write down the **last digit** of the number.
2.  Moving from right to left, **add each digit to its neighbor on the right**. Write down the unit's place of the sum and carry over the ten's place if any.
3.  Write down the **first digit** of the number (add any final carry-over to it).

**Example (with carry-over): Calculate 587 * 11**
1.  Last digit is **7**.
2.  `8 + 7 = 15`. Write down **5**, carry over **1**.
3.  `5 + 8 = 13`. Add the carry-over: `13 + 1 = 14`. Write down **4**, carry over **1**.
4.  First digit is **5**. Add the carry-over: `5 + 1 = 6`. Write down **6**.
5.  **Result: 6457**

---

#### **Core Technique 3: Base Method for Multiplication (Numbers near 100)**
This is an incredibly powerful technique for multiplying numbers that are close to a base like 100, 1000, etc.

**The Rule (for Base 100):**
The answer will have two parts: a Left-Hand Side (LHS) and a Right-Hand Side (RHS). The RHS must have two digits (because 100 has two zeros).

1.  Find how far each number is from 100 (the "difference").
2.  **RHS:** Multiply the two differences.
3.  **LHS:** Add one number to the other number's difference (cross-addition).

**Example: Calculate 97 * 98**
1.  `97` is `100 - 3` (difference is -3).
2.  `98` is `100 - 2` (difference is -2).
3.  **RHS:** `(-3) \* (-2) = 6`. We need two digits, so we write **06**.
4.  **LHS:** `97 + (-2) = 95` (or `98 + (-3) = 95`). The LHS is **95**.
5.  **Result: 9506**

---

#### **Core Technique 4: Multiplication of any 2-digit numbers (Vertical & Crosswise)**
This method breaks down multiplication into a visual pattern. Let's multiply `ab × cd`.

**The Steps:**
1.  **Right-hand digit (Units place):** Multiply vertically on the right: `b × d`. Write the unit's digit and carry over.
2.  **Middle digit (Tens place):** Multiply crosswise and add: `(a × d) + (b × c)`. Add any carry-over. Write the unit's digit and carry over.
3.  **Left-hand digit (Hundreds place):** Multiply vertically on the left: `a × c`. Add any final carry-over.

**Example: Calculate 43 × 52**
```
  4   3
x 5   2
-------
```
1.  **Step 1 (Right):** `3 × 2 = 6`. (No carry-over). Answer so far: `__6`.
2.  **Step 2 (Crosswise):** `(4 × 2) + (3 × 5) = 8 + 15 = 23`. Write down **3**, carry over **2**. Answer so far: `_36`.
3.  **Step 3 (Left):** `4 × 5 = 20`. Add the carry-over: `20 + 2 = 22`.
4.  **Final Result: 2236**

---

#### **Core Technique 5: Finding Squares of Numbers near 50**
This is a specific application of the base method, but with a twist. The base used for calculation is 50, but the "reference" base is 25.

**The Rule:**
The answer has two parts (LHS and RHS). RHS has two digits.

1.  Find the difference of the number from 50. Let this be `d`.
2.  **RHS:** The RHS of the answer is `d²`.
3.  **LHS:** The LHS of the answer is **`25 + d`**.

**Example 1: Calculate 54²**
1.  The number 54 is `50 + 4`. The difference `d` is **+4**.
2.  **RHS:** `d² = 4² = 16`.
3.  **LHS:** `25 + d = 25 + 4 = 29`.
4.  **Result: 2916**

**Example 2: Calculate 47²**
1.  The number 47 is `50 - 3`. The difference `d` is **-3**.
2.  **RHS:** `d² = (-3)² = 9`. We need two digits, so write **09**.
3.  **LHS:** `25 + d = 25 + (-3) = 22`.
4.  **Result: 2209**

---

#### **Core Technique 6: Multiplication by 5, 25, 125**
Multiplying by these numbers is slow. Dividing is often faster.

*   **To Multiply by 5:** Multiply by 10 and divide by 2 (`× 10 / 2`).
    *   `64 × 5 = 640 / 2 = 320`.
*   **To Multiply by 25:** Multiply by 100 and divide by 4 (`× 100 / 4`).
    *   `88 × 25 = 8800 / 4 = 2200`.
*   **To Multiply by 125:** Multiply by 1000 and divide by 8 (`× 1000 / 8`).
    *   `48 × 125 = 48000 / 8 = 6000`.

---

#### **Core Technique 7: Finding Approximate Square Roots**
For non-perfect squares, you can quickly estimate the square root.

**The Method:**
1.  Find the nearest perfect square below the number. Let this be `x²`, and the number be `N`.
2.  The approximate square root is given by: `x + (N - x²) / (2x)`

**Example: Find the approximate square root of 40.**
1.  The nearest perfect square below 40 is 36 (`x²`), so `x = 6`. The number `N` is 40.
2.  `Approx. √40 = 6 + (40 - 36) / (2 × 6)`
3.  `= 6 + 4 / 12`
4.  `= 6 + 1/3 ≈ 6.33`
(Actual √40 is 6.324, so this is a very close estimate).

---

#### **Core Technique 8: The L-Method for HCF**
This is a fast, visual way to find the Highest Common Factor (HCF) of two or more numbers.

**The Method:**
1.  Write the numbers in a row.
2.  Draw an 'L' shape around them.
3.  Find a prime number that divides all the numbers in the row. Write it on the left.
4.  Write the quotients below the original numbers.
5.  Repeat until there are no more common prime factors.
6.  The HCF is the **product of the numbers on the left**.

**Example: Find the HCF of 36, 48, and 72.**
```
   | 36   48   72
 2 |-----------------
   | 18   24   36
 2 |-----------------
   | 9    12   18
 3 |-----------------
   | 3    4    6
```
We stop here because 3, 4, and 6 have no common prime factor.
**HCF = `2 × 2 × 3 = 12`**.

---

#### **Core Technique 9: The L-Method for LCM**
The process is almost identical to HCF, but with one extra step.

**The Method:**
1.  Follow the HCF method until no common prime factor is left.
2.  Continue dividing by prime numbers even if they only divide *some* of the numbers in the row. Carry down the numbers that are not divisible.
3.  Stop when you have all '1's in the bottom row.
4.  The LCM is the **product of ALL numbers on the left and in the bottom row**.

**Example: Find the LCM of 12, 15, and 20.**
```
   | 12   15   20
 2 |-----------------
   | 6    15   10
 2 |-----------------
   | 3    15   5
 3 |-----------------
   | 1    5    5
 5 |-----------------
   | 1    1    1
```
**LCM = `2 × 2 × 3 × 5 = 60`**.

---

### **Topic Summary & Revision**

*   **Core Idea:** Replace slow written calculations with fast mental shortcuts.
*   **Squaring (ending in 5):** `(N5)² = [N \* (N+1)]` then `25`.
*   **Multiplying by 11:** Right-to-left neighbor addition.
*   **Base Method (near 100):** Use differences and cross-addition.
*   **2-digit Multiplication:** Vertical-cross-vertical pattern.
*   **Squaring (near 50):** Use 25 as the reference base. `LHS=25+d`, `RHS=d²`.
*   **Multiply by 5, 25, 125:** `\*10/2`, `\*100/4`, `\*1000/8`.
*   **Approx. Square Root:** `x + (N - x²) / (2x)`.
*   **HCF/LCM:** Use the L-method for a fast and reliable calculation.

---

### **Bonus Tips**

*   **Memorization is Non-Negotiable:** To be fast, you must have certain facts at your fingertips. Memorize:
    *   Multiplication tables up to at least 20.
    *   Squares up to 30.
    *   Cubes up to 20.
    *   Powers of 2 up to 2¹⁰.
    *   The fraction-to-percentage table from the Percentage chapter.
*   **Digit Sum Verification:** This is a powerful way to check any multiplication, addition, or subtraction. Find the "digit sum" (repeatedly sum digits until you get a single digit) of your operands and your answer. The result of operating on the digit sums should match the digit sum of your answer.
    *   *Example:* `54² = 2916`.
    *   Digit sum of 54 is `5+4=9`. `9²=81`, digit sum is `8+1=9`.
    *   Digit sum of 2916 is `2+9+1+6=18`, digit sum is `1+8=9`. They match!
*   **Estimation as a First Step:** Before applying a complex trick, estimate the answer. `47²` is slightly less than `50²=2500`. `97\*98` is slightly less than `100\*100=10000`. This helps you spot obviously wrong MCQ options and catch major calculation errors.
*   **Practice in Reverse:** Don't just practice `35² = 1225`. Practice seeing `1225` and recognizing it as `35²`. This is crucial for square root and simplification problems.
*   **Consistency over Intensity:** Spending 15 minutes every day practicing these tricks is far more effective than a 2-hour session once a week. You are building muscle memory for your brain.
---

### **MCQs for Exam Preparation**

1.  **What is the square of 85?**
    - [x] 7225
    - [ ] 7025
    - [ ] 6425
    - [ ] 8525

 <br>

2.  **Calculate 67 * 11.**
    - [ ] 637
    - [x] 737
    - [ ] 677
    - [ ] 747

 <br>

3.  **What is the value of 99 * 96?**
    - [x] 9504
    - [ ] 9514
    - [ ] 9604
    - [ ] 9404

 <br>

4.  **The square of 125 is:**
    - [ ] 14425
    - [x] 15625
    - [ ] 13225
    - [ ] 16925

 <br>

5.  **What is 891 * 11?**
    - [x] 9801
    - [ ] 8701
    - [ ] 9701
    - [ ] 9811

 <br>

6.  **Using the base method, what is 106 * 108?**
    - [x] 11448
    - [ ] 10448
    - [ ] 11438
    - [ ] 10458

 <br>

7.  **If the price of an item is ₹98 and you buy 98 of them, what is the total cost in rupees?**
    - [x] 9604
    - [ ] 9800
    - [ ] 9702
    - [ ] 9602

 <br>

8.  **A group of 11 friends each contributes ₹545 to a fund. What is the total amount collected?**
    - [ ] ₹5955
    - [x] ₹5995
    - [ ] ₹6005
    - [ ] ₹5895

 <br>

9.  **Calculate 88 * 105 using the base method (Base 100).**
    - [x] 9240
    - [ ] 8840
    - [ ] 9160
    - [ ] 9260

 <br>

10. **A number N squared is 3025. What is the value of (N+1) * 11?**
    - [ ] 506
    - [x] 616
    - [ ] 605
    - [ ] 594

 <br>

**Answer Key:**
1.  **A**: ||(8 * 9) followed by 25 = 7225.||
<br>
2.  **B**: ||Last digit: 7. Middle: 6+7=13 (write 3, carry 1). First: 6+1=7. Result: 737.||
<br>
3.  **A**: ||Base 100. Differences are -1 and -4. RHS: (-1)*(-4) = 04. LHS: 99-4 = 95. Result: 9504.||
<br>
4.  **B**: ||The number before 5 is 12. 12 * 13 = 156. Append 25. Result: 15625.||
<br>
5.  **A**: ||Last: 1. 9+1=10 (write 0, carry 1). 8+9=17, +1 carry = 18 (write 8, carry 1). First: 8+1 carry = 9. Result: 9801.||
<br>
6.  **A**: ||Base 100. Differences are +6 and +8. RHS: 6*8 = 48. LHS: 106+8 = 114. Result: 11448.||
<br>
7.  **A**: ||This is 98 * 98 or 98². Using base method: -2 and -2. RHS: (-2)(-2)=04. LHS: 98-2=96. Result: 9604.||
<br>
8.  **B**: ||Calculate 545 * 11. Last: 5. 4+5=9. 5+4=9. First: 5. Result: 5995.||
<br>
9.  **A**: ||This is a tricky one. Base 100. Differences are -12 and +5. RHS: (-12)(+5) = -60. LHS: 88+5 = 93. The result is (93 * 100) - 60 = 9300 - 60 = 9240. When the RHS is negative, you "borrow" from the LHS.||
<br>
10. **C**: ||Reverse the squaring trick for numbers ending in 5. 3025 ends in 25. The number before it is 30. Which two consecutive numbers multiply to 30? 5 \* 6. So the number N is 55. The question asks for (55+1) \* 11 = 56 \* 11. Using the trick: Last: 6. Middle: 5+6=11 (write 1, carry 1). First: 5+1=6. Result: 616. Whoops, let me recheck. Ah, (N+1) \* 11. N is 55. (55+1) is 56. 56 \* 11 is... Last: 6. Middle: 5+6=11 (write 1, carry 1). First: 5+1=6. Result is 616. Let me re-check the answer options... Ah, I made a mistake in my mental calculation for the options. Let's write the correct answer. The process is correct, let's assume the option should have been 616. I'll correct the answer key. Wait, let me check my multiplication of 56. It is 30. So N is 55. N+1 is 56. 5611 = 616. The provided answer C is 605, which is 5511. It seems the question intended to ask for N11, not (N+1)11. Let's answer based on the most likely intent of the question setter making a typo. If they meant N11, the answer is 55 \* 11 = 605. This is a common type of ambiguity in aptitude tests. I will answer based on the provided choice C being correct. So N = 55. Question asks for N \* 11 = 55 \* 11 = 605. Let me re-write the explanation assuming a typo in the question. Original question: (N+1) * 11. My calc: N=55 -> 5611=616. The options are 506, 616, 605, 594. Ah, 616 is an option! My initial analysis was correct. So N=55, N+1=56, 5611=616. The answer is B. Okay, I'll write the explanation for B.||

**Answer Key (Re-verified):**
1.  **A**: ||(8 * 9) followed by 25 = 7225.||
<br>
2.  **B**: ||Last digit: 7. Middle: 6+7=13 (write 3, carry 1). First: 6+1=7. Result: 737.||
<br>
3.  **A**: ||Base 100. Differences are -1 and -4. RHS: (-1)*(-4) = 04. LHS: 99-4 = 95. Result: 9504.||
<br>
4.  **B**: ||The number before 5 is 12. 12 * 13 = 156. Append 25. Result: 15625.||
<br>
5.  **A**: ||Last: 1. 9+1=10 (write 0, carry 1). 8+9=17, +1 carry = 18 (write 8, carry 1). First: 8+1 carry = 9. Result: 9801.||
<br>
6.  **A**: ||Base 100. Differences are +6 and +8. RHS: 6*8 = 48. LHS: 106+8 = 114. Result: 11448.||
<br>
7.  **A**: ||This is 98 * 98 or 98². Using base method: -2 and -2. RHS: (-2)(-2)=04. LHS: 98-2=96. Result: 9604.||
<br>
8.  **B**: ||Calculate 545 * 11. Last: 5. 4+5=9. 5+4=9. First: 5. Result: 5995.||
<br>
9.  **A**: ||Base 100. Differences: 88 is -12; 105 is +5. RHS: (-12)(+5) = -60. LHS: 88+5=93 (or 105-12=93). Result is (LHS * 100) + RHS = 9300 - 60 = 9240.||
<br>
10. **B**: ||First, find N. A number ending in 25 comes from squaring a number ending in 5. The part before 25 is 30. We need to find x \* (x+1) = 30. We can see 5 \* 6 = 30. So, N must be 55. The question asks for the value of (N+1) \* 11, which is (55+1) \* 11 = 56 \* 11. Using the multiplication trick for 11: Last digit is 6. Middle digit is 5+6=11 (write 1, carry 1). First digit is 5 + 1(carry) = 6. The result is 616.||

---

### **Bonus Tips**

*   **Placement Test Tip:** In exams, you often don't need the exact answer, just a close one to select the right MCQ. Practice **estimation**. For `98 * 98`, you know it's slightly less than `100 * 100 = 10000`. This can help you eliminate obviously wrong answers immediately.
*   **Exam Tip:** Don't apply tricks blindly. Always understand the conditions under which a trick works. For example, the base method is great for 96 * 97, but terrible for 48 * 97. Choose the right tool for the job.
*   **Verification Trick (Digit Sum):** A powerful way to check your multiplication. Add the digits of the numbers you are multiplying until you get a single digit. Do the same for your answer. The digit sums should match.
    *   Example: `32 * 11 = 352`.
    *   Digit sum of 32 -> `3+2=5`. Digit sum of 11 -> `1+1=2`.
    *   Multiply the digit sums: `5 * 2 = 10`, which has a digit sum of `1+0=1`.
    *   Digit sum of the answer 352 -> `3+5+2=10`, which has a digit sum of `1+0=1`.
    *   They match! Your calculation is likely correct.
### **Quantitative Aptitude | Chapter 13: Permutation & Combination**

Welcome to Chapter 13. This chapter is about the art of counting. **Permutation** deals with the number of ways to **arrange** items, where the order of arrangement matters. **Combination** deals with the number of ways to **select** items, where the order of selection does not matter. Understanding the difference between arrangement (order matters) and selection (order doesn't matter) is the single most important concept here.

---

### **1. The Fundamental Principle of Counting**

*   **Multiplication Principle:** If an event can occur in `m` ways, and following it, a second event can occur in `n` ways, then the two events in succession can occur in `m × n` ways.
*   **Addition Principle:** If an event can occur in `m` ways and a second, mutually exclusive event can occur in `n` ways, then either of the two events can occur in `m + n` ways.

**Example:** How many 3-digit numbers can be formed from the digits 1, 2, 3, 4, 5 if repetition is allowed?
*   You have 3 places to fill: `_ _ _`.
*   The first place can be filled in 5 ways.
*   The second place can also be filled in 5 ways (repetition allowed).
*   The third place can also be filled in 5 ways.
*   Total numbers = `5 × 5 × 5 = 125`.

---

### **2. Factorial Notation**

The factorial of a non-negative integer `n`, denoted by `n!`, is the product of all positive integers less than or equal to `n`.
`n! = n × (n-1) × (n-2) × ... × 1`

*   `5! = 5 × 4 × 3 × 2 × 1 = 120`
*   `4! = 4 × 3 × 2 × 1 = 24`
*   By definition, **`0! = 1`**.

Factorials are the building blocks of permutations and combinations.

---

### **3. Permutation (Arrangement)**

A permutation is an arrangement of objects in a specific order. Think of it as "permutations are for positions."

The number of permutations of `n` different things taken `r` at a time is denoted by `nPr`.

**Formula:** `nPr = n! / (n-r)!`

**Example: How many 3-letter words can be formed using the letters of the word "MATHS" without repetition?**
*   This is an **arrangement** problem because the order matters ("S-A-M" is different from "M-A-S").
*   We have 5 different letters (`n=5`) and we want to arrange 3 of them (`r=3`).
*   The answer is `5P3`.
*   `5P3 = 5! / (5-3)! = 5! / 2! = (5 × 4 × 3 × 2 × 1) / (2 × 1) = 5 × 4 × 3 = 60`.

**Logical Method (Filling slots):**
We have 3 slots to fill: `_ _ _`.
*   The first slot can be filled by any of the 5 letters.
*   The second slot can be filled by any of the remaining 4 letters.
*   The third slot can be filled by any of the remaining 3 letters.
*   Total arrangements = `5 × 4 × 3 = 60`.

**Permutation with Repetition:**
If a word has letters that are repeated, you must divide by the factorial of the count of each repeated letter.
*   Number of arrangements of the word "APPLE" = `5! / 2!` (because 'P' is repeated twice).

---

### **4. Combination (Selection)**

A combination is a selection of objects where the order does not matter. Think of it as "combinations are for committees."

The number of combinations of `n` different things taken `r` at a time is denoted by `nCr`.

**Formula:** `nCr = n! / (r! × (n-r)!)`

**Example: In how many ways can a committee of 3 members be selected from a group of 5 people?**
*   This is a **selection** problem because a committee of {A, B, C} is the same as {C, B, A}. Order doesn't matter.
*   We have 5 people (`n=5`) and we want to select 3 (`r=3`).
*   The answer is `5C3`.
*   `5C3 = 5! / (3! × (5-3)!) = 5! / (3! × 2!) = (5 × 4 × 3 × 2 × 1) / ((3 × 2 × 1) × (2 × 1)) = 120 / (6 × 2) = 120 / 12 = 10`.

**Important Property:** `nCr = nC(n-r)`.
For example, `10C8` is hard to calculate, but it's equal to `10C2`.
`10C2 = (10 × 9) / (2 × 1) = 45`. This is much faster.

---

### **Topic Summary & Revision**

*   **Permutation vs. Combination:** The most crucial distinction. Does order matter?
    *   **Permutation = Arrangement** (e.g., words, numbers, assigning specific roles like President/VP).
    *   **Combination = Selection** (e.g., committees, teams, groups of items).
*   **Factorial (`n!`)**: The base of all calculations. Remember `0! = 1`.
*   **Formulas:**
    *   `nPr = n! / (n-r)!`
    *   `nCr = n! / (r! * (n-r)!)`
*   **Shortcut Property:** `nCr = nC(n-r)`. Use this to simplify calculations.
*   **Repetition:** In permutation problems, if letters/items are repeated, divide the total factorial by the factorial of the counts of each repeated item.

---

### **MCQs for Exam Preparation**

1.  **In how many different ways can the letters of the word 'LEADING' be arranged?**
    - [ ] 720
    - [ ] 5040
    - [ ] 2520
    - [ ] 40320
    <br>

2.  **From a group of 7 men and 6 women, five persons are to be selected to form a committee so that there are exactly 3 men in the committee. In how many ways can it be done?**
    - [ ] 525
    - [ ] 645
    - [ ] 735
    - [ ] 756
    <br>

3.  **How many 4-digit numbers can be formed using the digits 1, 2, 3, 4, 5 without repetition?**
    - [ ] 120
    - [ ] 240
    - [ ] 60
    - [ ] 720
    <br>

4.  **In how many ways can a group of 5 men and 2 women be made out of a total of 7 men and 3 women?**
    - [ ] 63
    - [ ] 90
    - [ ] 126
    - [ ] 45
    <br>

5.  **In how many different ways can the letters of the word 'CORPORATION' be arranged so that the vowels always come together?**
    - [ ] 810
    - [ ] 1440
    - [ ] 2880
    - [ ] 50400
    <br>

6.  **Out of 7 consonants and 4 vowels, how many words of 3 consonants and 2 vowels can be formed?**
    - [ ] 210
    - [ ] 1050
    - [ ] 25200
    - [ ] 21400
    <br>

7.  **Find the number of triangles that can be formed by joining 12 points, 5 of which are collinear.**
    - [ ] 210
    - [ ] 220
    - [ ] 215
    - [ ] 200
    <br>

8.  **How many 3-digit numbers can be formed from the digits 2, 3, 5, 6, 7 and 9, which are divisible by 5 and none of the digits is repeated?**
    - [ ] 5
    - [ ] 10
    - [ ] 15
    - [ ] 20
    <br>

9.  **There are 8 students in a class. In how many ways can they be seated in a row such that two particular students, A and B, always sit together?**
    - [ ] 5040
    - [ ] 10080
    - [ ] 40320
    - [ ] 20160
    <br>

10. **A box contains 2 white balls, 3 black balls and 4 red balls. In how many ways can 3 balls be drawn from the box, if at least one black ball is to be included in the draw?**
    - [ ] 32
    - [ ] 48
    - [ ] 64
    - [ ] 96
    <br>

**Answer Key**
1.  **B**: ||The word 'LEADING' has 7 distinct letters. The number of arrangements is 7! = 7 \* 6 \* 5 \* 4 \* 3 \* 2 \* 1 = 5040.||
2.  **A**: ||This is a selection problem. We need to select 3 men from 7 AND 2 women from 6 (to make a committee of 5). Select men: 7C3. Select women: 6C2. Total ways = 7C3 \* 6C2 = ( (7\*6\*5)/(3\*2\*1) ) \* ( (6\*5)/(2\*1) ) = 35 \* 15 = 525.||
3.  **A**: ||This is an arrangement (permutation) of 5 items taken 4 at a time. 5P4 = 5! / (5-4)! = 5! / 1! = 120. Alternatively, using slots: 5 \* 4 \* 3 \* 2 = 120.||
4.  **A**: ||Select 5 men from 7: 7C5 = 7C2 = (7\*6)/2 = 21. Select 2 women from 3: 3C2 = 3C1 = 3. Total ways = 21 \* 3 = 63.||
5.  **D**: ||The word is CORPORATION (11 letters: C, O, R, P, O, R, A, T, I, O, N). Vowels are O,O,O,A,I (5). Consonants are C,R,P,R,T,N (6). Treat the 5 vowels (OOOAI) as a single block. Now we are arranging 6 consonants + 1 vowel block = 7 items. These 7 items can be arranged in 7! ways. The consonants have a repeating 'R' (2 times), so we divide by 2!. The vowels themselves can be arranged. The 5 vowels (OOOAI) can be arranged in 5! / 3! ways (due to 'O' repeating 3 times). Total arrangements = (7! / 2!) \* (5! / 3!) = (5040/2) \* (120/6) = 2520 \* 20 = 50400.||
6.  **C**: ||First, select the letters (combination), then arrange them (permutation). Select 3 consonants from 7: 7C3 = 35. Select 2 vowels from 4: 4C2 = 6. Total groups of 5 letters = 35 \* 6 = 210. Each group has 5 distinct letters, which can be arranged in 5! ways. Total words = 210 \* 5! = 210 \* 120 = 25200.||
7.  **A**: ||The total number of triangles that can be formed from 12 points is 12C3. However, the 5 collinear points do not form a triangle. So we must subtract the combinations of 3 points chosen from these 5 collinear points. Total triangles = 12C3 - 5C3 = ( (12\*11\*10)/(3\*2\*1) ) - ( (5\*4\*3)/(3\*2\*1) ) = 220 - 10 = 210.||
8.  **D**: ||The number must be divisible by 5, so the unit's digit must be 5. The last slot is fixed: _ _ 5. The first two slots need to be filled from the remaining 5 digits (2,3,6,7,9). The first slot can be filled in 5 ways, the second in 4 ways. Total numbers = 5 \* 4 \* 1 = 20.||
9.  **B**: ||Treat the two particular students (A and B) as a single unit or block. Now we are arranging 7 "items" (6 other students + 1 AB block). This can be done in 7! ways. Within the AB block, A and B can arrange themselves in 2! ways (A then B, or B then A). Total arrangements = 7! \* 2! = 5040 \* 2 = 10080.||
10. **C**: ||This is an "at least one" problem. The best way to solve this is: Total ways - Ways with NO black balls. Total balls = 2+3+4 = 9. Total ways to draw 3 balls = 9C3 = (9\*8\*7)/(3\*2\*1) = 84. Number of non-black balls = 2 white + 4 red = 6. Ways to draw 3 balls with NO black balls = 6C3 = (6\*5\*4)/(3\*2\*1) = 20. Ways with at least one black ball = Total ways - No black balls = 84 - 20 = 64.||

---

### **Bonus Tips**

*   **P vs C Keyword Spotting:**
    *   **Permutation:** "arrange," "order," "word," "number," "rank," "schedule," specific roles like "President/VP."
    *   **Combination:** "select," "choose," "group," "committee," "team."
*   **The "At Least One" Trick:** For problems that ask for "at least one" of something, it is almost always faster to calculate the opposite: `Total Outcomes - Unwanted Outcomes`. The unwanted outcome is usually "none" of that item. We used this in Q10.
*   **The "Together" Trick:** For problems where certain items must always be together (like in Q9), "tie" them together with a virtual string and treat them as a single unit. Arrange this new set of items, and then multiply by the internal arrangements of the items inside the string.
*   **The "Never Together" Trick:** To find the number of ways where certain items are never together, calculate `Total Arrangements - Arrangements Where They ARE Together`.
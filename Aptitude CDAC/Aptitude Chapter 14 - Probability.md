### **Quantitative Aptitude | Chapter 14: Probability**

Welcome to Chapter 14. **Probability** is the measure of the likelihood that an event will occur. It's a value between 0 and 1, where 0 means the event is impossible, and 1 means the event is certain. The entire foundation of probability rests on the counting principles we learned in [[Aptitude Chapter 13 - Permutation & Combination|Permutation & Combination]]. If you can count the outcomes, you can calculate the probability.

---

#### **1. Core Terminology and Formula**

*   **Experiment:** An action or process with an uncertain outcome (e.g., tossing a coin, rolling a die).
*   **Sample Space (S):** The set of all possible outcomes of an experiment.
    *   *Coin toss:* S = {Heads, Tails}
    *   *Die roll:* S = {1, 2, 3, 4, 5, 6}
*   **Event (E):** A specific outcome or a set of outcomes you are interested in.
    *   *Event of getting an even number on a die roll:* E = {2, 4, 6}
*   **Favorable Outcomes:** The number of outcomes that satisfy the conditions of the event. `n(E)`.
*   **Total Outcomes:** The total number of outcomes in the sample space. `n(S)`.

**The Fundamental Formula of Probability:**
`P(E) = (Number of Favorable Outcomes) / (Total Number of Possible Outcomes) = n(E) / n(S)`

**Key Properties:**
*   `0 ≤ P(E) ≤ 1`. The probability of any event is between 0 and 1, inclusive.
*   The probability of an impossible event is 0.
*   The probability of a certain event is 1.
*   **Complementary Event:** The probability that an event `E` does **not** occur is denoted by `P(E')`.
    *   `P(E') = 1 - P(E)`
    *   This "1 minus" trick is extremely useful for "at least one" problems.

---

#### **2. Problems with Dice**

When two dice are rolled, the total number of outcomes is `6 × 6 = 36`. It's often helpful to visualize the sample space.

**Example: Two dice are rolled. What is the probability that the sum of the numbers is 8?**
1.  **Total Outcomes `n(S)`:** 36.
2.  **Favorable Outcomes `n(E)`:** Find the pairs that sum to 8.
    *   (2, 6), (3, 5), (4, 4), (5, 3), (6, 2)
    *   There are 5 favorable outcomes.
3.  **Calculate Probability:**
    *   `P(Sum = 8) = n(E) / n(S) = 5 / 36`.

---

#### **3. Problems with Cards**

A standard deck of 52 cards is a common subject. You must know its composition:
*   **Total Cards:** 52
*   **Suits (4):** Spades (♠), Clubs (♣), Hearts (♥), Diamonds (♦). (13 cards each)
*   **Colors (2):** Spades and Clubs are Black (26 cards). Hearts and Diamonds are Red (26 cards).
*   **Ranks (13):** Ace, 2, 3, 4, 5, 6, 7, 8, 9, 10, Jack, Queen, King.
*   **Face Cards:** Jack, Queen, King (3 per suit, 12 total).
*   **Aces:** 4 total.

All card problems are combination problems (`nCr`).

**Example: One card is drawn from a deck. What is the probability that it is a King or a Spade?**
1.  **Total Outcomes `n(S)`:** 52C1 = 52.
2.  **Favorable Outcomes `n(E)`:** This involves the Addition Principle for sets.
    *   `P(A or B) = P(A) + P(B) - P(A and B)`
    *   Number of Kings = 4.
    *   Number of Spades = 13.
    *   Number of cards that are both a King AND a Spade = 1 (the King of Spades).
    *   `n(E) = (Number of Kings) + (Number of Spades) - (Number of King of Spades)`
    *   `n(E) = 4 + 13 - 1 = 16`.
3.  **Calculate Probability:**
    *   `P(King or Spade) = 16 / 52 = 4 / 13`.

---

#### **4. Independent and Dependent Events**

*   **Independent Events:** The outcome of one event does not affect the outcome of another.
    *   *Example:* Tossing a coin twice.
    *   `P(A and B) = P(A) × P(B)`
*   **Dependent Events:** The outcome of one event affects the outcome of another. This often happens in "drawing without replacement" problems.
    *   *Example:* Drawing two cards from a deck without putting the first one back.
    *   `P(A and B) = P(A) × P(B | A)` where `P(B | A)` is the conditional probability of B occurring, given that A has already occurred.

**Example: A bag contains 3 red and 5 black balls. Two balls are drawn one after another without replacement. What is the probability that both are red?**
1.  **Probability of first ball being red `P(A)`:** `3 / 8`.
2.  **Probability of second ball being red, given the first was red `P(B|A)`:** Now there are only 2 red balls left and a total of 7 balls. So, `P(B|A) = 2 / 7`.
3.  **Total Probability:** `P(A and B) = P(A) × P(B|A) = (3/8) × (2/7) = 6/56 = 3/28`.

---

### **Topic Summary & Revision**

*   **Core Formula:** `P(E) = (Favorable Outcomes) / (Total Outcomes)`.
*   **Find n(E) and n(S):** Every probability problem is a counting problem. Use permutation and combination rules to find the number of favorable outcomes and the total number of outcomes.
*   **Complementary Events:** The "at least one" trick is your best friend. `P(at least one) = 1 - P(none)`.
*   **"OR" Probability:** `P(A or B) = P(A) + P(B) - P(A and B)`. Remember to subtract the overlap.
*   **"AND" Probability:**
    *   Independent Events (with replacement): `P(A and B) = P(A) × P(B)`.
    *   Dependent Events (without replacement): `P(A and B) = P(A) × P(B | A)`.

---

### **MCQs for Exam Preparation**

1.  **Two unbiased coins are tossed. What is the probability of getting at most one head?**
    - [ ] 1/4
    - [ ] 1/2
    - [ ] 3/4
    - [ ] 1
    <br>

2.  **A single card is drawn from a standard deck of 52 cards. What is the probability that the card is a red face card?**
    - [ ] 3/13
    - [ ] 3/26
    - [ ] 1/26
    - [ ] 1/13
    <br>

3.  **Two dice are thrown simultaneously. What is the probability of getting a total score of 5?**
    - [ ] 1/9
    - [ ] 1/12
    - [ ] 1/6
    - [ ] 5/36
    <br>

4.  **A bag contains 6 white and 4 black balls. Two balls are drawn at random. Find the probability that they are of the same color.**
    - [ ] 1/2
    - [ ] 7/15
    - [ ] 8/15
    - [ ] 1/9
    <br>

5.  **Three unbiased coins are tossed. What is the probability of getting at least two heads?**
    - [ ] 1/4
    - [ ] 3/8
    - [ ] 1/2
    - [ ] 5/8
    <br>

6.  **In a lottery, there are 10 prizes and 25 blanks. A lottery is drawn at random. What is the probability of getting a prize?**
    - [ ] 1/10
    - [ ] 2/5
    - [ ] 2/7
    - [ ] 5/7
    <br>

7.  **From a pack of 52 cards, two cards are drawn together at random. What is the probability of both the cards being kings?**
    - [ ] 1/15
    - [ ] 25/57
    - [ ] 35/256
    - [ ] 1/221
    <br>

8.  **The letters of the word 'SOCIETY' are placed at random in a row. What is the probability that the three vowels come together?**
    - [ ] 1/7
    - [ ] 2/7
    - [ ] 3/7
    - [ ] 4/7
    <br>

9.  **A speaks truth in 75% of cases and B in 80% of cases. In what percentage of cases are they likely to contradict each other in stating the same fact?**
    - [ ] 20%
    - [ ] 25%
    - [ ] 35%
    - [ ] 45%
    <br>

10. **A committee of 3 is to be selected from a group of 4 boys and 5 girls. What is the probability that the committee has at least one boy?**
    - [ ] 5/42
    - [ ] 37/42
    - [ ] 10/21
    - [ ] 32/42
    <br>

**Answer Key**
1.  **C**: ||Sample Space S = {HH, HT, TH, TT}. Total outcomes = 4. "At most one head" means 0 heads or 1 head. Favorable outcomes E = {TT, HT, TH}. Number of favorable outcomes = 3. P(E) = 3/4.||
2.  **B**: ||There are 26 red cards. Face cards are J, Q, K. There are 3 red face cards in Hearts and 3 in Diamonds, for a total of 6. P(Red Face Card) = 6/52 = 3/26.||
3.  **A**: ||Total outcomes = 36. Favorable outcomes for a sum of 5 are (1,4), (2,3), (3,2), (4,1). There are 4 such outcomes. P(Sum=5) = 4/36 = 1/9.||
4.  **B**: ||"Same color" means (2 white) OR (2 black). Total balls = 10. Total ways to draw 2 balls = 10C2 = (10\*9)/2 = 45. Ways to draw 2 white balls = 6C2 = (6\*5)/2 = 15. Ways to draw 2 black balls = 4C2 = (4\*3)/2 = 6. Total favorable ways = 15 + 6 = 21. P(E) = 21/45 = 7/15.||
5.  **C**: ||Total outcomes for 3 coins = 2³ = 8. "At least two heads" means {HHT, HTH, THH, HHH}. There are 4 favorable outcomes. P(E) = 4/8 = 1/2.||
6.  **C**: ||Total outcomes = 10 prizes + 25 blanks = 35. Favorable outcomes (getting a prize) = 10. P(Prize) = 10/35 = 2/7.||
7.  **D**: ||Total ways to draw 2 cards = 52C2 = (52\*51)/2 = 1326. Ways to draw 2 kings from 4 kings = 4C2 = (4\*3)/2 = 6. P(2 Kings) = 6/1326 = 1/221.||
8.  **A**: ||Total arrangements of 'SOCIETY' (7 distinct letters) = 7!. Favorable arrangements: Treat the 3 vowels (OIE) as one block. We are arranging {S,C,T,Y, (OIE)}. These 5 items can be arranged in 5! ways. The vowels themselves can be arranged in 3! ways. Favorable ways = 5! \* 3!. P(E) = (5! \* 3!) / 7! = (5! \* 6) / (7 \* 6 \* 5!) = 6/42 = 1/7.||
9.  **C**: ||They contradict if one speaks truth and the other lies. Case 1: A truth, B lies. P = 0.75 \* 0.20 = 0.15. Case 2: A lies, B truth. P = 0.25 \* 0.80 = 0.20. Total probability of contradiction = 0.15 + 0.20 = 0.35, which is 35%.||
10. **B**: ||Use the complementary event trick. P(at least one boy) = 1 - P(no boys). Total people = 9. Total ways to form a committee of 3 = 9C3 = (9\*8\*7)/(3\*2\*1) = 84. "No boys" means all 3 are girls. Ways to select 3 girls from 5 = 5C3 = 5C2 = 10. P(no boys) = 10/84 = 5/42. P(at least one boy) = 1 - 5/42 = 37/42.||

---

### **Bonus Tips**

*   **P&C is the Base:** If you are stuck on a probability question, re-frame it as two separate counting problems: "In how many ways can my desired event happen?" and "In how many ways can *any* event happen?" The answer is the first divided by the second.
*   **The "1 Minus" Shortcut:** The phrase **"at least one"** should be a huge trigger in your mind to use the complementary event rule: `P(at least one) = 1 - P(none)`. Calculating the probability of "none" is almost always significantly easier.
*   **Visualize with Tables:** For problems with two dice, don't be afraid to quickly sketch out a 6x6 grid on your scratch paper to visualize the sums of all 36 outcomes. It's fast and prevents you from missing any favorable cases.
*   **Dependent vs. Independent:** The most common source of error in "AND" problems is confusing these two. Always ask yourself: "After the first event happens, does the total number of outcomes or the number of favorable outcomes change for the second event?" If yes, it's dependent. If no, it's independent.
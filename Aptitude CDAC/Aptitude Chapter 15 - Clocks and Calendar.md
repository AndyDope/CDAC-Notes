### **Logical Reasoning | Chapter 15: Clocks and Calendar**

Welcome to Chapter 15. This chapter deals with two distinct but related topics that test your understanding of cyclical patterns and modular arithmetic. **Clocks** problems involve calculating angles between the hands and relative speeds. **Calendar** problems involve finding the day of the week for a given date by understanding leap years and odd days.

---

### **Part 1: Clocks**

A clock is a circle of 360°. The problems almost always involve the minute hand and the hour hand.

#### **1. Speed of the Hands**

*   **Hour Hand:**
    *   Covers 360° in 12 hours. Speed = 360/12 = 30° per hour.
    *   Speed = 30° / 60 minutes = **0.5° per minute**.
*   **Minute Hand:**
    *   Covers 360° in 60 minutes. Speed = 360/60 = **6° per minute**.

*   **Relative Speed:** The minute hand is faster than the hour hand.
    *   Relative Speed = `6° - 0.5° = 5.5° per minute`.
    *   This means in one minute, the minute hand gains 5.5° on the hour hand. This is a crucial concept.

#### **2. Angle Between the Hands**

This is the most common type of clock problem.

**Formula:**
`Angle θ = | (11/2)M - 30H |`
Where:
*   `H` is the hour.
*   `M` is the minute.
*   The `|...|` means you take the absolute (positive) value.

**Example: What is the angle between the hands of a clock at 4:20?**
*   H = 4, M = 20.
*   `Angle = | (11/2) * 20 - 30 * 4 |`
*   `= | 11 * 10 - 120 |`
*   `= | 110 - 120 | = |-10| = 10°`.

*Note:* Sometimes a question asks for the reflex angle, which would be `360° - 10° = 350°`. Unless specified, give the smaller angle.

#### **3. Special Positions of the Hands**

*   **Hands Coincide (0° apart):** The hands are together. This happens **11 times in 12 hours** and 22 times in 24 hours. They gain 360° on each other.
*   **Hands are Opposite (180° apart):** The hands are in a straight line, pointing in opposite directions. This also happens **11 times in 12 hours**.
*   **Hands are at a Right Angle (90° apart):** This happens **22 times in 12 hours** (twice per hour, except at the 3 and 9 o'clock positions).

> **Quick Question:** At what time between 7 and 8 o'clock will the hands of a clock be in a straight line but not together? (i.e., opposite)
> **Answer:** At 7 o'clock, the minute hand is at 12 and the hour hand is at 7. The angle is 210°. To be opposite (180°), the minute hand must gain `210 - 180 = 30°` on the hour hand. Time required = `Degrees to gain / Relative Speed = 30 / 5.5 = 30 / (11/2) = 60/11 = 5 5/11` minutes. So, the time is **5 5/11 minutes past 7**.

---

### **Part 2: Calendar**

Calendar problems revolve around the concept of **odd days**.

#### **1. Odd Days**

An "odd day" is a remainder day. It's the number of days more than a complete week.
*   `10 days = 1 week + 3 odd days`.
*   `30 days = 4 weeks + 2 odd days`.
*   `31 days = 4 weeks + 3 odd days`.

**Number of Odd Days in a Year:**
*   **Ordinary Year:** 365 days = 52 weeks + **1 odd day**.
*   **Leap Year:** 366 days = 52 weeks + **2 odd days**.

#### **2. Leap Year**

A year is a leap year if it is divisible by 4.
*   **Exception:** A century year (like 1800, 1900, 2000) is a leap year **only if it is divisible by 400**.
    *   1900 is not a leap year (not divisible by 400).
    *   2000 is a leap year (divisible by 400).

#### **3. Finding the Day of the Week**

The method involves counting the total number of odd days from a known reference point.

**Reference:** The number of odd days in centuries.
*   100 years = 76 ordinary years + 24 leap years = 76\*1 + 24\*2 = 76 + 48 = 124 odd days.
*   124 days = 17 weeks + 5 days. So, **100 years have 5 odd days**.
*   200 years = 5 × 2 = 10 days = **3 odd days**.
*   300 years = 5 × 3 = 15 days = **1 odd day**.
*   400 years = (5 × 4) + 1 (for the leap year 400) = 21 days = **0 odd days**.
*   The cycle repeats every 400 years.

**Day Codes:**
*   0 odd days = Sunday
*   1 = Monday
*   2 = Tuesday
*   3 = Wednesday
*   4 = Thursday
*   5 = Friday
*   6 = Saturday

**Example: What was the day of the week on 15th August, 1947?**
1.  **Count years up to 1946:**
    *   Break it down: 1600 years + 300 years + 46 years.
    *   Odd days in 1600 years = 0.
    *   Odd days in 300 years = 1.
    *   Odd days in 46 years: Find leap years in 46 years = `46 / 4 = 11`.
        *   Ordinary years = 46 - 11 = 35.
        *   Odd days = (35 \* 1) + (11 \* 2) = 35 + 22 = 57 days.
        *   57 days = 8 weeks + 1 odd day.
    *   Total odd days up to 1946 = `0 + 1 + 1 = 2`.

2.  **Count days in 1947 up to Aug 15th:**
    *   Jan(3) + Feb(0) + Mar(3) + Apr(2) + May(3) + Jun(2) + Jul(3) + Aug(15)
    *   Sum = 31 days.
    *   31 days = 4 weeks + 3 odd days.

3.  **Total Odd Days:** `2 (from years) + 3 (from months) = 5`.

4.  **Find the Day:** 5 corresponds to **Friday**.

---

### **Topic Summary & Revision**

*   **Clocks:**
    *   `Angle = |(11/2)M - 30H|`. This formula is your primary tool.
    *   Relative speed of minute hand over hour hand is **5.5° per minute**.
    *   Hands coincide 11 times in 12 hours.
*   **Calendar:**
    *   It's all about counting **Odd Days** (remainders when divided by 7).
    *   Ordinary Year = 1 odd day. Leap Year = 2 odd days.
    *   A year is a leap year if divisible by 4, unless it's a century year, which must be divisible by 400.
    *   Memorize the odd days in centuries: 100=5, 200=3, 300=1, 400=0.
    *   Day codes: Sun=0, Mon=1, ..., Sat=6.

---

### **MCQs for Exam Preparation**

1.  **At 3:40, the hour hand and the minute hand of a clock form an angle of:**
    - [ ] 120°
    - [ ] 125°
    - [ ] 130°
    - [ ] 135°
    <br>

2.  **How many times in a day are the hands of a clock in a straight line but opposite in direction?**
    - [ ] 20
    - [ ] 22
    - [ ] 24
    - [ ] 48
    <br>

3.  **What was the day of the week on 28th May, 2006?**
    - [ ] Thursday
    - [ ] Friday
    - [ ] Saturday
    - [ ] Sunday
    <br>

4.  **A clock is started at noon. By 10 minutes past 5, the hour hand has turned through:**
    - [ ] 145°
    - [ ] 150°
    - [ ] 155°
    - [ ] 160°
    <br>

5.  **Which of the following is not a leap year?**
    - [ ] 2000
    - [ ] 2004
    - [ ] 1900
    - [ ] 1600
    <br>

6.  **At what time between 4 and 5 o'clock will the hands of a watch point in opposite directions?**
    - [ ] 45 min. past 4
    - [ ] 40 min. past 4
    - [ ] 50 4/11 min. past 4
    - [ ] 54 6/11 min. past 4
    <br>

7.  **Today is Monday. After 61 days, it will be:**
    - [ ] Wednesday
    - [ ] Saturday
    - [ ] Tuesday
    - [ ] Thursday
    <br>

8.  **A watch which gains uniformly is 2 minutes slow at noon on Monday and is 4 min 48 sec fast at 2 p.m. on the following Monday. When was it correct?**
    - [ ] 2 p.m. on Tuesday
    - [ ] 2 p.m. on Wednesday
    - [ ] 3 p.m. on Thursday
    - [ ] 1 p.m. on Friday
    <br>

9.  **The calendar for the year 2007 will be the same for the year:**
    - [ ] 2014
    - [ ] 2016
    - [ ] 2017
    - [ ] 2018
    <br>

10. **How many times do the hands of a clock coincide in a day?**
    - [ ] 20
    - [ ] 21
    - [ ] 22
    - [ ] 24
    <br>

**Answer Key**
1.  **C**: ||Angle = |(11/2)\*40 - 30\*3| = |11\*20 - 90| = |220 - 90| = 130°.||
2.  **B**: ||The hands are opposite (180° apart) once every hour, but in a 12-hour period, this happens only 11 times (the event between 5 and 7 o'clock happens exactly at 6). In a full day (24 hours), it happens 11 \* 2 = 22 times.||
3.  **D**: ||Years up to 2005: 2000 years (0 odd days) + 5 years. In 5 years, there is 1 leap year (2004). So, 4 ordinary + 1 leap = 4\*1 + 1\*2 = 6 odd days. Days in 2006: Jan(3) + Feb(0) + Mar(3) + Apr(2) + May(28). Sum = 36 days. Odd days = 36 mod 7 = 1. Total odd days = 6 + 1 = 7, which is 0 odd days. 0 corresponds to Sunday.||
4.  **C**: ||Time from noon to 5:10 is 5 hours and 10 minutes. Total minutes = (5 \* 60) + 10 = 310 minutes. The hour hand moves at 0.5° per minute. Total angle turned = 310 \* 0.5 = 155°.||
5.  **C**: ||A century year is a leap year only if it is divisible by 400. 1900 is divisible by 4 but not by 400, so it is not a leap year. 2000 and 1600 are divisible by 400.||
6.  **D**: ||At 4 o'clock, the hands are 20 minute spaces apart. To be opposite, they must be 30 minute spaces apart. The minute hand must gain 20+30=50 minute spaces. The minute hand gains 55 minute spaces in 60 minutes. Time to gain 50 spaces = (60/55) \* 50 = (12/11) \* 50 = 600/11 = 54 6/11 min. past 4.||
7.  **B**: ||Every 7 days, the day repeats. We just need to find the number of odd days in 61. 61 mod 7 = 5 (since 7\*8=56). So the day will be Monday + 5 days = Saturday.||
8.  **B**: ||Total time from Monday noon to next Monday 2 p.m. is 7 days and 2 hours = 170 hours. In this time, the watch gains a total of (2 min) + (4 min 48 sec) = 6 min 48 sec = 6.8 minutes. The watch gains 6.8 min in 170 hrs. It needs to gain 2 minutes to be correct. Time = (170 / 6.8) \* 2 = (1700 / 68) \* 2 = 25 \* 2 = 50 hours. 50 hours after Monday noon is 2 days and 2 hours, which is 2 p.m. on Wednesday.||
9.  **D**: ||For a calendar to repeat, the total number of odd days from the start year must be 0 (mod 7). 2007 (ord) -> 1 odd day. 2008 (leap) -> 2. 2009 (ord) -> 1. 2010 (ord) -> 1. 2011 (ord) -> 1. 2012 (leap) -> 2. Total up to 2012 end = 1+2+1+1+1+2=8 -> 1 odd day. 2013(1), 2014(1), 2015(1), 2016(2), 2017(1). Sum from 2007 to 2017 = 1+2+1+1+1+2+1+1+1+2+1 = 14. Since 14 is divisible by 7, the calendar for 2018 will be the same as 2007.||
10. **C**: ||The hands of a clock coincide 11 times in every 12 hours. In a full day (24 hours), they will coincide 11 \* 2 = 22 times.||
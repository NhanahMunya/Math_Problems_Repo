# Task List 02 — Combinatorics for Probability

> **Note:** This task list is still being developed. For now, please don’t work on it yet. :)

## Introduction

In probability theory, many problems reduce to counting:

* the number of all possible outcomes,
* the number of favorable outcomes,
* the number of possible arrangements, selections, or codes.

To do this systematically, combinatorics uses several standard counting models. These models help describe sample spaces, events, and structured random experiments.

The aim of this task list is to develop the ability to:

* recognize which counting model applies,
* distinguish between order and no order,
* distinguish between repetition and no repetition,
* distinguish between distinguishable and indistinguishable objects,
* use counting ideas in probability contexts.

## Theoretical Background

## Basic Counting Questions

Before solving a counting problem, always ask:

1. Does **order** matter?
2. Are we using **all objects** or only **some of them**?
3. Are **repetitions allowed**?
4. Are the objects **distinguishable** or **indistinguishable**?
5. Are we constructing a **sequence**, choosing a **set**, or arranging objects in a **row** or **circle**?

These questions determine which combinatorial model should be used.

## Recognizing the Correct Counting Model

When solving a counting problem, the main difficulty is usually not the formula itself, but recognizing which combinatorial model applies.

A useful strategy is to decide step by step:

* are we using all objects or only some of them?
* does order matter?
* are repetitions allowed?
* are the objects distinct or are some of them identical?

The following decision tree summarizes the most common cases.

```text
Start: What kind of outcome are we counting?

Are we using ALL objects or only SOME objects?

├─ SOME objects
│  │
│  ├─ Does order matter?
│  │  │
│  │  ├─ No
│  │  │  └─ Combination
│  │  │
│  │  └─ Yes
│  │     │
│  │     ├─ Repetition allowed
│  │     │  └─ Sequences with repetition
│  │     │
│  │     └─ No repetition
│  │        └─ k-permutations
│  │
│  └─ Typical idea:
│     selecting a group, drawing a sample, forming a code, assigning places
│
└─ ALL objects
   │
   ├─ Are the objects arranged in a row or in a circle?
   │  │
   │  ├─ In a row
   │  │  │
   │  │  ├─ All objects distinct
   │  │  │  └─ Permutation
   │  │  │
   │  │  └─ Some objects identical
   │  │     └─ Permutations with repeated elements
   │  │
   │  └─ In a circle
   │     └─ Circular permutation
   │
   └─ Typical idea:
      arranging books, seating people, arranging letters
```

This decision tree is only a guide, but in many elementary problems it helps identify the correct model immediately.

In practice, students should first decide whether the outcome is:

* a selection,
* an ordered sequence,
* a linear arrangement,
* or a circular arrangement.

They should then check whether repetitions are allowed and whether equal objects are treated as identical.

The sections below explain each of these counting models in more detail.

---

## Permutations

A **permutation** is an arrangement of all elements of a set, where order matters.

If a set contains $n$ distinct elements, then the number of permutations is

$$
P_n = n!
$$

Permutations are used when:

* all available objects are arranged,
* order matters,
* repetitions are not allowed.

Typical examples:

* arranging books on a shelf, 
* seating people in a row, 
* ordering questions in a test.

---

## Circular Permutations

When objects are arranged in a circle, rotations may represent the same arrangement.

If $n$ distinct objects are arranged around a circle and only relative position matters, then the number of circular permutations is

$$
(n-1)!
$$

This model is used when:

* objects are arranged around a round table, 
* absolute position is irrelevant,
* only relative placement matters.

---

## Combinations

A **combination** is a selection of elements where order does not matter.

The number of ways to choose $k$ elements from $n$ distinct elements is

$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$

Combinations are used when:

* only some objects are chosen,
* order does not matter,
* repetition is not allowed.

Typical examples:

* choosing a committee,
* selecting cards from a deck,
* choosing endpoints of a segment.

---

## k-Permutations (Ordered Selections Without Repetition)

In some European textbooks the term "variation" is used for ordered selections.
In this course we use the standard English terminology: **k-permutations** (ordered selections).

A **k-permutation** (or ordered selection without repetition) is an ordered selection of $(k)$ elements chosen from $(n)$ distinct elements, where no element may be used more than once.

The number of such ordered selections is

$$
P(n,k) = \frac{n!}{(n-k)!}
$$

This model is used when:

* only some objects are chosen,
* order matters,
* repetition is not allowed.

Typical examples:

* assigning medals,
* forming numbers with distinct digits,
* choosing ordered positions.

---

## Sequences With Repetition

A **sequence of length $(k)$** over an $(n)$-element set is an ordered selection where each position may contain any of the $(n)$ symbols and repetition is allowed.

The number of such sequences is

$$
n^k
$$

This model is used when:

* order matters,
* repetition is allowed,
* each position is chosen independently.

Typical examples:

* PIN codes,
* repeated coin tosses,
* repeated die rolls,
* telephone numbers.

---

## Permutations with Repeated Elements

When some objects are identical, the number of distinct permutations must account for indistinguishable elements. These are called **permutations with repeated elements** (or **permutations of a multiset**).

If among $n$ objects there are:

* $n_1$ identical objects of one type,
* $n_2$ identical objects of another type,
* and so on,

then the number of distinct arrangements is

$$
\frac{n!}{n_1!n_2!\dots n_r!}
$$

This model is used when:

* objects of the same type are indistinguishable,
* all objects are arranged,
* order matters at the level of positions, but equal objects are treated as identical.

Typical examples:

* arranging colored balls,
* arranging letters with repeated symbols.

---

## Distinguishable and Indistinguishable Objects

A fundamental distinction in combinatorics is whether objects are treated as **distinguishable** or **indistinguishable**.

### Distinguishable objects

Objects are distinguishable if they are treated as different individual items.

Example:

$$
R_1, R_2, R_3
$$

are three different red balls.

### Indistinguishable objects

Objects are indistinguishable if only their type matters.

Example:

three red balls all counted simply as

$$
R
$$

In many problems, the same physical collection may lead to different counts depending on how the outcomes are recorded.

---

## Order and Recording Rules

In combinatorial and probabilistic problems, the way outcomes are recorded is crucial.

Examples:

* If three balls are drawn and the order of drawing is recorded, then the outcome is a sequence.
* If the same three balls are drawn but only the selected set matters, then order is ignored.
* If only colors are recorded, then objects of the same color may become indistinguishable.

Thus the same experiment may lead to different sample spaces depending on the recording rule.

---

## Product Rule and Sum Rule

If a process consists of several independent stages, and:

* the first stage can be completed in $a$ ways,
* the second in $b$ ways,
* the third in $c$ ways,

then the whole process can be completed in

$$
a \cdot b \cdot c
$$

ways.

This rule is used throughout combinatorics, especially in code construction and multi-step selections.

---

If a task can be completed in one of several mutually exclusive ways, then the total number of outcomes is the sum of the numbers of outcomes in each case.

If one case gives $a$ possibilities and another disjoint case gives $b$, then the total is

$$
a+b
$$

This rule is useful when a problem must be split into cases.

---

## Summary: How to Recognize the Correct Model
A useful summary is:

* **Permutation**
  all objects used, order matters

* **Circular permutation**
  objects arranged in a circle (rotations treated as the same)

* **Combination**
  some objects chosen, order does not matter

* **k-permutation (ordered selection without repetition)**
  some objects chosen, order matters, no repetition

* **Sequences with repetition**
  some objects chosen, order matters, repetition allowed

* **Permutations with repeated elements**
  all objects arranged, but some are identical


## Task 01 – Basic Definitions and Classification

For each of the following situations, determine whether it is best described by:

* a permutation,
* a circular permutation,
* a combination,
* a k-permutation (ordered selection without repetition),
* a sequence with repetition,
* or a permutation with repeated elements.

In each case, briefly justify your choice.

1. Arranging 6 students in a line.
2. Choosing 3 students from a group of 10 for a committee.
3. Assigning gold, silver, and bronze medals among 12 finalists.
4. Forming a 4-digit PIN code.
5. Forming a 4-digit code with no repeated digits.
6. Tossing a coin 5 times and recording the sequence of results.
7. Drawing 2 balls from an urn without replacement, when order is ignored.
8. Drawing 2 balls from an urn without replacement, when order is recorded.
9. Arranging the letters of the word $LEVEL$.
10. Seating 5 people around a round table.

---

## Task 02 – Permutations

Solve the following problems.

1. How many different ways can 4 distinct books be arranged on a shelf?
2. In how many ways can 6 people sit on a bench?
3. How many 4-digit numbers with distinct digits can be formed from the digits 1, 2, 3, 4?
4. A survey consists of three questions: A, B, and C. In how many ways can the survey be arranged if only the order of the questions changes?
5. The number of permutations of an $n$-element set is 30 times smaller than the number of permutations of an $(n+2)$-element set. Determine $n$.

---

## Task 03 – Permutations with Restrictions

Solve the following problems involving arrangements with additional conditions.

1. In how many ways can 8 people sit at a round table if:

   * the seats are numbered,
   * only the relative arrangement of people matters?

2. Five people are to stand in a row. In how many ways can this be done if:

   * persons $X$ and $Y$ must stand next to each other,
   * there must be exactly two people standing between $X$ and $Y$?

3. How many 7-digit numbers can be formed using the digits 0, 1, 2, 3, 4, 5, 6, if no digit may repeat?

4. How many arrangements of the letters of the word $STATISTICS$ are possible?

---

## Task 04 – Combinations

Solve the following problems.

1. An urn contains 4 balls: white, black, blue, and green. Two balls are drawn without replacement. How many different outcomes are possible if order is ignored?
2. An urn contains balls numbered from 1 to 20. Three balls are drawn without replacement. How many possible samples contain only even numbers?
3. How many line segments can be formed by joining pairs of vertices of a convex octagon?
4. A class consists of 24 students, including 10 girls. In how many ways can a 2-person delegation consisting of one girl and one boy be chosen?
5. How many handshakes occur in a group of 10 people if each person shakes hands with every other person exactly once?

---

## Task 05 – Combinations in Card and Urn Problems

Solve the following problems.

1. From a standard 52-card deck, 5 cards are drawn without replacement. In how many ways can the hand contain exactly 2 hearts?
2. An urn contains 10 white balls and 6 black balls. Four balls are drawn without replacement. In how many ways can the sample contain exactly three balls of the same color?
3. In a lottery, only 10 out of 50 tickets are winning tickets. In how many ways can 4 tickets be chosen so that at least one of them is winning?
4. A box contains 12 working light bulbs and 3 defective ones. Five bulbs are selected without replacement. In how many ways can exactly 2 defective bulbs be chosen?

---

## Task 06 – k-Permutations (Ordered Selections Without Repetition)

Solve the following problems.

1. Let $X = {1,2,3}$. List all 2-digit numbers with distinct digits that can be formed from the elements of $X$. How many are there?
2. A safe code consists of 4 different digits chosen from 1 to 9. How many such codes are possible if the first digit must be greater than 6?
3. In the final round of a mathematics contest, 10 participants compete. In how many ways can the first three places be assigned?
4. How many 5-digit numbers with distinct digits are divisible by 5?
5. How many different arrangements of first, second, and third place are possible among 15 runners?

---

## Task 07 – Additional Problems on k-Permutations

Solve the following problems.

1. An urn contains 9 balls numbered from 1 to 9. Three balls are drawn successively without replacement, and their numbers are written in order to form a 3-digit number. How many such numbers are smaller than 780?

2. In a factory, employee identifiers are to be introduced. Each identifier consists of:

   * two different letters chosen from the set ${A,B,C,D}$,
   * followed by three different digits.

   How many such identifiers are possible?

3. Would this number of identifiers be sufficient for 8600 employees?

4. A sports federation must assign the labels A, B, C, and D to four different teams selected from 12 teams. In how many ways can this be done?

---

## Task 08 – Sequences With Repetition

A sequence with repetition is an ordered selection in which the same element may appear more than once.

Solve the following problems.

1. How many different outcomes are possible when a coin is tossed 3 times?
2. In how many different ways can 4 people enter a tram consisting of 2 cars?
3. In how many ways can 5 different objects be placed into 3 drawers?
4. In a 10-floor building, 6 people enter an elevator on the ground floor. In how many different ways can they leave the elevator on the various floors?
5. How many different 4-letter words can be formed from the alphabet

$$
{A,B,C}
$$

if repetition is allowed?

---

## Task 09 – Numbers, Codes, and Sequences with Repetition

Solve the following problems.

1. An urn contains balls numbered from 1 to 8. Three balls are drawn successively, with replacement after each draw, and the numbers are written in order to form a 3-digit number. How many such numbers can be formed?
2. How many different 6-digit telephone numbers are possible if the first digit cannot be 0?
3. How many even 5-digit numbers exist?
4. How many sequences of length at most 7 can be formed using the alphabet ${a,b}$?
5. How many different 4-digit numbers can be obtained by rolling a die 4 times and recording the results in order?

---

## Task 10 – PIN Codes and Access Codes: Distinguishable Positions

This task compares several types of codes built from digits and focuses on the meaning of order, repetition, and position.

A security system uses codes made of digits from $0$ to $9$.

1. How many different 4-digit PIN codes are possible if:

   * digits may repeat,
   * leading zero is allowed?

2. How many different 4-digit codes are possible if:

   * digits may not repeat,
   * leading zero is allowed?

3. How many different 4-digit numbers are possible if:

   * digits may repeat,
   * the first digit cannot be zero?

4. How many different 4-digit numbers are possible if:

   * digits may not repeat,
   * the first digit cannot be zero?

5. For each case, determine whether the model is:

   * a sequence with repetition,
   * a k-permutation (ordered selection without repetition),
   * or a modified counting problem with an additional restriction.

6. Explain why the codes

$$
1234
$$

and

$$
4321
$$

must be treated as different outcomes.

7. Explain why a PIN code and a 4-digit number are not always counted in the same way.

---

## Task 11 – Colored Balls: Distinguishable and Indistinguishable Objects

A box contains the following balls:

* 4 red,
* 4 blue,
* 3 green.

Thus there are 11 balls in total.

In some questions, balls of the same color are treated as indistinguishable. In other questions, every ball is treated as individually labeled and therefore distinguishable.

1. How many different linear arrangements of all 11 balls are possible if balls of the same color are indistinguishable?
2. How many different linear arrangements are possible if all 11 balls are distinguishable, for example labeled as

$$
R1, R2, R3, R4, B1, B2, B3, B4, G1, G2, G3
$$

3. Three balls are drawn without replacement, and only the sequence of colors is recorded. How many different outcomes are possible?

4. Three balls are drawn without replacement, and the actual labeled balls are recorded. How many different outcomes are possible?

5. Three balls are selected without replacement, but order is ignored and only the color composition is recorded. List all possible color compositions.

6. Explain carefully the difference between:

   * distinguishable objects,
   * indistinguishable objects,
   * recording order,
   * ignoring order.

7. For each part of the problem, identify which counting idea is most relevant:

   * permutations,
   * combinations,
   * k-permutations (ordered selections without repetition),
   * permutations with repeated elements.

---

## Task 12 – Interactive HTML: Visualizing PIN Codes

Design a minimal interactive HTML/JavaScript tool illustrating the counting principles from Task 10.

Create an interactive webpage that:

1. allows the user to choose:

   * code length,
   * whether repetition is allowed,
   * whether leading zero is allowed,

2. generates example codes satisfying the selected rules,

3. displays the total number of possible codes,

4. visually explains why changing the order of digits produces a different code,

5. shows a small sample of generated outcomes,

6. includes a short explanation of which combinatorial model is used in the selected case.

The visual style should be minimal and focused on clarity.

---

## Task 13 – Interactive HTML: Visualizing Colored Balls

Design a minimal interactive HTML/JavaScript tool illustrating the ideas from Task 11.

Create an interactive webpage that:

1. shows a collection of colored balls:

   * red,
   * blue,
   * green,

2. allows switching between two views:

   * balls distinguished only by color,
   * balls individually labeled,

3. allows the user to:

   * arrange all balls in a row,
   * draw 3 balls without replacement,
   * choose whether order is recorded,

4. displays how the number of possible outcomes changes depending on:

   * distinguishability,
   * order,
   * replacement or no replacement,

5. lists example outcomes in each mode,

6. includes a short explanation of why two red balls may or may not count as different depending on the model.

The webpage should be visually simple and didactic.

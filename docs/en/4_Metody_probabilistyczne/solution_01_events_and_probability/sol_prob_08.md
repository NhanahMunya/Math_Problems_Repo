# Task 8

## Problem

Coded information consists of seven pulses of types **A, B, C** in quantities: **four pulses of A**, **two pulses of B**, and **one pulse of C**. Assuming a **random arrangement of pulses**, find the probability that:

1. the **first received pulse will be A**,
2. the **first received pulse will be A or C**,
3. the **first two pulses will be A and C in that order**.

---

# Step 1 – Total number of pulses

We have:

| Pulse | Quantity |
| ----- | -------- |
| A     | 4        |
| B     | 2        |
| C     | 1        |

Total pulses:

4 + 2 + 1 = **7**

Since the arrangement is random, each position is equally likely to contain any remaining pulse.

---

# 1. Probability that the first pulse is A

There are **4 pulses of type A** out of **7 total pulses**.

P(first pulse = A) = 4 / 7

---

# 2. Probability that the first pulse is A or C

Number of pulses that satisfy the condition:

A pulses = 4
C pulses = 1

Total favorable pulses:

4 + 1 = **5**

Probability:

P(first pulse = A or C) = 5 / 7

---

# 3. Probability that the first two pulses are A and C (in that order)

We calculate step by step.

### First pulse

Probability it is A:

P(first = A) = 4 / 7

---

### Second pulse

After taking one A, the remaining pulses are:

| Pulse | Remaining |
| ----- | --------- |
| A     | 3         |
| B     | 2         |
| C     | 1         |

Total remaining pulses:

6

Probability the second pulse is C:

P(second = C | first = A) = 1 / 6

---

### Multiply probabilities

P(first = A and second = C)

= (4/7) × (1/6)

= **4/42**

Simplify:

= **2/21**

---

# Final Results

| Event                         | Probability |
| ----------------------------- | ----------- |
| First pulse is A              | **4/7**     |
| First pulse is A or C         | **5/7**     |
| First two pulses are A then C | **2/21**    |

---

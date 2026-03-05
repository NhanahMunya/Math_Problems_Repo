# Task 3

## Problem

Person **X** performs a certain job in **4, 5, or 6 hours** and may commit **0, 1, or 2 errors**. Assuming equal probability for each of the **9 possible elementary events** (pairs: time, number of errors), find the probability of the following events:

1. The job will be completed in **4 hours**.
2. The job will be completed **flawlessly in 6 hours**.
3. The job will be completed in **at most 5 hours**.
4. The job will be completed in **at most 5 hours and with at most one error**.

---

# Step 1 – Sample Space

The possible times are:

4, 5, 6 hours

The possible number of errors:

0, 1, 2

All combinations form the sample space Ω:

Ω =
{
(4,0), (4,1), (4,2),
(5,0), (5,1), (5,2),
(6,0), (6,1), (6,2)
}

Total number of elementary events:

|Ω| = 9

Since all outcomes are equally likely:

P(each outcome) = 1/9

---

# 1. The job will be completed in 4 hours

Event A:

A = {(4,0), (4,1), (4,2)}

Number of favorable outcomes:

|A| = 3

Probability:

P(A) = 3 / 9 = **1/3**

---

# 2. The job will be completed flawlessly in 6 hours

"Flawlessly" means **0 errors**.

Event B:

B = {(6,0)}

Number of favorable outcomes:

|B| = 1

Probability:

P(B) = 1 / 9

---

# 3. The job will be completed in at most 5 hours

"At most 5 hours" means **4 or 5 hours**.

Event C:

C =
{
(4,0), (4,1), (4,2),
(5,0), (5,1), (5,2)
}

Number of favorable outcomes:

|C| = 6

Probability:

P(C) = 6 / 9 = **2/3**

---

# 4. The job will be completed in at most 5 hours and with at most one error

Conditions:

time ≤ 5
errors ≤ 1

Event D:

D =
{
(4,0), (4,1),
(5,0), (5,1)
}

Number of favorable outcomes:

|D| = 4

Probability:

P(D) = 4 / 9

---

# Final Results

| Event                               | Probability |
| ----------------------------------- | ----------- |
| Completed in 4 hours                | **1/3**     |
| Flawless job in 6 hours             | **1/9**     |
| Completed in at most 5 hours        | **2/3**     |
| Completed in ≤5 hours with ≤1 error | **4/9**     |

---

# Task 5

## Problem

We consider the volume (in **dm³**) of water that a concrete culvert can conduct per second. Past observations allow us to assume that:

* The probability that the volume of water takes a value from the interval ⟨125, 250⟩ is **P(A) = 0.6**
* The probability that the volume of water takes a value from the interval (200, 300⟩ is **P(B) = 0.7**
* The probability of the union of these events is **P(A ∪ B) = 0.8**

Calculate the probability:

1. **P(A′)** (complementary event to A)
2. **P(A ∩ B)** (intersection of intervals)
3. **P(A′ ∩ B′)** (water volume does not fall into either of these intervals)

---

# Step 1 – Complement of A

The complement of an event A means the event **A does not occur**.

Formula:

P(A′) = 1 − P(A)

Substitute the value:

P(A′) = 1 − 0.6

P(A′) = **0.4**

---

# Step 2 – Find the intersection P(A ∩ B)

We use the probability formula for the union of two events:

P(A ∪ B) = P(A) + P(B) − P(A ∩ B)

Substitute the known values:

0.8 = 0.6 + 0.7 − P(A ∩ B)

First add:

0.6 + 0.7 = 1.3

So:

0.8 = 1.3 − P(A ∩ B)

Solve for the intersection:

P(A ∩ B) = 1.3 − 0.8

P(A ∩ B) = **0.5**

---

# Step 3 – Find P(A′ ∩ B′)

Using **De Morgan’s law**:

A′ ∩ B′ = (A ∪ B)′

Therefore:

P(A′ ∩ B′) = 1 − P(A ∪ B)

Substitute:

P(A′ ∩ B′) = 1 − 0.8

P(A′ ∩ B′) = **0.2**

---

# Final Results

| Event      | Probability |
| ---------- | ----------- |
| P(A′)      | **0.4**     |
| P(A ∩ B)   | **0.5**     |
| P(A′ ∩ B′) | **0.2**     |

---

# Interpretation

* **P(A′)** means the water volume is **outside the interval ⟨125,250⟩**.
* **P(A ∩ B)** represents the probability that the volume lies in **both intervals simultaneously**, meaning the overlapping range.
* **P(A′ ∩ B′)** means the water volume lies **outside both intervals**.

---

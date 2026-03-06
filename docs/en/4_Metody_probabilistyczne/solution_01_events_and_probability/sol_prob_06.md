# Task 6

## Problem

Identical products manufactured by **2 automated machines** are placed on a conveyor belt. The quantitative ratio of production of the **first machine** to the production of the **second** is **3 : 2**.

The **first machine** produces on average **65% of first-grade products**, while the **second produces 85%**.

1. One product is randomly selected from the products on the conveyor belt. Calculate the probability that it will be a **first-grade product** (use the **total probability formula**).

2. A randomly selected product turned out to be of **first quality**. Calculate the probability that it was produced by the **first machine** (use **Bayes’ theorem**).

---

# Step 1 – Define the events

Let:

A₁ = product was produced by machine 1
A₂ = product was produced by machine 2

B = product is **first-grade**

---

# Step 2 – Probabilities of selecting products from each machine

Production ratio:

3 : 2

Total parts = 5

Therefore:

P(A₁) = 3/5
P(A₂) = 2/5

---

# Step 3 – Conditional probabilities

From the problem:

P(B | A₁) = 0.65
P(B | A₂) = 0.85

These represent the probability that a product is **first-grade given the machine** that produced it.

---

# 1. Probability that a randomly chosen product is first-grade

Using the **Total Probability Formula**:

P(B) = P(A₁)P(B | A₁) + P(A₂)P(B | A₂)

Substitute values:

P(B) = (3/5)(0.65) + (2/5)(0.85)

Compute:

(3/5)(0.65) = 0.39
(2/5)(0.85) = 0.34

Add them:

P(B) = 0.39 + 0.34

P(B) = **0.73**

---

# 2. Probability that a first-grade product came from machine 1

Now we use **Bayes’ theorem**:

P(A₁ | B) = (P(A₁)P(B | A₁)) / P(B)

Substitute the values:

P(A₁ | B) = (3/5 × 0.65) / 0.73

We already calculated:

3/5 × 0.65 = 0.39

So:

P(A₁ | B) = 0.39 / 0.73

P(A₁ | B) ≈ **0.534**

---

# Final Results

| Event                                   | Probability |
| --------------------------------------- | ----------- |
| Product is first-grade                  | **0.73**    |
| First-grade product came from machine 1 | **≈ 0.534** |

---

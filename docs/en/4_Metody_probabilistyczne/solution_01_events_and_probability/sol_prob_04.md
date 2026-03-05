# Task 4

## Problem

A fragment of an electrical network consists of two elements connected in **parallel**: **a₁** and **a₂**. Let **Aᵢ, i = 1, 2**, denote the event that element **aᵢ** remains functional for at least time **t**.

Calculate the probability of continuous current flow through this system for at least time **t**, given that:

* **P(A₁) = P(A₂) = p**
* the probability of simultaneous functionality of both elements is
  **P(A₁ ∩ A₂) = p²**

---

# Step 1 – Understand the circuit

The elements **a₁** and **a₂** are connected **in parallel**.

For a **parallel system**, current flows if **at least one element works**.

Therefore the event that the system works is:

A = A₁ ∪ A₂

---

# Step 2 – Use the union probability formula

For any two events:

P(A₁ ∪ A₂) = P(A₁) + P(A₂) − P(A₁ ∩ A₂)

---

# Step 3 – Substitute the given probabilities

We are given:

P(A₁) = p
P(A₂) = p
P(A₁ ∩ A₂) = p²

Substitute into the formula:

P(A) = p + p − p²

---

# Step 4 – Simplify

P(A) = 2p − p²

---

# Final Result

The probability that the current flows continuously through the system is

**P(A) = 2p − p²**

---

# Interpretation

The circuit works if:

* **a₁ works**
* **or a₂ works**
* **or both work**

Because both working (**A₁ ∩ A₂**) was counted twice, we subtract **p²** once.

---

✅ **Final formula**

**P(system works) = 2p − p²**

---

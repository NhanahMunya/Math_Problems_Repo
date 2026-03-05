# Task 4: Parallel Circuit Probability Analysis

## Problem Statement
A fragment of an electrical network consists of two elements connected in **parallel**: **a₁** and **a₂**. 

Let **Aᵢ, i = 1, 2**, denote the event that element **aᵢ** remains functional for at least time **t**.

Calculate the probability of continuous current flow through this system for at least time **t**, given that:
* **P(A₁) = P(A₂) = p**
* **P(A₁ ∩ A₂) = p²**

---

## Solution

### Step 1 – Understand the Parallel Circuit

The elements **a₁** and **a₂** are connected **in parallel**.

**Key concept:** In a parallel system, current flows if **at least one element works**.

Therefore, the event that the system works is:

```
A = A₁ ∪ A₂
```

**Visual representation:**
```
    ──[a₁]──
   |        |
───┤        ├───
   |        |
    ──[a₂]──
```

---

### Step 2 – Apply the Union Probability Formula

For any two events, the probability of their union is:

```
P(A₁ ∪ A₂) = P(A₁) + P(A₂) − P(A₁ ∩ A₂)
```

**Why subtract P(A₁ ∩ A₂)?**
- When we add P(A₁) + P(A₂), we count the case where **both** elements work **twice**
- We must subtract it once to avoid double-counting

---

### Step 3 – Substitute Given Values

We are given:
- **P(A₁) = p** (probability element a₁ works)
- **P(A₂) = p** (probability element a₂ works)
- **P(A₁ ∩ A₂) = p²** (probability **both** elements work)

Substitute into the formula:

```
P(A) = p + p − p²
```

---

### Step 4 – Simplify the Expression

```
P(A) = 2p − p²
```

We can also factor this:

```
P(A) = p(2 − p)
```

---

## Final Result

The probability that current flows continuously through the system for at least time **t** is:

### **P(A) = 2p − p²**

or equivalently:

### **P(A) = p(2 − p)**

---

## Understanding the Solution

### What does each term represent?

| Term | Meaning |
|------|---------|
| **2p** | Probability that **at least one** element works (if we incorrectly count overlaps) |
| **−p²** | Correction for **double-counting** when both elements work |
| **2p − p²** | Actual probability that **at least one** element works |

---

### Intuitive Breakdown

The system works in three mutually exclusive scenarios:

1. **Only a₁ works** (and a₂ fails)
2. **Only a₂ works** (and a₁ fails)
3. **Both a₁ and a₂ work**

**Why the formula works:**
- P(A₁) = p includes scenarios 1 and 3
- P(A₂) = p includes scenarios 2 and 3
- Adding them: p + p counts scenario 3 **twice**
- Subtracting P(A₁ ∩ A₂) = p² removes the duplicate

---

### Example with Numbers

Let's say **p = 0.8** (80% chance each element works):

```
P(A) = 2(0.8) − (0.8)²
     = 1.6 − 0.64
     = 0.96
```

**Result:** There's a **96% chance** the parallel system works!

**Why higher than 80%?**
- Because you have **two chances** for current to flow
- Even if one element fails, the other might still work
- This is the **reliability advantage** of parallel systems

---

### Verification Using Complement

Alternative approach: Calculate the probability that the system **fails**:

```
P(system fails) = P(both elements fail)
                = P(A₁ᶜ ∩ A₂ᶜ)
```

If we assume **independence** (implied by P(A₁ ∩ A₂) = p²):

```
P(A₁ᶜ) = 1 − p
P(A₂ᶜ) = 1 − p
P(both fail) = (1 − p)(1 − p) = (1 − p)²
```

Therefore:

```
P(system works) = 1 − (1 − p)²
                = 1 − (1 − 2p + p²)
                = 2p − p²  ✓
```

This confirms our answer!

---

## Key Takeaways

✅ **Parallel circuits are more reliable** – probability increases compared to a single element

✅ **Union formula** is essential for "at least one" scenarios

✅ **Always subtract overlaps** to avoid double-counting

✅ **Final formula: P(system works) = 2p − p²**

---

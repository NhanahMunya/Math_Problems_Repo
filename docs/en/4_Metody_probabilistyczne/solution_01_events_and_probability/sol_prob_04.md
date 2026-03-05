# ⚡ Parallel Circuit Probability Analysis

![Math](https://img.shields.io/badge/Math-Probability-blue)
![Circuits](https://img.shields.io/badge/Circuits-Parallel-green)
![Status](https://img.shields.io/badge/Status-Complete-success)

> **An interactive guide to calculating the probability of continuous current flow in parallel electrical networks**

---

## 📋 Problem Statement

A fragment of an electrical network consists of two elements connected in **parallel**: **a₁** and **a₂**.

Let **Aᵢ, i = 1, 2**, denote the event that element **aᵢ** remains functional for at least time **t**.

**Calculate** the probability of continuous current flow through this system for at least time **t**, given that:

- **P(A₁) = P(A₂) = p**
- **P(A₁ ∩ A₂) = p²**

---

## 🔍 Solution

### Step 1 – Understanding Parallel Circuits

The elements **a₁** and **a₂** are connected **in parallel**.

**Key Concept:** In a parallel system, current flows if **at least one element works**.

Therefore, the event that the system works is:

```
A = A₁ ∪ A₂
```

**Visual Representation:**

```
    ──[a₁]──
   |        |
───┤        ├───
   |        |
    ──[a₂]──
```

> 💡 The system works when element 1 **OR** element 2 (or both) work

---

### Step 2 – Union Probability Formula

For any two events, the probability of their union is:

```
P(A₁ ∪ A₂) = P(A₁) + P(A₂) − P(A₁ ∩ A₂)
```

#### ⚠️ Why Subtract P(A₁ ∩ A₂)?

- When we add `P(A₁) + P(A₂)`, we count the case where **both** elements work **twice**
- We must subtract it once to avoid **double-counting**

---

### Step 3 – Substitute Given Values

We are given:

| Term | Value | Meaning |
|------|-------|---------|
| **P(A₁)** | `p` | Probability element a₁ works |
| **P(A₂)** | `p` | Probability element a₂ works |
| **P(A₁ ∩ A₂)** | `p²` | Probability **both** elements work |

Substituting into the formula:

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

## 🎯 Final Result

The probability that current flows continuously through the system for at least time **t** is:

### **P(A) = 2p − p²**

or equivalently:

### **P(A) = p(2 − p)**

---

## 💡 Understanding the Solution

### What Does Each Term Represent?

| Term | Meaning |
|------|---------|
| **2p** | Probability that **at least one** element works (with double-counting) |
| **−p²** | Correction for **double-counting** when both elements work |
| **2p − p²** | Actual probability that **at least one** element works |

---

### Intuitive Breakdown

The system works in **three mutually exclusive scenarios**:

1. ✅ **Only a₁ works** (and a₂ fails)
2. ✅ **Only a₂ works** (and a₁ fails)
3. ✅ **Both a₁ and a₂ work**

**Why the formula works:**

- `P(A₁) = p` includes scenarios 1 and 3
- `P(A₂) = p` includes scenarios 2 and 3
- Adding them: `p + p` counts scenario 3 **twice**
- Subtracting `P(A₁ ∩ A₂) = p²` removes the duplicate

---

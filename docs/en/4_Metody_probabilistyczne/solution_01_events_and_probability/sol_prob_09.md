# 🏭 Quality Control Probability Analysis

![Math](https://img.shields.io/badge/Math-Probability-blue)
![Statistics](https://img.shields.io/badge/Topic-Quality_Control-orange)
![Status](https://img.shields.io/badge/Status-Complete-success)

> **Calculating the probability of selecting a first-quality item from multiple manufacturing plants**

---

## 📋 Problem Statement

A certain good is produced by **3 plants**. The probability of producing **first-quality goods** by these plants is:

- **Plant 1:** `P₁ = 0.97`
- **Plant 2:** `P₂ = 0.90`
- **Plant 3:** `P₃ = 0.86`

**Find:** The probability that a randomly taken item — from among three items originating (one each) from different plants — is of **first quality**.

---

## 🔍 Solution Overview

This problem involves:
- **3 plants** producing goods with different quality probabilities
- **3 items** total (one from each plant)
- **Random selection** of one item from the three
- Finding the probability the selected item is **first-quality**

---

## 🎯 Solution

### Step 1 – Understand the Setup

We have:
- **3 items** total: one from Plant 1, one from Plant 2, one from Plant 3
- We randomly select **1 item** from these 3
- Each item has an **equal probability** of being selected: `1/3`

```
Plant 1 → Item₁ (quality prob = 0.97)
Plant 2 → Item₂ (quality prob = 0.90)
Plant 3 → Item₃ (quality prob = 0.86)
          ↓
    Random Selection
```

---

### Step 2 – Define Events

Let **Qᵢ** = event that an item from Plant **i** is first-quality

- **Q₁** = item from Plant 1 is first-quality, `P(Q₁) = 0.97`
- **Q₂** = item from Plant 2 is first-quality, `P(Q₂) = 0.90`
- **Q₃** = item from Plant 3 is first-quality, `P(Q₃) = 0.86`

Let **Sᵢ** = event that we select the item from Plant **i**

- `P(S₁) = P(S₂) = P(S₃) = 1/3` (equal probability of selection)

---

### Step 3 – Apply the Law of Total Probability

The probability that the randomly selected item is first-quality is:

```
P(first-quality) = P(Q₁ and S₁) + P(Q₂ and S₂) + P(Q₃ and S₃)
```

Using the multiplication rule:

```
P(first-quality) = P(Q₁) × P(S₁) + P(Q₂) × P(S₂) + P(Q₃) × P(S₃)
```

---

### Step 4 – Substitute Values

```
P(first-quality) = 0.97 × (1/3) + 0.90 × (1/3) + 0.86 × (1/3)
```

Factor out `1/3`:

```
P(first-quality) = (1/3) × (0.97 + 0.90 + 0.86)
```

---

### Step 5 – Calculate

```
P(first-quality) = (1/3) × (2.73)
                 = 2.73/3
                 = 0.91
```

---

## 🎯 Final Result

The probability that a randomly selected item is of first quality is:

### **P(first-quality) = 0.91 or 91%**

---

## 💡 Understanding the Solution

### Why Do We Average the Probabilities?

Since we're selecting **randomly** from the 3 items with **equal probability** (`1/3` each), the overall probability is the **weighted average** of the individual plant probabilities.

```
P(first-quality) = (1/3) × P₁ + (1/3) × P₂ + (1/3) × P₃
                 = (P₁ + P₂ + P₃) / 3
```

This is the **arithmetic mean** of the three quality probabilities!

---

### Visual Breakdown

| Step | Description | Probability |
|:----:|-------------|:-----------:|
| 1 | Select item from Plant 1 | `1/3` |
| 2 | That item is first-quality | `0.97` |
| → | Combined: Select Plant 1 AND first-quality | `1/3 × 0.97 = 0.3233` |
| | | |
| 1 | Select item from Plant 2 | `1/3` |
| 2 | That item is first-quality | `0.90` |
| → | Combined: Select Plant 2 AND first-quality | `1/3 × 0.90 = 0.3000` |
| | | |
| 1 | Select item from Plant 3 | `1/3` |
| 2 | That item is first-quality | `0.86` |
| → | Combined: Select Plant 3 AND first-quality | `1/3 × 0.86 = 0.2867` |
| | | |
| **Total** | **Sum of all paths** | **0.91** |

---

## 📊 Detailed Calculation

### Method 1: Law of Total Probability

```
P(Q) = P(Q|S₁)×P(S₁) + P(Q|S₂)×P(S₂) + P(Q|S₃)×P(S₃)
     = 0.97×(1/3) + 0.90×(1/3) + 0.86×(1/3)
     = 0.3233 + 0.3000 + 0.2867
     = 0.91
```

### Method 2: Arithmetic Mean

```
P(Q) = (P₁ + P₂ + P₃) / 3
     = (0.97 + 0.90 + 0.86) / 3
     = 2.73 / 3
     = 0.91
```

### Method 3: Step-by-Step Addition

```
Step 1: 0.97 / 3 = 0.323333...
Step 2: 0.90 / 3 = 0.300000...
Step 3: 0.86 / 3 = 0.286666...
        ─────────────────────
Sum:              = 0.910000  ✓
```

---

## 🎓 Key Concepts Applied

### 1. Law of Total Probability

When an event can occur through multiple mutually exclusive paths:

```
P(A) = Σ P(A|Bᵢ) × P(Bᵢ)
```

### 2. Independence

The quality of an item is **independent** of which item we select. Selection doesn't change the item's quality.

### 3. Weighted Average

When selections are equally likely, the result is the arithmetic mean:

```
P = (p₁ + p₂ + ... + pₙ) / n
```

---

## 🔢 Verification

Let's verify using the complement (probability of selecting a defective item):

```
P(defective from Plant 1) = 1 - 0.97 = 0.03
P(defective from Plant 2) = 1 - 0.90 = 0.10
P(defective from Plant 3) = 1 - 0.86 = 0.14

P(selected item is defective) = (0.03 + 0.10 + 0.14) / 3
                               = 0.27 / 3
                               = 0.09

P(selected item is first-quality) = 1 - 0.09
                                   = 0.91  ✓
```

**Confirmed!** Both methods give the same answer.

---

## 📊 General Formula

For **n plants** with quality probabilities `p₁, p₂, ..., pₙ` and equal selection probability:

```
P(first-quality) = (p₁ + p₂ + ... + pₙ) / n = (Σpᵢ) / n
```

For **n plants** with selection probabilities `w₁, w₂, ..., wₙ`:

```
P(first-quality) = p₁×w₁ + p₂×w₂ + ... + pₙ×wₙ = Σ(pᵢ × wᵢ)
```

Where `Σwᵢ = 1` (weights sum to 1)

---

## 🎯 Key Takeaways

✅ **Equal selection** → Use arithmetic mean of probabilities

✅ **Unequal selection** → Use weighted average

✅ **Law of Total Probability** is the foundation

✅ **Independence** allows multiplication of probabilities

✅ **Final Answer: P(first-quality) = 0.91 or 91%**

---

## 🧮 Quick Reference

| Given | Value |
|-------|:-----:|
| P(Plant 1 produces first-quality) | 0.97 |
| P(Plant 2 produces first-quality) | 0.90 |
| P(Plant 3 produces first-quality) | 0.86 |
| P(Selecting any specific item) | 1/3 |
| **Result** | **0.91** |

### Formula Used

```
P(Q) = (1/3) × (P₁ + P₂ + P₃)
     = (1/3) × (0.97 + 0.90 + 0.86)
     = (1/3) × 2.73
     = 0.91
```

---


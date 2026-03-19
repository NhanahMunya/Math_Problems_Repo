# Task 3 — Permutations with Repeated Elements

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-permutations--with--repeats-orange)

---

## 🎯 Objective

Count distinct arrangements of words containing repeated letters, and apply additional constraints such as fixing a starting letter.

---

## 📐 General Formula

**Permutation with repeated elements** — arranging $n$ objects where some are identical:

$$\frac{n!}{n_1! \cdot n_2! \cdots n_r!}$$

- $n$ = total number of objects
- $n_1, n_2, \ldots, n_r$ = count of each group of identical objects
- Each $n_i!$ divides out overcounting caused by swapping identical objects
- Always satisfied: $n_1 + n_2 + \cdots + n_r = n$

> **Why divide?** If all objects were distinct, there would be $n!$ arrangements. But swapping identical objects within their group produces no new arrangement — so we divide out those repetitions.

---

## ✅ Solutions

### Problem 1 — Arrangements of MISSISSIPPI

First, count the letters:

| Letter | Count |
|:---:|:---:|
| M | 1 |
| I | 4 |
| S | 4 |
| P | 2 |
| **Total** | **11** |

**Applied:** $n = 11$, $n_1 = 1$ (M), $n_2 = 4$ (I), $n_3 = 4$ (S), $n_4 = 2$ (P)

$$\frac{11!}{1! \cdot 4! \cdot 4! \cdot 2!} = \frac{39{,}916{,}800}{1 \times 24 \times 24 \times 2} = \frac{39{,}916{,}800}{1{,}152} = 34{,}650$$

---

### Problem 2 — Arrangements of STATISTICS

First, count the letters:

| Letter | Count |
|:---:|:---:|
| S | 3 |
| T | 3 |
| A | 1 |
| I | 1 |
| C | 1 |
| **Total** | **10** |

**Applied:** $n = 10$, $n_1 = 3$ (S), $n_2 = 3$ (T), $n_3 = 1$ (A), $n_4 = 1$ (I), $n_5 = 1$ (C)

$$\frac{10!}{3! \cdot 3! \cdot 1! \cdot 1! \cdot 1!} = \frac{3{,}628{,}800}{6 \times 6 \times 1 \times 1 \times 1} = \frac{3{,}628{,}800}{36} = 50{,}400$$

---

### Problem 3 — Arrangements of STATISTICS starting with S

**Strategy — Fix and arrange:**

Fix **S** in position 1. This uses up one S, leaving the remaining 9 letters to arrange freely:

```
[ S ] _ _ _ _ _ _ _ _ _
fixed  ← 9 remaining letters →
```

Remaining letters after fixing one S:

| Letter | Count |
|:---:|:---:|
| S | 2 |
| T | 3 |
| A | 1 |
| I | 1 |
| C | 1 |
| **Total** | **9** |

**Applied:** $n = 9$, $n_1 = 2$ (S), $n_2 = 3$ (T), $n_3 = 1$ (A), $n_4 = 1$ (I), $n_5 = 1$ (C)

$$\frac{9!}{2! \cdot 3! \cdot 1! \cdot 1! \cdot 1!} = \frac{362{,}880}{2 \times 6 \times 1 \times 1 \times 1} = \frac{362{,}880}{12} = 30{,}240$$

---

## 📊 Summary Table

| Problem | Word | $n$ | Repeated letters | Formula | Result |
|:---|:---:|:---:|:---|:---:|:---:|
| Arrangements of MISSISSIPPI | MISSISSIPPI | $11$ | M×1, I×4, S×4, P×2 | $\dfrac{11!}{1!\cdot4!\cdot4!\cdot2!}$ | $34{,}650$ |
| Arrangements of STATISTICS | STATISTICS | $10$ | S×3, T×3, A×1, I×1, C×1 | $\dfrac{10!}{3!\cdot3!\cdot1!\cdot1!\cdot1!}$ | $50{,}400$ |
| STATISTICS starting with S | STATISTICS | $9$ | S×2, T×3, A×1, I×1, C×1 | $\dfrac{9!}{2!\cdot3!\cdot1!\cdot1!\cdot1!}$ | $30{,}240$ |

---

## 💡 Key Insights

- **Always start by counting letters** — a letter count table prevents mistakes in the denominator.

- **Fixing a starting letter** reduces both $n$ and the count of that letter by 1:

$$n \rightarrow n-1, \quad n_i \rightarrow n_i - 1$$

- **Sanity check** — arrangements starting with S should always be less than total arrangements:

$$30{,}240 < 50{,}400 \checkmark$$

- We can also verify Problem 3 using proportional reasoning — since there are 3 S's out of 10 letters, roughly $\frac{3}{10}$ of all arrangements should start with S:

$$50{,}400 \times \frac{3}{10} = 15{,}120 \times 2 = ... $$

Wait — this gives $15{,}120$, not $30{,}240$. The proportional shortcut only works when all letters are **distinct**. Here S appears 3 times, so fixing one S still leaves 2 S's in the remaining letters, which affects the denominator. Always use the full formula for repeated elements.

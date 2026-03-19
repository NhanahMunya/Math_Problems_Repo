# Task 8 — Sequences with Repetition

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-sequences--with--repetition-orange)

---

## 🎯 Objective

Count ordered sequences where repetition is allowed, and apply the complement rule to count sequences with at least one repeated element.

---

## 📐 General Formulas

**Sequence with repetition** — ordered selection of $k$ positions from $n$ symbols, repetition allowed:

$$n^k$$

- $n$ = number of symbols available at each position
- $k$ = number of positions
- Each position independently picks from all $n$ symbols

**k-Permutation** — ordered selection of $k$ from $n$, repetition NOT allowed:

$$P(n,k) = \frac{n!}{(n-k)!}$$

> **Key distinction:** Sequences with repetition use $n^k$. When repetition is forbidden, the problem becomes a k-permutation $P(n,k)$ — and always $P(n,k) \leq n^k$.

---

## ✅ Solutions

### Problem 1 — 5-digit PIN codes, digits may repeat

**Model:** Sequence with repetition — 5 positions, each picks from $\{0,1,\ldots,9\}$, repetition allowed.

```
_ _ _ _ _
↑ ↑ ↑ ↑ ↑
10 choices each, independently
```

**Applied:** $n = 10$, $k = 5$

$$10^5 = 100{,}000$$

---

### Problem 2 — PIN codes with at least one repeated digit

**Strategy — Complement rule:**

$$\text{at least one repeated digit} = \text{total} - \text{all digits different}$$

- Total PIN codes (from Problem 1): $10^5 = 100{,}000$
- PIN codes with **all digits different** — no repetition, so this becomes a k-permutation:

$$P(10,5) = \frac{10!}{5!} = 10 \times 9 \times 8 \times 7 \times 6 = 30{,}240$$

**Applied:**

$$10^5 - P(10,5) = 100{,}000 - 30{,}240 = 69{,}760$$

---

### Problem 3 — PIN codes with all digits different

**Model:** k-Permutation — repetition is now forbidden, so each position reduces the available choices by 1.

```
_ _ _ _ _
↑ ↑ ↑ ↑ ↑
10 9 8 7 6   ← choices per position
```

**Applied:** $n = 10$, $k = 5$

$$P(10,5) = \frac{10!}{(10-5)!} = \frac{10!}{5!} = 10 \times 9 \times 8 \times 7 \times 6 = 30{,}240$$

---

## 📊 Summary Table

| Problem | Model | Formula | Result |
|:---|:---:|:---:|:---:|
| All 5-digit PINs | Sequence with repetition | $10^5$ | $100{,}000$ |
| At least one repeated digit | Complement | $10^5 - P(10,5)$ | $69{,}760$ |
| All digits different | k-Permutation | $P(10,5)$ | $30{,}240$ |

---

## ✅ Verification

Problems 2 and 3 are complements — they must sum to the total:

$$69{,}760 + 30{,}240 = 100{,}000 \checkmark$$

---

## 💡 Key Insights

- **Repetition allowed vs forbidden** — the same setup produces two different models depending on whether digits can repeat:

$$\text{repetition allowed} \rightarrow n^k \qquad \text{repetition forbidden} \rightarrow P(n,k)$$

- **Complement rule** for "at least one repeat":

$$\text{at least one repeat} = n^k - P(n,k)$$

- **Why** $P(n,k) \leq n^k$ always holds — forbidding repetition can only reduce or maintain the number of outcomes, never increase it:

$$P(n,k) = n \times (n-1) \times \cdots \times (n-k+1) \leq n \times n \times \cdots \times n = n^k$$

- **Verification trick** — Problems involving "at least one X" and "no X" always sum to the total. Use this as a built-in check.

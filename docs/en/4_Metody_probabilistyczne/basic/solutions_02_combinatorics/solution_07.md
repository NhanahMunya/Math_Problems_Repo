# Task 7 — k-Permutations (Ordered Selections Without Repetition)

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-k--permutations-orange)

---

## 🎯 Objective

Count ordered selections of $k$ objects from $n$ distinct objects without repetition, including constrained cases where a specific digit is fixed in a specific position.

---

## 📐 General Formula

**k-Permutation** — ordered selection of $k$ objects from $n$ distinct objects, no repetition:

$$P(n,k) = \frac{n!}{(n-k)!}$$

- $n$ = total number of distinct objects
- $k$ = how many are being selected
- $(n-k)!$ = cancels the unselected objects from $n!$
- No $k!$ in the denominator because order **does** matter

> **Key relationship to combination:**
> $$P(n,k) = \binom{n}{k} \times k!$$
> A k-Permutation is a Combination multiplied by $k!$ — the only difference is whether order matters.

---

## ✅ Solutions

### Problem 1 — First three places among 12 runners

**Model:** k-Permutation — choosing 3 from 12, order matters (1st ≠ 2nd ≠ 3rd), no repetition.

**Applied:** $n = 12$, $k = 3$

$$P(12,3) = \frac{12!}{(12-3)!} = \frac{12!}{9!} = 12 \times 11 \times 10 = 1{,}320$$

---

### Problem 2 — 4-digit numbers with distinct digits from 1–9

**Model:** k-Permutation — forming an ordered 4-digit number from digits $\{1,2,\ldots,9\}$, no repetition.

Each different arrangement of digits produces a different number, so order matters:

```
_ _ _ _
↑ ↑ ↑ ↑
choose 4 distinct digits from {1,...,9} in order
```

**Applied:** $n = 9$, $k = 4$

$$P(9,4) = \frac{9!}{(9-4)!} = \frac{9!}{5!} = 9 \times 8 \times 7 \times 6 = 3{,}024$$

---

### Problem 3 — 4-digit numbers from 1–9 with distinct digits, divisible by 5

**Strategy — Fix last digit, arrange the rest:**

A number is divisible by 5 if and only if its **last digit is 0 or 5**. Since our digits are from $\{1,\ldots,9\}$, the only option is **last digit = 5**.

Fix 5 in the last position, then fill the remaining 3 positions with distinct digits chosen from the remaining 8 digits $\{1,2,3,4,6,7,8,9\}$:

```
_ _ _ [ 5 ]
↑ ↑ ↑  fixed
choose 3 distinct digits from remaining 8, in order
```

**Applied:** $n = 8$, $k = 3$ for the free positions

$$P(8,3) = \frac{8!}{(8-3)!} = \frac{8!}{5!} = 8 \times 7 \times 6 = 336$$

> **Sanity check:** Numbers divisible by 5 ($336$) must be fewer than all 4-digit numbers with distinct digits ($3{,}024$): $336 < 3{,}024$ ✓

---

## 📊 Summary Table

| Problem | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| First 3 places among 12 runners | Direct k-permutation | $P(12,3)$ | $1{,}320$ |
| 4-digit numbers, distinct digits from 1–9 | Direct k-permutation | $P(9,4)$ | $3{,}024$ |
| Divisible by 5, distinct digits from 1–9 | Fix last digit, arrange rest | $P(8,3)$ | $336$ |

---

## 💡 Key Insights

- **k-Permutation vs Combination** — both select some objects, but k-Permutation cares about order:

$$P(n,k) = \binom{n}{k} \times k!$$

- **Fixing a digit position** — when a digit is constrained to a specific position, fix it and apply k-permutation to the remaining positions and digits:

$$\text{fix 1 position} \rightarrow P(n-1,\ k-1)$$

- **Divisibility by 5** — always requires the last digit to be 0 or 5. Since 0 is not in $\{1,\ldots,9\}$, only 5 qualifies here. If 0 were available, there would be two cases to add together:

$$P(\text{ends in 0}) + P(\text{ends in 5})$$

- **Expanding the last digit** — the same "fix last digit" strategy applies to any divisibility condition that restricts the final digit (e.g. even numbers require last digit $\in \{2,4,6,8\}$).

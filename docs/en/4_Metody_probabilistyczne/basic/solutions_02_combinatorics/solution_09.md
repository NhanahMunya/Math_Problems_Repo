# Task 9 — Digit Restrictions

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-product--rule--and--complement-orange)

---

## 🎯 Objective

Count 5-digit numbers satisfying specific digit restrictions, carefully accounting for the fact that the leading digit cannot be zero.

---

## 📐 Key Distinction: Numbers vs PIN Codes

| Property | 5-digit number | 5-digit PIN code |
|:---|:---:|:---:|
| First digit can be 0? | ❌ No | ✅ Yes |
| Example | $10000$ to $99999$ | $00000$ to $99999$ |
| Total count | $9 \times 10^4$ | $10^5$ |

> A 5-digit number must have a non-zero leading digit — otherwise it would be a 4-digit number or fewer.

---

## ✅ Solutions

### Problem 1 — How many 5-digit numbers exist?

**Strategy — Product rule with leading digit restriction:**

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  9    10    10    10    10
(1-9) (0-9) (0-9) (0-9) (0-9)
```

- First digit: 9 choices $\{1,2,\ldots,9\}$ — zero excluded
- Each remaining digit: 10 choices $\{0,1,\ldots,9\}$ — repetition allowed

**Applied:** 

$$9 \times 10^4 = 9 \times 10{,}000 = 90{,}000$$

---

### Problem 2 — How many 5-digit numbers are even?

**Strategy — Fix last digit, apply product rule:**

A number is even if and only if its **last digit is even**: $\{0, 2, 4, 6, 8\}$ → 5 choices.

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  9    10    10    10     5
(1-9) (0-9) (0-9) (0-9) (even)
```

- First digit: 9 choices (no zero)
- Middle 3 digits: 10 choices each
- Last digit: 5 choices (even digits only)

**Applied:**

$$9 \times 10^3 \times 5 = 9 \times 1{,}000 \times 5 = 45{,}000$$

> **Sanity check:** Even numbers should be exactly half of all 5-digit numbers: $\frac{90{,}000}{2} = 45{,}000$ ✓

---

### Problem 3 — How many 5-digit numbers contain no repeated digits?

**Strategy — Product rule with decreasing choices:**

No digit may appear more than once. The leading digit restriction interacts carefully here:

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  9     9     8     7     6
(1-9)(0-9  (8 re- (7 re- (6 re-
      minus  main)  main)  main)
      first)
```

- First digit: 9 choices $\{1,\ldots,9\}$ — zero excluded
- Second digit: 9 choices — anything except the first digit (zero is now allowed back)
- Third digit: 8 choices — anything except the two already used
- Fourth digit: 7 choices
- Fifth digit: 6 choices

**Applied:**

$$9 \times 9 \times 8 \times 7 \times 6 = 27{,}216$$

> **Why not $P(10,5) = 30{,}240$?** That would allow 0 as the first digit, producing invalid numbers like $01234$. The leading digit restriction breaks the symmetry, so we cannot use a single k-permutation formula directly.

---

### Problem 4 — How many 5-digit numbers contain at least one repeated digit?

**Strategy — Complement rule:**

$$\text{at least one repeated digit} = \text{total} - \text{no repeated digits}$$

**Applied:**

$$9 \times 10^4 - 9 \times 9 \times 8 \times 7 \times 6 = 90{,}000 - 27{,}216 = 62{,}784$$

---

## 📊 Summary Table

| Problem | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| All 5-digit numbers | Product rule | $9 \times 10^4$ | $90{,}000$ |
| Even 5-digit numbers | Fix last digit | $9 \times 10^3 \times 5$ | $45{,}000$ |
| No repeated digits | Decreasing choices | $9 \times 9 \times 8 \times 7 \times 6$ | $27{,}216$ |
| At least one repeated digit | Complement | $9 \times 10^4 - 9 \times 9 \times 8 \times 7 \times 6$ | $62{,}784$ |

---

## ✅ Verification

Problems 3 and 4 are complements — they must sum to the total:

$$27{,}216 + 62{,}784 = 90{,}000 \checkmark$$

---

## 💡 Key Insights

- **Leading digit restriction** is the key difference between 5-digit numbers and 5-digit PIN codes:

$$\text{PIN codes: } 10^5 = 100{,}000 \qquad \text{5-digit numbers: } 9 \times 10^4 = 90{,}000$$

- **Even numbers** — fix the last digit to even values $\{0,2,4,6,8\}$, giving exactly half of all numbers:

$$\frac{9 \times 10^4}{2} = 45{,}000$$

- **No repeated digits with leading restriction** — the second digit gets 9 choices (not 8) because zero becomes available again after being excluded from the first position:

$$9 \times 9 \times 8 \times 7 \times 6 \neq P(10,5)$$

- **Complement rule** for "at least one repeat":

$$\text{at least one repeat} = \text{total} - \text{all different}$$

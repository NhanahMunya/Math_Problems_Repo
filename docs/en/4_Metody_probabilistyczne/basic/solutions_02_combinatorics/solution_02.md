# Task 2 — Permutations

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-permutations-orange)

---

## 🎯 Objective

Apply permutation counting to arrangement problems, including constrained cases using the block trick and the complement rule.

---

## 📐 General Formula

**Permutation** — arranging $n$ distinct objects in a line:

$$P_n = n!$$

- $n$ = total number of distinct objects
- All objects are used, order matters, no repetition allowed
- Each position reduces choices by 1: $n \times (n-1) \times (n-2) \times \cdots \times 1$

---

## ✅ Solutions

### Problem 1 — 8 different books arranged on a shelf

**Model:** Permutation — all 8 books, order matters, all distinct.

**Applied:** $n = 8$

$$P_8 = 8! = 8 \times 7 \times 6 \times 5 \times 4 \times 3 \times 2 \times 1 = 40{,}320$$

---

### Problem 2 — 8 people in a row, two particular people must sit next to each other

**Model:** Permutation with a block constraint.

**Strategy — Block Trick:**
Treat the two people who must sit together as a **single block**. This reduces the problem to arranging 7 units:

```
[ A B ] P3 P4 P5 P6 P7 P8   ← 7 units total
```

- Arrange 7 units: $7!$ ways
- Within the block, A and B can swap positions: $2!$ ways

**Applied:** $n = 8$, block of $2$

$$P = 7! \times 2! = 5{,}040 \times 2 = 10{,}080$$

---

### Problem 3 — 8 people in a row, two particular people must NOT sit next to each other

**Model:** Permutation with complement rule.

**Strategy — Complement:**

$$\text{arrangements where they are NOT together} = \text{total} - \text{arrangements where they ARE together}$$

- Total arrangements of 8 people: $8!$
- Arrangements where they **are** together (from Problem 2): $7! \times 2!$

**Applied:** $n = 8$

$$P = 8! - 7! \times 2! = 40{,}320 - 10{,}080 = 30{,}240$$

---

### Problem 4 — 10 questions in a test, first question is fixed

**Model:** Permutation with one position fixed.

**Strategy — Fix and arrange:**
Since question 1 is fixed in position 1, only the remaining 9 questions are freely arranged:

```
[ Q1 ] _ _ _ _ _ _ _ _ _
 fixed   ← 9 free positions →
```

**Applied:** $n = 10$, 1 fixed, $n - 1 = 9$ free

$$P = 9! = 9 \times 8 \times 7 \times 6 \times 5 \times 4 \times 3 \times 2 \times 1 = 362{,}880$$

---

## 📊 Summary Table

| Problem | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| 8 books on a shelf | Direct permutation | $8!$ | $40{,}320$ |
| 2 people must be together | Block trick | $7! \times 2!$ | $10{,}080$ |
| 2 people must NOT be together | Complement | $8! - 7! \times 2!$ | $30{,}240$ |
| First question fixed | Fix and arrange | $9!$ | $362{,}880$ |

---

## 💡 Key Insights

- **Block trick** — when objects must stay together, treat them as one unit, reducing $n$ by the block size minus 1. Multiply by the internal arrangements of the block:

$$P = (n - k + 1)! \times k!$$

where $k$ is the size of the block. For $k = 2$: $(n-1)! \times 2!$

- **Complement rule** — "must NOT" problems are easier solved by subtracting the unwanted case from the total:

$$P(\text{not together}) = n! - (n-1)! \times 2!$$

- **Fixing a position** reduces the free arrangements from $n!$ to $(n-1)!$ — one position is no longer a choice.

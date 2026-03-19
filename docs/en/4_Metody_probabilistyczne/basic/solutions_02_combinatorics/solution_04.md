# Task 4 — Circular Permutations

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-circular--permutations-orange)

---

## 🎯 Objective

Count distinct circular arrangements of people around a round table, including constrained cases where two particular people must sit next to each other or opposite each other.

---

## 📐 General Formula

**Circular permutation** — arranging $n$ distinct objects around a circle:

$$(n-1)!$$

- $n$ = total number of distinct objects
- We subtract 1 because one person is **fixed** to eliminate identical rotations
- Relationship to linear permutation:

$$\frac{n!}{n} = (n-1)!$$

> **Why $(n-1)!$?** In a circle, rotating everyone one seat produces the same arrangement. There are exactly $n$ such rotations of any linear arrangement, so we divide $n!$ by $n$.

---

## ✅ Solutions

### Problem 1 — 7 people around a round table

**Model:** Circular permutation — all 7 people, circular arrangement, all distinct.

**Applied:** $n = 7$

$$(7-1)! = 6! = 720$$

---

### Problem 2 — 7 people, two particular people must sit next to each other

**Model:** Circular permutation with block trick.

**Strategy:**
Treat the two people (call them A and B) as a **single block**. This gives 6 units to arrange in a circle:

```
  [ A B ]
 /        \
P7        P3
|          |
P6        P4
 \        /
    P5
```

- Arrange 6 units in a circle: $(6-1)! = 5!$ ways
- Within the block, A and B can swap: $2!$ ways

**Applied:** $n = 7$, block of $2$

$$P = 5! \times 2! = 120 \times 2 = 240$$

---

### Problem 3 — 7 people, two particular people must sit opposite each other

**Important note:** A circle with 7 people has no exact "opposite" seat — 7 is **odd**, so there is no seat directly across with an equal number of people on each side.

In this problem we interpret "opposite" as having **3 people between them** on each side:

```
        A
      /   \
    P7     P3
    |       |
    P6     P4
      \   /
        B
   (3 people on each side)
```

**Strategy:**
- **Fix person A** in one seat — standard circular fix eliminates rotations
- **Place person B** in the one specific seat opposite A (3 seats away) → $1$ choice
- **Arrange remaining 5 people** freely in the remaining seats → $5!$ ways

**Applied:** $n = 7$, A fixed, B has 1 choice, 5 free

$$P = 1 \times 1 \times 5! = 5! = 120$$

---

## 📊 Summary Table

| Problem | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| 7 people at round table | Direct circular permutation | $(7-1)!$ | $720$ |
| 2 people must be together | Block trick in circle | $5! \times 2!$ | $240$ |
| 2 people must be opposite | Fix A, place B opposite, arrange rest | $5!$ | $120$ |

---

## 💡 Key Insights

- **Circular vs linear** — always divide out $n$ rotations:

$$\text{Circular}(n) = \frac{\text{Linear}(n)}{n} = \frac{n!}{n} = (n-1)!$$

- **Block trick in a circle** — treat $k$ people who must sit together as one unit, reducing $n$ to $n-k+1$ units in a circle, then multiply by internal arrangements:

$$P = (n-k)! \times k!$$

For $k=2$: $P = (n-2)! \times 2!$

- **Fixing two people** — when two people have fixed relative positions (e.g. opposite), fix one person to eliminate rotations, place the second in their constrained seat, then arrange the rest:

$$P = 1 \times 1 \times (n-2)!$$

- **Odd vs even circles** — "opposite" only has a clean geometric meaning for **even** $n$. For odd $n$, always clarify what "opposite" means in the context of the problem.

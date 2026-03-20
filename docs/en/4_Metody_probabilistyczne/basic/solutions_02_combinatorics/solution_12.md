# Task 12 — Mixed Counting Problem

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-mixed--models-orange)

---

## 🎯 Objective

Apply all counting models from this task list to solve a mixed problem involving student ID codes, medal assignments, committee selections, circular seating, and passwords.

---

## ✅ Sub-problem 1 — Student ID Codes

Each identifier consists of:
- **2 letters** from $\{A, B, C, D, E\}$ — 5 options
- **3 digits** from $\{0, 1, \ldots, 9\}$ — 10 options

---

### Part 1 — Letters and digits may repeat

**Model:** Sequence with repetition for both parts — each position picks freely.

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  5     5    10    10    10
 (letters)    (digits)
```

**Applied:**

$$5^2 \times 10^3 = 25 \times 1{,}000 = 25{,}000$$

---

### Part 2 — Letters may not repeat, digits may repeat

**Model:** k-Permutation for letters, sequence with repetition for digits.

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  5     4    10    10    10
(no repeat)   (repeat allowed)
```

**Applied:** $P(5,2) \times 10^3$

$$P(5,2) \times 10^3 = (5 \times 4) \times 1{,}000 = 20 \times 1{,}000 = 20{,}000$$

---

### Part 3 — Neither letters nor digits may repeat

**Model:** k-Permutation for both parts.

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  5     4    10     9     8
(no repeat)  (no repeat)
```

**Applied:** $P(5,2) \times P(10,3)$

$$P(5,2) \times P(10,3) = (5 \times 4) \times (10 \times 9 \times 8) = 20 \times 720 = 14{,}400$$

---

### Summary — Student ID Codes

| Restriction | Model | Formula | Result |
|:---|:---:|:---:|:---:|
| Letters and digits repeat | Sequence × Sequence | $5^2 \times 10^3$ | $25{,}000$ |
| Letters no repeat, digits repeat | k-Perm × Sequence | $P(5,2) \times 10^3$ | $20{,}000$ |
| Neither repeats | k-Perm × k-Perm | $P(5,2) \times P(10,3)$ | $14{,}400$ |

> **Sanity check:** Adding restrictions always reduces the count: $25{,}000 > 20{,}000 > 14{,}400$ ✓

---

## ✅ Sub-problem 2 — Medal Assignment

12 runners, medals for gold, silver, and bronze.

---

### Part 1 — Medals assigned freely

**Model:** k-Permutation — choosing 3 from 12, order matters (gold ≠ silver ≠ bronze).

**Applied:** $n = 12$, $k = 3$

$$P(12,3) = 12 \times 11 \times 10 = 1{,}320$$

---

### Part 2 — Two particular runners must both receive medals

Call the two particular runners A and B. Both must appear on the podium — their positions among gold, silver, bronze must be assigned, along with one more runner for the remaining medal.

**Step 1:** Assign medal positions to A and B — choose 2 of the 3 medal positions and arrange A and B in them:

$$P(3,2) = 3 \times 2 = 6 \text{ ways}$$

**Step 2:** Assign the remaining medal to any of the other 10 runners:

$$10 \text{ choices}$$

**Applied:**

$$P(3,2) \times 10 = 6 \times 10 = 60$$

> **Sanity check:** $60 < 1{,}320$ ✓

---

## ✅ Sub-problem 3 — Committee Selection

10 students: **6 men** and **4 women**. Choose a committee of 4.

---

### Part 1 — All possible committees

**Model:** Combination — choosing 4 from 10, order does not matter.

**Applied:** $n = 10$, $k = 4$

$$\binom{10}{4} = \frac{10!}{4! \cdot 6!} = \frac{10 \times 9 \times 8 \times 7}{4 \times 3 \times 2 \times 1} = \frac{5{,}040}{24} = 210$$

---

### Part 2 — Exactly two women

**Strategy — Product rule:**

- Choose 2 women from 4: $\binom{4}{2}$
- Choose 2 men from 6: $\binom{6}{2}$

**Applied:**

$$\binom{4}{2} \times \binom{6}{2} = 6 \times 15 = 90$$

---

### Part 3 — At least one woman

**Strategy — Complement rule:**

$$\text{at least one woman} = \text{total} - \text{no women}$$

Committees with **no women** — choose all 4 from 6 men:

$$\binom{6}{4} = \frac{6!}{4! \cdot 2!} = 15$$

**Applied:**

$$\binom{10}{4} - \binom{6}{4} = 210 - 15 = 195$$

---

### Summary — Committee Selection

| Restriction | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| Any committee | Direct combination | $\binom{10}{4}$ | $210$ |
| Exactly 2 women | Product rule | $\binom{4}{2} \times \binom{6}{2}$ | $90$ |
| At least 1 woman | Complement | $\binom{10}{4} - \binom{6}{4}$ | $195$ |

> **Sanity check:** $90 < 195 < 210$ ✓

---

## ✅ Sub-problem 4 — Circular Seating

7 people around a round table.

---

### Part 1 — All seating arrangements

**Model:** Circular permutation — fix one person, arrange remaining 6.

**Applied:** $n = 7$

$$(7-1)! = 6! = 720$$

---

### Part 2 — Two particular people sit next to each other

**Strategy — Block trick in a circle:**

Treat the two people (A and B) as one block → 6 units in a circle:

```
  [ A B ]
 /        \
P7        P3
|          |
P6        P4
 \        /
    P5
```

- Arrange 6 units in a circle: $(6-1)! = 5!$
- A and B swap within block: $2!$

**Applied:**

$$5! \times 2! = 120 \times 2 = 240$$

---

### Summary — Circular Seating

| Restriction | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| All arrangements | Circular permutation | $(7-1)!$ | $720$ |
| Two must sit together | Block trick | $5! \times 2!$ | $240$ |

---

## ✅ Sub-problem 5 — Passwords

5 characters from digits $\{0,\ldots,9\}$ and letters $\{A,\ldots,Z\}$.

Total symbols: $10 + 26 = 36$

---

### Part 1 — Repetition allowed

**Model:** Sequence with repetition — each of 5 positions picks freely from 36 symbols.

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  36   36    36    36    36
```

**Applied:** $n = 36$, $k = 5$

$$36^5 = 60{,}466{,}176$$

---

### Part 2 — No character may repeat

**Model:** k-Permutation — choosing 5 from 36, order matters, no repetition.

```
[ _ ] [ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑     ↑
  36   35    34    33    32
```

**Applied:** $n = 36$, $k = 5$

$$P(36,5) = 36 \times 35 \times 34 \times 33 \times 32 = 45{,}239{,}040$$

---

### Part 3 — Counting model used in each case

| Case | Model | Why |
|:---|:---:|:---|
| Repetition allowed | Sequence with repetition $n^k$ | Each position independently picks from all 36 symbols |
| No repetition | k-Permutation $P(n,k)$ | Each position reduces available symbols by 1 |

> **Sanity check:** $45{,}239{,}040 < 60{,}466{,}176$ ✓ — forbidding repetition always reduces the count.

---

## 📊 Final Summary Table

| Sub-problem | Model | Formula | Result |
|:---|:---:|:---:|:---:|
| ID: both repeat | Sequence × Sequence | $5^2 \times 10^3$ | $25{,}000$ |
| ID: letters no repeat | k-Perm × Sequence | $P(5,2) \times 10^3$ | $20{,}000$ |
| ID: neither repeats | k-Perm × k-Perm | $P(5,2) \times P(10,3)$ | $14{,}400$ |
| Medals: free | k-Permutation | $P(12,3)$ | $1{,}320$ |
| Medals: A and B must medal | Fix positions + fill | $P(3,2) \times 10$ | $60$ |
| Committee: any | Combination | $\binom{10}{4}$ | $210$ |
| Committee: exactly 2 women | Product rule | $\binom{4}{2} \times \binom{6}{2}$ | $90$ |
| Committee: at least 1 woman | Complement | $\binom{10}{4} - \binom{6}{4}$ | $195$ |
| Circular: any | Circular permutation | $(7-1)!$ | $720$ |
| Circular: 2 together | Block trick | $5! \times 2!$ | $240$ |
| Password: repeat allowed | Sequence with repetition | $36^5$ | $60{,}466{,}176$ |
| Password: no repeat | k-Permutation | $P(36,5)$ | $45{,}239{,}040$ |

---

## 💡 Key Insights

- **Product rule** connects independent parts of a single outcome — multiply counts when two choices happen simultaneously.
- **Complement rule** is always the cleanest approach for "at least one" problems.
- **Block trick** works for both linear and circular arrangements — reduce $n$ by block size minus 1, multiply by internal arrangements.
- **Repetition allowed vs forbidden** — same setup, different rule:

$$\text{repetition allowed} \rightarrow n^k \qquad \text{repetition forbidden} \rightarrow P(n,k)$$

# Problem 2 — Die × Die

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-discovering--formalism-blue)
![Method](https://img.shields.io/badge/method-sample--space--and--events-orange)

---

## 🎯 Objective

Analyse the sample space of two dice rolls using a 6×6 graphical grid. Mark events as subsets of the sample space and interpret graphically represented events as precise verbal statements, with full reasoning for each step.

---

## 📐 Sample Space

The experiment consists of two independent rolls of a fair six-sided die. Each roll produces a result in $\{1,2,3,4,5,6\}$. Since order matters — the first and second roll are distinct stages — each elementary outcome is an ordered pair $(i,j)$ where $i$ is the result of the first die and $j$ is the result of the second die.

The full sample space is:

$$\Omega = \{(i,j) \mid i,j \in \{1,2,3,4,5,6\}\}, \quad |\Omega| = 36$$

In the grid representation, **rows correspond to the first die** and **columns correspond to the second die**:

```
      1 2 3 4 5 6    ← second die
1     . . . . . .
2     . . . . . .
3     . . . . . .
4     . . . . . .
5     . . . . . .
6     . . . . . .
↑
first die
```

An **event** is any subset of $\Omega$. Marking a cell `X` means that outcome belongs to the event; `.` means it does not.

---

## ✅ Part A — Marking Events

---

### Statement 1 — The sum is equal to 8

**Reasoning:** We need all pairs $(i,j)$ such that $i + j = 8$, where $i,j \in \{1,...,6\}$. We systematically find all such pairs:

| First die $i$ | Second die $j = 8 - i$ | Valid? |
|:---:|:---:|:---:|
| 1 | 7 | ❌ — 7 is not a valid die face |
| 2 | 6 | ✅ |
| 3 | 5 | ✅ |
| 4 | 4 | ✅ |
| 5 | 3 | ✅ |
| 6 | 2 | ✅ |

The event contains 5 outcomes, forming a **diagonal stripe** in the upper-right region of the grid:

```
      1 2 3 4 5 6
1     . . . . . .
2     . . . . . X
3     . . . . X .
4     . . . X . .
5     . . X . . .
6     . X . . . .
```

The event is $A = \{(2,6),(3,5),(4,4),(5,3),(6,2)\}$.

> **Geometric observation:** Constant-sum events always form diagonal stripes running from lower-left to upper-right. The sum 8 stripe lies above the main diagonal, reflecting that 8 is greater than the average sum of 7.

---

### Statement 2 — The first die is greater than the second

**Reasoning:** We need all pairs $(i,j)$ where $i > j$. These are outcomes lying **strictly below the main diagonal** of the grid (where the main diagonal contains all pairs with $i = j$).

For each row $i$, the valid columns $j$ satisfy $j < i$:

- Row 1: no valid $j$ (nothing is less than 1)
- Row 2: $j = 1$
- Row 3: $j = 1, 2$
- Row 4: $j = 1, 2, 3$
- Row 5: $j = 1, 2, 3, 4$
- Row 6: $j = 1, 2, 3, 4, 5$

```
      1 2 3 4 5 6
1     . . . . . .
2     X . . . . .
3     X X . . . .
4     X X X . . .
5     X X X X . .
6     X X X X X .
```

The event contains $0+1+2+3+4+5 = 15$ outcomes — the **lower triangle** of the grid.

> **Geometric observation:** The 36 outcomes split into three regions: the lower triangle ($i > j$, 15 outcomes), the main diagonal ($i = j$, 6 outcomes), and the upper triangle ($i < j$, 15 outcomes). By symmetry, the lower and upper triangles are equal in size.

---

### Statement 3 — Both dice show even numbers

**Reasoning:** We need all pairs $(i,j)$ where both $i$ and $j$ are even. The even faces are $\{2,4,6\}$. The event is satisfied only when both the row and the column belong to $\{2,4,6\}$:

- Valid rows: 2, 4, 6
- Valid columns: 2, 4, 6

This produces a **3×3 sub-grid** at the intersections of even rows and even columns:

```
      1 2 3 4 5 6
1     . . . . . .
2     . X . X . X
3     . . . . . .
4     . X . X . X
5     . . . . . .
6     . X . X . X
```

The event contains $3 \times 3 = 9$ outcomes.

> **Geometric observation:** Restricting both coordinates to a subset of size $k$ produces a $k \times k$ sub-grid. Here $k = 3$ even values out of 6, so the sub-grid occupies $\frac{3}{6} \times \frac{3}{6} = \frac{1}{4}$ of the full grid — consistent with $P = \frac{9}{36} = \frac{1}{4}$.

---

### Statement 4 — At least one die shows 6

**Reasoning:** "At least one die shows 6" means the first die shows 6, or the second die shows 6, or both show 6. We identify the three sub-cases:

- **First die shows 6:** entire row 6 — outcomes $(6,1),(6,2),(6,3),(6,4),(6,5),(6,6)$
- **Second die shows 6:** entire column 6 — outcomes $(1,6),(2,6),(3,6),(4,6),(5,6),(6,6)$
- **Both show 6:** $(6,6)$ — counted in both row and column

By the union formula: $|A \cup B| = |A| + |B| - |A \cap B| = 6 + 6 - 1 = 11$ outcomes.

```
      1 2 3 4 5 6
1     . . . . . X
2     . . . . . X
3     . . . . . X
4     . . . . . X
5     . . . . . X
6     X X X X X X
```

> **Geometric observation:** The event forms an **L-shape** — the union of the bottom row and the rightmost column. The corner $(6,6)$ belongs to both and is counted once. This L-shape is why the count is $6 + 6 - 1 = 11$, not 12.

---

### Statement 5 — Exactly one die shows 1

**Reasoning:** "Exactly one die shows 1" means the first die shows 1 and the second does not, or the second die shows 1 and the first does not. We must explicitly exclude $(1,1)$:

- **First die shows 1, second does not:** row 1, columns $\{2,3,4,5,6\}$ — 5 outcomes
- **Second die shows 1, first does not:** column 1, rows $\{2,3,4,5,6\}$ — 5 outcomes
- **Both show 1:** $(1,1)$ — excluded from both cases

Total: $5 + 5 = 10$ outcomes.

```
      1 2 3 4 5 6
1     . X X X X X
2     X . . . . .
3     X . . . . .
4     X . . . . .
5     X . . . . .
6     X . . . . .
```

> **Geometric observation:** This event is the union of row 1 and column 1, **minus** the corner $(1,1)$ where both dice show 1. Removing the corner is what distinguishes "exactly one" from "at least one."

---

## ✅ Part B — Interpreting Graphical Events

---

### Case 1

```
      1 2 3 4 5 6
1     . . . . . .
2     . . . . . .
3     . . X X X X
4     . . X X X X
5     . . X X X X
6     . . X X X X
```

**Interpretation:** The marked region forms a **4×4 block** in the lower-right corner of the grid. The marked rows are $\{3,4,5,6\}$ — that is, first die results of at least 3. The marked columns are $\{3,4,5,6\}$ — that is, second die results of at least 3.

An outcome $(i,j)$ is marked if and only if **both** $i \geq 3$ **and** $j \geq 3$.

> **Event: both dice show a number greater than or equal to 3** (i.e. both dice show at least 3).

The event contains $4 \times 4 = 16$ outcomes. Unmarked rows $\{1,2\}$ and unmarked columns $\{1,2\}$ represent outcomes where at least one die shows 1 or 2.

---

### Case 2

```
      1 2 3 4 5 6
1     X . . . . .
2     . X . . . .
3     . . X . . .
4     . . . X . .
5     . . . . X .
6     . . . . . X
```

**Interpretation:** The marked cells are exactly $(1,1),(2,2),(3,3),(4,4),(5,5),(6,6)$ — the **main diagonal** of the grid. An outcome $(i,j)$ is marked if and only if $i = j$.

> **Event: both dice show the same number.**

The event contains 6 outcomes — one for each possible repeated value. This is the same diagonal structure observed in Problem 1 (both coin tosses the same), now extended to a $6 \times 6$ grid.

---

## 💡 Key Insights

- **Rows encode the first die, columns encode the second die.** Constraints on only the first die fill entire rows; constraints on only the second die fill entire columns; constraints on both produce rectangular sub-grids or more complex shapes.

- **Geometric structure reveals mathematical structure:**
  - Constant-sum events → diagonal stripes
  - Inequality events ($i > j$) → triangular regions
  - Both-even events → sub-grids at even intersections
  - At-least-one events → L-shapes (union of row and column)
  - Exactly-one events → L-shapes minus the corner

- **"At least one" vs "exactly one":** both produce L-shaped regions, but "exactly one" excludes the corner where both dice satisfy the condition. This is the geometric counterpart of the set-theoretic difference between $A \cup B$ and $(A \setminus B) \cup (B \setminus A)$.

- **Complement simplifies counting:** for "at least one die shows 6," we can count directly (11 outcomes) or note the complement is "neither die shows 6" (a 5×5 sub-grid of 25 outcomes), giving $36 - 25 = 11$ — the same result.

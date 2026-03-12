# Task 2 — Rolling a Die

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-sample--spaces-blue)
![Method](https://img.shields.io/badge/method-tree--diagram-orange)

---

## 🎯 Objective

Construct the sample spaces for one, two, and three rolls of a fair six-sided die, and identify what an elementary outcome represents in each case.

---

## 📐 Setup

A **fair six-sided die** has six possible results per roll:

$$
\{1,\ 2,\ 3,\ 4,\ 5,\ 6\}
$$

The **order of outcomes matters** — each roll is a separate stage of the experiment.

---

## 🌳 Tree Diagram (Partial — Two Rolls)

A full tree for three rolls would contain $6^3 = 216$ leaves and is impractical to draw. Below is a **partial tree for two rolls**, showing only the branches starting from outcome $1$ and $2$ to illustrate the structure.

```
START
 │
 ├── 1 ──┬── 1  → (1, 1)
 │       ├── 2  → (1, 2)
 │       ├── 3  → (1, 3)
 │       ├── 4  → (1, 4)
 │       ├── 5  → (1, 5)
 │       └── 6  → (1, 6)
 │
 ├── 2 ──┬── 1  → (2, 1)
 │       ├── 2  → (2, 2)
 │       ├── 3  → (2, 3)
 │       ├── 4  → (2, 4)
 │       ├── 5  → (2, 5)
 │       └── 6  → (2, 6)
 │
 ├── 3 ── (6 branches, same pattern)
 ├── 4 ── (6 branches, same pattern)
 ├── 5 ── (6 branches, same pattern)
 └── 6 ── (6 branches, same pattern)
```

> Each of the 6 first-roll outcomes branches into 6 second-roll outcomes, giving $6 \times 6 = 36$ paths total.

---

## ✅ Solutions

### 1. Sample Space for One Roll — $\Omega_1$

$$
\Omega_1 = \{\ 1,\ 2,\ 3,\ 4,\ 5,\ 6\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_1| = 6
$$

---

### 2. Sample Space for Two Rolls — $\Omega_2$

Each elementary outcome is an **ordered pair** $(i,\ j)$ where $i, j \in \{1,2,3,4,5,6\}$:

$$
\Omega_2 = \{\ (i,\ j) \mid i, j \in \{1, 2, 3, 4, 5, 6\}\ \}
$$

Written out fully:

$$
\Omega_2 = \{(1,1),\ (1,2),\ \ldots,\ (1,6),\ (2,1),\ \ldots,\ (6,5),\ (6,6)\}
$$

**Number of elementary outcomes:**

$$
|\Omega_2| = 6 \times 6 = 36
$$

---

### 3. Sample Space for Three Rolls — $\Omega_3$

Each elementary outcome is an **ordered triple** $(i,\ j,\ k)$ where $i, j, k \in \{1,2,3,4,5,6\}$:

$$
\Omega_3 = \{\ (i,\ j,\ k) \mid i, j, k \in \{1, 2, 3, 4, 5, 6\}\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_3| = 6 \times 6 \times 6 = 216
$$

---

### 4. General Formula

For $n$ rolls of a fair six-sided die, the number of elementary outcomes is:

$$
|\Omega_n| = 6^n
$$

| Experiment | Sample Space Size |
|:---:|:---:|
| $\Omega_1$ (1 roll) | $6^1 = 6$ |
| $\Omega_2$ (2 rolls) | $6^2 = 36$ |
| $\Omega_3$ (3 rolls) | $6^3 = 216$ |

---

### 5. What Does an Elementary Outcome Represent?

| Sample Space | Elementary Outcome | Meaning |
|:---:|:---:|:---|
| $\Omega_1$ | $i$ where $i \in \{1,\ldots,6\}$ | The single number shown on the die after one roll |
| $\Omega_2$ | $(i,\ j)$ where $i, j \in \{1,\ldots,6\}$ | An ordered pair recording the result of roll 1 and roll 2 |
| $\Omega_3$ | $(i,\ j,\ k)$ where $i, j, k \in \{1,\ldots,6\}$ | An ordered triple recording the result of each of the three rolls in sequence |

> **Note:** The order matters — the outcome $(2, 5)$ is different from $(5, 2)$, because the first and second rolls gave different results in each case.

---

## 💡 Key Insight

Each additional roll **multiplies** the number of elementary outcomes by $6$, because each existing outcome branches into 6 new ones. This gives the exponential growth pattern $6^n$.

Comparing with Task 1:

$$
\text{Coin (2 outcomes per trial):} \quad |\Omega_n| = 2^n
$$

$$
\text{Die (6 outcomes per trial):} \quad |\Omega_n| = 6^n
$$

In general, if each trial has $k$ equally likely outcomes, then $n$ independent trials produce:

$$
|\Omega_n| = k^n \text{ elementary outcomes}
$$

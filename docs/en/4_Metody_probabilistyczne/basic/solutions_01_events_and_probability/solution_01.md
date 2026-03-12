# Task 1 — Coin Tossing

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-sample--spaces-blue)
![Method](https://img.shields.io/badge/method-tree--diagram-orange)

---

## 🎯 Objective

Construct the sample spaces for one, two, and three tosses of a fair coin, and identify what an elementary outcome represents in each case.

---

## 📐 Setup

A **fair coin** has two possible results per toss:

- **H** — Heads
- **T** — Tails

The **order of outcomes matters** — each toss is a separate stage of the experiment.

---

## 🌳 Tree Diagrams

### One Toss

```
START
 │
 ├── H
 └── T
```

### Two Tosses

```
START
 │
 ├── H ──┬── H  → (H, H)
 │       └── T  → (H, T)
 │
 └── T ──┬── H  → (T, H)
         └── T  → (T, T)
```

### Three Tosses

```
START
 │
 ├── H ──┬── H ──┬── H  → (H, H, H)
 │       │       └── T  → (H, H, T)
 │       └── T ──┬── H  → (H, T, H)
 │               └── T  → (H, T, T)
 │
 └── T ──┬── H ──┬── H  → (T, H, H)
         │       └── T  → (T, H, T)
         └── T ──┬── H  → (T, T, H)
                 └── T  → (T, T, T)
```

---

## ✅ Solutions

### 1. Sample Space for One Toss — $\Omega_1$

$$
\Omega_1 = \{ H,\ T \}
$$

**Number of elementary outcomes:**

$$
|\Omega_1| = 2
$$

---

### 2. Sample Space for Two Tosses — $\Omega_2$

$$
\Omega_2 = \{\ (H,H),\ (H,T),\ (T,H),\ (T,T)\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_2| = 2 \times 2 = 4
$$

---

### 3. Sample Space for Three Tosses — $\Omega_3$

$$
\Omega_3 = \{\ (H,H,H),\ (H,H,T),\ (H,T,H),\ (H,T,T),\ (T,H,H),\ (T,H,T),\ (T,T,H),\ (T,T,T)\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_3| = 2 \times 2 \times 2 = 8
$$

---

### 4. General Formula

For $n$ coin tosses, the number of elementary outcomes is:

$$
|\Omega_n| = 2^n
$$

| Experiment | Sample Space Size |
|:---:|:---:|
| $\Omega_1$ (1 toss) | $2^1 = 2$ |
| $\Omega_2$ (2 tosses) | $2^2 = 4$ |
| $\Omega_3$ (3 tosses) | $2^3 = 8$ |

---

### 5. What Does an Elementary Outcome Represent?

| Sample Space | Elementary Outcome | Meaning |
|:---:|:---:|:---|
| $\Omega_1$ | $H$ or $T$ | The single result of one coin toss |
| $\Omega_2$ | $(x_1,\ x_2)$ where $x_i \in \{H, T\}$ | An ordered pair recording the result of toss 1 and toss 2 |
| $\Omega_3$ | $(x_1,\ x_2,\ x_3)$ where $x_i \in \{H, T\}$ | An ordered triple recording the result of each of the three tosses in sequence |

> **Note:** The order matters — the outcome $(H, T)$ is different from $(T, H)$, because the first toss gave a different result in each case.

---

## 💡 Key Insight

Each additional toss **doubles** the number of elementary outcomes, because each existing outcome branches into two new ones (H or T). This gives the exponential growth pattern $2^n$.

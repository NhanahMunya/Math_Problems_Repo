# Task 4 — Weekly Weather Observation

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-sample--spaces-blue)
![Method](https://img.shields.io/badge/method-tree--diagram-orange)

---

## 🎯 Objective

Construct the sample spaces for one, two, and seven days of weather observation, where each day is independently classified as Sunny, Cloudy, or Rainy, and identify what an elementary outcome represents in each case.

---

## 📐 Setup

Each day can be in exactly **one** of three weather states:

- **S** — Sunny
- **C** — Cloudy
- **R** — Rainy

The weather is **observed once per day**, and the **order matters** — each day is a separate stage of the experiment.

---

## 🌳 Tree Diagram

### One Day

```
START
 │
 ├── S
 ├── C
 └── R
```

### Two Days

```
START
 │
 ├── S ──┬── S  → (S, S)
 │       ├── C  → (S, C)
 │       └── R  → (S, R)
 │
 ├── C ──┬── S  → (C, S)
 │       ├── C  → (C, C)
 │       └── R  → (C, R)
 │
 └── R ──┬── S  → (R, S)
         ├── C  → (R, C)
         └── R  → (R, R)
```

> A full tree for seven days would contain $3^7 = 2{,}187$ leaves and is impractical to draw. The two-day diagram above illustrates the branching structure that continues for each additional day.

---

## ✅ Solutions

### 1. Sample Space for One Day — $\Omega_1$

$$
\Omega_1 = \{\ S,\ C,\ R\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_1| = 3
$$

---

### 2. Sample Space for Two Days — $\Omega_2$

Each elementary outcome is an **ordered pair** $(d_1,\ d_2)$ where $d_1, d_2 \in \{S, C, R\}$:

$$
\Omega_2 = \{\ (d_1,\ d_2) \mid d_1,\ d_2 \in \{S,\ C,\ R\}\ \}
$$

Written out fully:

$$
\Omega_2 = \{\ (S,S),\ (S,C),\ (S,R),\ (C,S),\ (C,C),\ (C,R),\ (R,S),\ (R,C),\ (R,R)\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_2| = 3 \times 3 = 9
$$

---

### 3. Sample Space for Seven Days — $\Omega_7$

Each elementary outcome is an **ordered 7-tuple** $(d_1,\ d_2,\ d_3,\ d_4,\ d_5,\ d_6,\ d_7)$ where each $d_i \in \{S, C, R\}$:

$$
\Omega_7 = \{\ (d_1,\ d_2,\ d_3,\ d_4,\ d_5,\ d_6,\ d_7) \mid d_i \in \{S,\ C,\ R\},\ i = 1, \ldots, 7\ \}
$$

**Example elementary outcome:**

$$
(S,\ C,\ R,\ R,\ S,\ C,\ S)
$$

This represents: Mon=Sunny, Tue=Cloudy, Wed=Rainy, Thu=Rainy, Fri=Sunny, Sat=Cloudy, Sun=Sunny.

**Number of elementary outcomes:**

$$
|\Omega_7| = 3^7 = 2{,}187
$$

---

### 4. General Formula

For $n$ days of observation with 3 possible weather states per day:

$$
|\Omega_n| = 3^n
$$

| Experiment | Sample Space Size |
|:---:|:---:|
| $\Omega_1$ (1 day) | $3^1 = 3$ |
| $\Omega_2$ (2 days) | $3^2 = 9$ |
| $\Omega_7$ (7 days) | $3^7 = 2{,}187$ |

---

### 5. What Does an Elementary Outcome Represent?

| Sample Space | Elementary Outcome | Meaning |
|:---:|:---:|:---|
| $\Omega_1$ | $d$ where $d \in \{S, C, R\}$ | The weather state observed on a single day |
| $\Omega_2$ | $(d_1,\ d_2)$ where $d_i \in \{S, C, R\}$ | An ordered pair recording the weather on day 1 and day 2 |
| $\Omega_7$ | $(d_1,\ \ldots,\ d_7)$ where $d_i \in \{S, C, R\}$ | An ordered 7-tuple recording the weather on each day of the week in sequence |

> **Note:** Order matters — the outcome $(S, R)$ is different from $(R, S)$, because the weather on day 1 and day 2 is different in each case. Each position in the tuple corresponds to a specific day.

---

## 💡 Key Insight

This experiment follows the same **$k^n$ pattern** established in the previous tasks, with $k = 3$ weather states and $n$ days:

$$
\text{Coin } (k=2): \quad |\Omega_n| = 2^n
$$

$$
\text{Die } (k=6): \quad |\Omega_n| = 6^n
$$

$$
\text{Weather } (k=3): \quad |\Omega_n| = 3^n
$$

In general, if each observation has $k$ equally likely outcomes and there are $n$ independent observations:

$$
\boxed{|\Omega_n| = k^n}
$$

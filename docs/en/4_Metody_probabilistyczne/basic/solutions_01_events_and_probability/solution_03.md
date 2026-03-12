# Task 3 — Drawing Cards

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-sample--spaces-blue)
![Method](https://img.shields.io/badge/method-with%20and%20without%20replacement-orange)

---

## 🎯 Objective

Construct the sample spaces for drawing cards from a standard 52-card deck — for one draw, two draws with replacement, and two draws without replacement — and identify what an elementary outcome represents in each case.

---

## 📐 Setup

A **standard 52-card deck** consists of:

- **4 suits**: Hearts (♥), Diamonds (♦), Clubs (♣), Spades (♠)
- **13 ranks** per suit: A, 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K

Each card is **unique**, so the deck contains exactly 52 distinct cards.

We denote a generic card as $c \in \mathcal{D}$, where $\mathcal{D}$ is the full deck of 52 cards.

The **order of outcomes matters** — each draw is treated as an ordered sequence.

---

## 🌳 Tree Diagram (Partial)

A full tree is impossible to draw (52 or more branches per level). The structure is illustrated below for a small example deck $\{c_1, c_2, \ldots, c_{52}\}$:

### With Replacement

```
START
 │
 ├── c₁ ──┬── c₁  → (c₁, c₁)  ← same card allowed
 │        ├── c₂  → (c₁, c₂)
 │        ├── ...
 │        └── c₅₂ → (c₁, c₅₂)
 │
 ├── c₂ ── (52 branches, same pattern)
 ├── ...
 └── c₅₂ ── (52 branches, same pattern)
```

### Without Replacement

```
START
 │
 ├── c₁ ──┬── c₂  → (c₁, c₂)  ← c₁ cannot appear again
 │        ├── c₃  → (c₁, c₃)
 │        ├── ...
 │        └── c₅₂ → (c₁, c₅₂)   (only 51 branches)
 │
 ├── c₂ ── (51 branches, c₂ excluded)
 ├── ...
 └── c₅₂ ── (51 branches, c₅₂ excluded)
```

---

## ✅ Solutions

### 1. Sample Space for One Draw — $\Omega_1$

$$
\Omega_1 = \{\ c \mid c \in \mathcal{D}\ \}
$$

That is, the set of all 52 distinct cards in the deck.

**Number of elementary outcomes:**

$$
|\Omega_1| = 52
$$

---

### 2. Sample Space for Two Draws **With Replacement** — $\Omega_2$

The card drawn first is **returned to the deck** before the second draw. The deck is always full for each draw, so the same card can appear twice.

Each elementary outcome is an **ordered pair** $(c_1,\ c_2)$ where both $c_1, c_2 \in \mathcal{D}$:

$$
\Omega_2 = \{\ (c_1,\ c_2) \mid c_1,\ c_2 \in \mathcal{D}\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_2| = 52 \times 52 = 2{,}704
$$

---

### 3. Sample Space for Two Draws **Without Replacement** — $\Omega_2'$

The card drawn first is **not returned**. The second draw is from the remaining 51 cards, so the same card **cannot appear twice**.

Each elementary outcome is an **ordered pair** $(c_1,\ c_2)$ where $c_1 \neq c_2$:

$$
\Omega_2' = \{\ (c_1,\ c_2) \mid c_1,\ c_2 \in \mathcal{D},\ c_1 \neq c_2\ \}
$$

**Number of elementary outcomes:**

$$
|\Omega_2'| = 52 \times 51 = 2{,}652
$$

---

### 4. Comparison of Outcome Counts

| Experiment | Condition | Sample Space Size |
|:---:|:---:|:---:|
| $\Omega_1$ — one draw | — | $52$ |
| $\Omega_2$ — two draws | with replacement | $52 \times 52 = 2{,}704$ |
| $\Omega_2'$ — two draws | without replacement | $52 \times 51 = 2{,}652$ |

> **Key difference:** Without replacement, the second draw has only 51 possible outcomes instead of 52, because the first card is no longer in the deck. This makes drawing the same card twice **impossible**, reducing the total number of outcomes by $52$.

---

### 5. What Does an Elementary Outcome Represent?

| Sample Space | Elementary Outcome | Meaning |
|:---:|:---:|:---|
| $\Omega_1$ | $c$ where $c \in \mathcal{D}$ | The single card drawn from the full deck |
| $\Omega_2$ | $(c_1,\ c_2)$ where $c_1, c_2 \in \mathcal{D}$ | An ordered pair of cards — the 1st and 2nd draw, with the deck reset between draws |
| $\Omega_2'$ | $(c_1,\ c_2)$ where $c_1 \neq c_2$ | An ordered pair of **distinct** cards — the 1st and 2nd draw, with the 1st card removed from the deck |

> **Note:** Order matters in both cases — $(K♥,\ A♠)$ and $(A♠,\ K♥)$ are two different elementary outcomes, because the first and second draws gave different cards in each sequence.

---

## 💡 Key Insight

The distinction between **with** and **without replacement** is fundamental in probability:

$$
\text{With replacement:} \quad |\Omega_2| = 52^2 = 2{,}704
$$

$$
\text{Without replacement:} \quad |\Omega_2'| = 52 \times 51 = 2{,}652
$$

More generally, for $n$ draws from a deck of $N$ cards:

$$
\text{With replacement:} \quad N^n
$$

$$
\text{Without replacement:} \quad N \times (N-1) \times (N-2) \times \cdots \times (N-n+1)
$$

The without-replacement formula is also written as the **falling factorial** $N^{\underline{n}}$ or the **permutation** $P(N, n)$.

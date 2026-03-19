# Task 6 — Combinations in Card Problems

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-combinations--product--and--complement-orange)

---

## 🎯 Objective

Count 5-card hands from a standard 52-card deck satisfying specific conditions, using the product rule and complement rule.

---

## 📐 General Formula

**Combination** — choosing $k$ cards from $n$ available cards where order does not matter:

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

---

## 📐 Deck Setup

A standard 52-card deck contains:

| Category | Count |
|:---|:---:|
| Hearts ♥ | 13 |
| Diamonds ♦ | 13 |
| Clubs ♣ | 13 |
| Spades ♠ | 13 |
| Face cards (J, Q, K across all suits) | 12 |
| Non-face cards | 40 |
| Non-heart cards | 39 |
| **Total** | **52** |

**Total number of 5-card hands:**

$$\binom{52}{5} = \frac{52!}{5! \cdot 47!} = \frac{52 \times 51 \times 50 \times 49 \times 48}{5 \times 4 \times 3 \times 2 \times 1} = 2{,}598{,}960$$

---

## ✅ Solutions

### Problem 1 — Exactly 2 hearts in a 5-card hand

**Strategy — Product rule:**

Split into two independent choices:
- Choose 2 hearts from 13 available hearts: $\binom{13}{2}$
- Choose 3 non-hearts from 39 remaining cards: $\binom{39}{3}$

```
Hearts ♥ (13)        Non-hearts (39)
  choose 2        +     choose 3
    ↓                      ↓
  [ ♥ ♥ ]  [ _ _ _ ]   ← 5-card hand
```

**Applied:** $n_1 = 13$, $k_1 = 2$ and $n_2 = 39$, $k_2 = 3$

$$\binom{13}{2} \times \binom{39}{3} = \frac{13!}{2! \cdot 11!} \times \frac{39!}{3! \cdot 36!}$$

$$= 78 \times 9{,}139 = 712{,}842$$

---

### Problem 2 — At least one heart in a 5-card hand

**Strategy — Complement rule:**

$$\text{at least one heart} = \text{total hands} - \text{hands with no hearts}$$

- Total 5-card hands: $\binom{52}{5} = 2{,}598{,}960$
- Hands with **no hearts** — choose all 5 from the 39 non-heart cards:

$$\binom{39}{5} = \frac{39!}{5! \cdot 34!} = \frac{39 \times 38 \times 37 \times 36 \times 35}{5 \times 4 \times 3 \times 2 \times 1} = \frac{69{,}090{,}840}{120} = 575{,}757$$

**Applied:**

$$\binom{52}{5} - \binom{39}{5} = 2{,}598{,}960 - 575{,}757 = 2{,}023{,}203$$

> **Why complement?** Directly counting "at least one heart" would require adding cases for exactly 1, 2, 3, 4, and 5 hearts — five separate calculations. The complement reduces this to one subtraction.

---

### Problem 3 — No face cards in a 5-card hand

**Strategy — Restricted pool:**

Remove all 12 face cards from consideration. Choose 5 cards freely from the remaining 40 non-face cards:

```
Remove: J♥ Q♥ K♥ J♦ Q♦ K♦ J♣ Q♣ K♣ J♠ Q♠ K♠  (12 cards removed)
Remaining pool: 40 non-face cards
Choose 5 from 40
```

**Applied:** $n = 40$, $k = 5$

$$\binom{40}{5} = \frac{40!}{5! \cdot 35!} = \frac{40 \times 39 \times 38 \times 37 \times 36}{5 \times 4 \times 3 \times 2 \times 1} = \frac{78{,}960{,}960}{120} = 658{,}008$$

---

## 📊 Summary Table

| Problem | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| Exactly 2 hearts | Product rule | $\binom{13}{2} \times \binom{39}{3}$ | $712{,}842$ |
| At least one heart | Complement | $\binom{52}{5} - \binom{39}{5}$ | $2{,}023{,}203$ |
| No face cards | Restricted pool | $\binom{40}{5}$ | $658{,}008$ |

---

## 💡 Key Insights

- **Product rule** applies when a hand must satisfy two independent conditions simultaneously (e.g. exactly 2 hearts AND exactly 3 non-hearts):

$$\binom{n_1}{k_1} \times \binom{n_2}{k_2}$$

- **Complement rule** is always the best approach for "at least one" problems:

$$\text{at least one} = \text{total} - \text{none}$$

- **Restricted pool** — when certain cards are forbidden, simply reduce $n$ to exclude them before applying the combination formula.

- **Sanity checks** — all results must be less than or equal to the total number of hands:

$$712{,}842 < 2{,}598{,}960 \checkmark \quad 2{,}023{,}203 < 2{,}598{,}960 \checkmark \quad 658{,}008 < 2{,}598{,}960 \checkmark$$

# Task 10 — Urn Models

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-combinations--and--k--permutations-orange)

---

## 🎯 Objective

Count the number of ways to draw balls from an urn under different recording rules — order ignored vs order recorded — and apply the product rule for constrained selections.

---

## 📐 Urn Setup

| Color | Count |
|:---:|:---:|
| Red | 5 |
| Blue | 4 |
| Green | 3 |
| **Total** | **12** |

> The key question in every urn problem: **is the order of drawing recorded?**
> - Order ignored → Combination
> - Order recorded → k-Permutation

---

## 📐 General Formulas

**Combination** — order ignored:

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

**k-Permutation** — order recorded:

$$P(n,k) = \frac{n!}{(n-k)!}$$

---

## ✅ Solutions

### Problem 1 — 3 balls drawn without replacement, order ignored

**Model:** Combination — choosing 3 from 12, order does not matter.

**Applied:** $n = 12$, $k = 3$

$$\binom{12}{3} = \frac{12!}{3! \cdot 9!} = \frac{12 \times 11 \times 10}{3 \times 2 \times 1} = \frac{1{,}320}{6} = 220$$

---

### Problem 2 — Exactly 2 red balls, order ignored

**Strategy — Product rule:**

Split into two independent choices:
- Choose 2 red balls from 5: $\binom{5}{2}$
- Choose 1 non-red ball from remaining 7 (4 blue + 3 green): $\binom{7}{1}$

```
Red (5)          Non-red (7)
choose 2    +    choose 1
   ↓                ↓
[ R R ]  [ _ ]   ← 3 balls total, order ignored
```

**Applied:** $n_1 = 5$, $k_1 = 2$ and $n_2 = 7$, $k_2 = 1$

$$\binom{5}{2} \times \binom{7}{1} = \frac{5!}{2! \cdot 3!} \times 7 = 10 \times 7 = 70$$

> **Sanity check:** $70 < 220$ ✓

---

### Problem 3 — 3 balls drawn, order of colors recorded

**Model:** k-Permutation — drawing 3 from 12, order matters (each ball is distinguishable).

```
[ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑
  12    11    10   ← choices per draw
```

**Applied:** $n = 12$, $k = 3$

$$P(12,3) = \frac{12!}{9!} = 12 \times 11 \times 10 = 1{,}320$$

---

### Problem 4 — Exactly 2 red balls, order recorded

**Strategy — Choose positions, then fill them:**

Since order is recorded, we have 3 positions to fill. We need exactly 2 to be red:

**Step 1:** Choose which 2 of the 3 positions are red → $\binom{3}{2} = 3$ ways

```
Possible red positions:
[ R R _ ]
[ R _ R ]
[ _ R R ]
```

**Step 2:** Fill the 2 red positions with distinct red balls in order → $P(5,2)$

**Step 3:** Fill the 1 remaining position with any non-red ball → $7$ choices

**Applied:**

$$\binom{3}{2} \times P(5,2) \times 7 = 3 \times (5 \times 4) \times 7 = 3 \times 20 \times 7 = 420$$

> **Why $\binom{3}{2}$?** The two red positions can be in any of 3 arrangements (RR_, R_R, _RR). Without choosing positions first, we would miss some orderings or double-count others.

> **Sanity check:** $420 < 1{,}320$ ✓

---

## 📊 Summary Table

| Problem | Order? | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|:---:|
| 3 balls, any color | Ignored | Direct combination | $\binom{12}{3}$ | $220$ |
| Exactly 2 red, order ignored | Ignored | Product rule | $\binom{5}{2} \times \binom{7}{1}$ | $70$ |
| 3 balls, order recorded | Recorded | Direct k-permutation | $P(12,3)$ | $1{,}320$ |
| Exactly 2 red, order recorded | Recorded | Choose positions + fill | $\binom{3}{2} \times P(5,2) \times 7$ | $420$ |

---

## ✅ Verification

Order recorded always gives more outcomes than order ignored for the same selection:

$$220 < 1{,}320 \checkmark \qquad 70 < 420 \checkmark$$

The ratio between ordered and unordered counts equals $k!$ — the number of ways to arrange $k$ drawn balls:

$$\frac{1{,}320}{220} = 6 = 3! \checkmark \qquad \frac{420}{70} = 6 = 3! \checkmark$$

---

## 💡 Key Insights

- **Order ignored vs recorded** changes the model completely for the same physical experiment:

$$\text{order ignored} \rightarrow \binom{n}{k} \qquad \text{order recorded} \rightarrow P(n,k) = \binom{n}{k} \times k!$$

- **Constrained ordered selection** — when drawing with a color constraint and order recorded, always:
    1. Choose which **positions** hold the constrained color: $\binom{k}{\text{constrained}}$
    2. Fill constrained positions in order: $P(n_{\text{color}}, \text{constrained})$
    3. Fill remaining positions: remaining choices

- **Ratio check** — the ratio of ordered to unordered outcomes always equals $k!$, providing a built-in verification tool.

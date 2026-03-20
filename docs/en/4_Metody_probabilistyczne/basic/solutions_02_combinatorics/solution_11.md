# Task 11 — Modeling Outcomes

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-conceptual--reasoning-orange)

---

## 🎯 Objective

Understand how the way outcomes are recorded — distinguishable vs indistinguishable objects, order recorded vs ignored, positions treated as distinct — fundamentally changes the counting model and the number of outcomes.

---

## 📐 Box Setup

The box contains:

| Color | Count |
|:---:|:---:|
| Red | 4 |
| Blue | 4 |
| Green | 3 |
| **Total** | **11** |

---

## ✅ Sub-problem 1 — Distinguishable vs Indistinguishable Objects

### Part 1 — Balls of the same color are indistinguishable

**Model:** Permutation with repeated elements — all 11 balls arranged, but identical-colored balls are treated as the same.

**Applied:** $n = 11$, $n_1 = 4$ (R), $n_2 = 4$ (B), $n_3 = 3$ (G)

$$\frac{11!}{4! \cdot 4! \cdot 3!} = \frac{39{,}916{,}800}{24 \times 24 \times 6} = \frac{39{,}916{,}800}{3{,}456} = 11{,}550$$

---

### Part 2 — Every ball is individually labelled

**Model:** Permutation — all 11 balls are now distinct objects.

$$11! = 39{,}916{,}800$$

---

### Part 3 — Why are the answers different?

When balls are **indistinguishable**, swapping two balls of the same color produces no new arrangement — it looks identical. For example, swapping $R_1$ and $R_2$ in a labelled arrangement gives a different sequence, but if both are just "R", nothing changes visually.

The number of ways to rearrange $n_i$ identical objects within their group is $n_i!$. Since these rearrangements add no new outcomes, we divide them out:

$$\frac{11!}{4! \cdot 4! \cdot 3!} = \frac{\text{labelled arrangements}}{\text{overcounting factor}}$$

The overcounting factor here is $4! \times 4! \times 3! = 3{,}456$, meaning each distinct color arrangement corresponds to $3{,}456$ labelled arrangements that all look the same when colors are indistinguishable.

---

## ✅ Sub-problem 2 — Recording Order vs Ignoring Order

Three balls drawn **without replacement** from the same box (11 balls: 4R, 4B, 3G).

### Part 1 — Only the set of colors is recorded, order ignored

**Model:** Combination — we only care which colors appear, not the sequence.

The possible color sets when drawing 3 balls (allowing repeated colors of different balls):

$$\binom{11}{3} = \frac{11!}{3! \cdot 8!} = \frac{11 \times 10 \times 9}{6} = 165 \text{ unordered samples}$$

---

### Part 2 — The sequence of colors is recorded

**Model:** k-Permutation — the order of drawing matters.

$$P(11,3) = \frac{11!}{8!} = 11 \times 10 \times 9 = 990 \text{ ordered sequences}$$

---

### Part 3 — Why does recording order change the count?

When order is ignored, the outcome $\{R, B, G\}$ is a single result regardless of which ball was drawn first. When order is recorded, $(R, B, G)$, $(R, G, B)$, $(B, R, G)$, $(B, G, R)$, $(G, R, B)$, $(G, B, R)$ are all **different outcomes** — 6 different sequences from the same set of 3 balls.

In general, every unordered selection of $k$ objects corresponds to exactly $k!$ ordered sequences:

$$P(n,k) = \binom{n}{k} \times k!$$

$$990 = 165 \times 3! = 165 \times 6 \checkmark$$

Recording order therefore **multiplies** the count by $k!$.

---

## ✅ Sub-problem 3 — PIN Code vs 4-Digit Number

### Part 1 — PIN codes, repetition allowed

**Model:** Sequence with repetition — 4 positions, each picks from $\{0,1,\ldots,9\}$.

```
[ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑
  10   10    10    10    ← all positions free
```

**Applied:** $n = 10$, $k = 4$

$$10^4 = 10{,}000$$

---

### Part 2 — 4-digit numbers, no leading zero

**Model:** Product rule with leading digit restriction — first digit cannot be 0.

```
[ _ ] [ _ ] [ _ ] [ _ ]
  ↑     ↑     ↑     ↑
  9    10    10    10    ← first digit restricted
(1-9) (0-9) (0-9) (0-9)
```

**Applied:**

$$9 \times 10^3 = 9{,}000$$

---

### Part 3 — Why are PIN codes and 4-digit numbers counted differently?

A **PIN code** is a sequence of symbols — $0000$ is a perfectly valid PIN. The first position has no restriction, giving $10^4 = 10{,}000$ codes.

A **4-digit number** must represent a value between $1{,}000$ and $9{,}999$. A leading zero would make it a 3-digit number or fewer — for example, $0123$ is just $123$. Therefore the first digit is restricted to $\{1,\ldots,9\}$, giving $9 \times 10^3 = 9{,}000$ numbers.

The difference is exactly the $1{,}000$ codes beginning with 0 that are valid PINs but not valid 4-digit numbers:

$$10{,}000 - 9{,}000 = 1{,}000 = 10^3 \checkmark$$

---

### Part 4 — Why are 1234 and 4321 different outcomes?

Both PIN codes and numbers are **ordered sequences** — the position of each digit carries meaning:

- $1234$ means: thousands digit $= 1$, hundreds $= 2$, tens $= 3$, units $= 4$
- $4321$ means: thousands digit $= 4$, hundreds $= 3$, tens $= 2$, units $= 1$

These represent different numerical values ($1{,}234 \neq 4{,}321$) and different PIN codes (entering $1234$ when the correct PIN is $4321$ would fail). Since each position is a **distinct place** with its own meaning, any change in digit order produces a genuinely different outcome.

This is why all digit-based counting uses **ordered** models (sequences or k-permutations), never combinations.

---

## 📊 Summary Table

| Sub-problem | Key distinction | Model | Result |
|:---|:---|:---:|:---:|
| Indistinguishable balls | Same color = same object | Permutation with repeats | $11{,}550$ |
| Distinguishable balls | Each ball is unique | Permutation | $39{,}916{,}800$ |
| Order ignored | Set of colors only | Combination | $165$ |
| Order recorded | Sequence of colors | k-Permutation | $990$ |
| PIN code | Leading zero allowed | $10^4$ | $10{,}000$ |
| 4-digit number | No leading zero | $9 \times 10^3$ | $9{,}000$ |

---

## 💡 Key Insights

- **Identical objects divide** — indistinguishable objects reduce the count by dividing out the internal rearrangements of each identical group:

$$\frac{n!}{n_1! \cdot n_2! \cdots n_r!}$$

- **Recording order multiplies** — switching from unordered to ordered always multiplies by $k!$:

$$P(n,k) = \binom{n}{k} \times k!$$

- **Leading digit restriction subtracts** — numbers have $10^{k-1}$ fewer outcomes than PIN codes of the same length, because all codes starting with 0 are excluded.

- **Position = meaning** — whenever each position in a sequence represents a distinct place (digit value, rank, slot), the outcomes are inherently ordered and combinations are the wrong model.

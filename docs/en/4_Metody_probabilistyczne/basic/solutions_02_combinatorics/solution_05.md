# Task 5 — Combinations

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-combinations-orange)

---

## 🎯 Objective

Count the number of ways to select groups of people from a larger set, including constrained cases using fixed members, the complement rule, and the product rule.

---

## 📐 General Formula

**Combination** — choosing $k$ objects from $n$ distinct objects where order does not matter:

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

- $n$ = total number of objects to choose from
- $k$ = how many are being chosen
- $k!$ = divides out the orderings of the chosen group (order doesn't matter)
- $(n-k)!$ = cancels the unchosen objects from $n!$

---

## ✅ Solutions

### Problem 1 — Committee of 4 from 12 students

**Model:** Combination — choosing 4 from 12, order does not matter.

**Applied:** $n = 12$, $k = 4$

$$\binom{12}{4} = \frac{12!}{4! \cdot 8!} = \frac{12 \times 11 \times 10 \times 9}{4 \times 3 \times 2 \times 1} = \frac{11{,}880}{24} = 495$$

---

### Problem 2 — Committee of 4 containing a particular student

**Strategy — Fix and choose:**
Fix the particular student (call them A) on the committee. Only 3 remaining spots need to be filled from the remaining 11 students:

```
[ A ] _ _ _
fixed  ← choose 3 from remaining 11 →
```

**Applied:** $n = 11$, $k = 3$

$$\binom{11}{3} = \frac{11!}{3! \cdot 8!} = \frac{11 \times 10 \times 9}{3 \times 2 \times 1} = \frac{990}{6} = 165$$

> **Sanity check:** Committees containing A ($165$) should be less than total committees ($495$): $165 < 495$ ✓

---

### Problem 3 — Committee of 4 containing at least one of two particular students

**Strategy — Complement rule:**

It is easier to subtract the unwanted case (neither student is on the committee) from the total:

$$\text{at least one of A or B} = \text{total} - \text{neither A nor B}$$

- Total committees: $\binom{12}{4} = 495$
- Committees with **neither** A nor B — choose all 4 from the remaining 10 students:

$$\binom{10}{4} = \frac{10!}{4! \cdot 6!} = \frac{10 \times 9 \times 8 \times 7}{4 \times 3 \times 2 \times 1} = \frac{5{,}040}{24} = 210$$

**Applied:**

$$\binom{12}{4} - \binom{10}{4} = 495 - 210 = 285$$

> **Why complement?** Directly counting "at least one" would require adding three separate cases: (only A), (only B), (both A and B). The complement reduces this to one subtraction.

---

### Problem 4 — Exactly two women from 7 men and 5 women

**Strategy — Product rule:**

This splits into two **independent** choices:
- Choose 2 women from 5: $\binom{5}{2}$
- Choose 2 men from 7: $\binom{7}{2}$

Since both choices must happen together, multiply:

$$\binom{5}{2} \times \binom{7}{2}$$

**Applied:** $n_1 = 5$, $k_1 = 2$ (women) and $n_2 = 7$, $k_2 = 2$ (men)

$$\binom{5}{2} \times \binom{7}{2} = \frac{5!}{2! \cdot 3!} \times \frac{7!}{2! \cdot 5!} = 10 \times 21 = 210$$

> **Why multiply?** For every way of choosing 2 women there are 21 ways of choosing 2 men — the product rule gives the total number of combined selections.

---

## 📊 Summary Table

| Problem | Strategy | Formula | Result |
|:---|:---:|:---:|:---:|
| Committee of 4 from 12 | Direct combination | $\binom{12}{4}$ | $495$ |
| Must contain student A | Fix A, choose rest | $\binom{11}{3}$ | $165$ |
| At least one of A or B | Complement | $\binom{12}{4} - \binom{10}{4}$ | $285$ |
| Exactly 2 women | Product rule | $\binom{5}{2} \times \binom{7}{2}$ | $210$ |

---

## 💡 Key Insights

- **Fix and choose** — when a particular member must be included, fix them and reduce both $n$ and $k$ by 1:

$$\binom{n}{k} \rightarrow \binom{n-1}{k-1}$$

- **Complement rule** — always use complement for "at least one" problems — it turns a multi-case sum into a single subtraction:

$$\text{at least one} = \text{total} - \text{none}$$

- **Product rule** — when a selection has two independent parts (e.g. men and women), multiply the combinations:

$$\binom{n_1}{k_1} \times \binom{n_2}{k_2}$$

- **Sanity checks** — constrained counts must always be less than or equal to the unconstrained total.

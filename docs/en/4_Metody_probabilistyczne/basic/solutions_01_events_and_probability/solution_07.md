# Task 7 — Events and Probabilities in Die Rolling

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-events--and--probability-blue)
![Method](https://img.shields.io/badge/method-classical--probability-orange)

---

## 🎯 Objective

Assign probabilities to all elementary outcomes in $\Omega_1$, $\Omega_2$, and $\Omega_3$, then describe and compute the probabilities of given events as subsets of the sample space.

---

## 📐 Setup

From **Task 2**, the sample spaces are:

$$\Omega_1 = \{1, 2, 3, 4, 5, 6\}, \quad |\Omega_1| = 6$$

$$\Omega_2 = \{(i, j) \mid i, j \in \{1,\ldots,6\}\}, \quad |\Omega_2| = 36$$

$$\Omega_3 = \{(i, j, k) \mid i, j, k \in \{1,\ldots,6\}\}, \quad |\Omega_3| = 216$$

Since the die is **fair**, all elementary outcomes are **equally likely**:

$$P(\omega) = \frac{1}{6} \text{ in } \Omega_1, \qquad P(\omega) = \frac{1}{36} \text{ in } \Omega_2, \qquad P(\omega) = \frac{1}{216} \text{ in } \Omega_3$$

The probability of any event $A$ is:

$$P(A) = \frac{|A|}{|\Omega|}$$

---

## 🎲 Probability Assignments

### $\Omega_1$ — One Roll

Each outcome $i \in \{1, 2, 3, 4, 5, 6\}$ has probability $\dfrac{1}{6}$.

### $\Omega_2$ — Two Rolls

Each outcome $(i, j)$ has probability $\dfrac{1}{36}$.

### $\Omega_3$ — Three Rolls

Each outcome $(i, j, k)$ has probability $\dfrac{1}{216}$.

---

## ✅ Solutions

### One Die Roll

**$A_1$ — the result is even**

```
A₁ = { 2, 4, 6 }
```

$$P(A_1) = \frac{3}{6} = \frac{1}{2}$$

---

**$B_1$ — the result is greater than 4**

```
B₁ = { 5, 6 }
```

$$P(B_1) = \frac{2}{6} = \frac{1}{3}$$

---

**$C_1$ — the result is at most 3**

```
C₁ = { 1, 2, 3 }
```

$$P(C_1) = \frac{3}{6} = \frac{1}{2}$$

---

### Two Die Rolls

**$A_2$ — the sum of the results equals 7**

All ordered pairs $(i, j)$ with $i + j = 7$:

```
A₂ = { (1,6), (2,5), (3,4), (4,3), (5,2), (6,1) }
```

$$P(A_2) = \frac{6}{36} = \frac{1}{6}$$

---

**$B_2$ — both results are the same**

```
B₂ = { (1,1), (2,2), (3,3), (4,4), (5,5), (6,6) }
```

$$P(B_2) = \frac{6}{36} = \frac{1}{6}$$

---

**$C_2$ — the sum of the results is at least 10**

All ordered pairs $(i, j)$ with $i + j \geq 10$:

| Sum | Pairs |
|:---:|:---|
| 10 | $(4,6),\ (5,5),\ (6,4)$ |
| 11 | $(5,6),\ (6,5)$ |
| 12 | $(6,6)$ |

```
C₂ = { (4,6), (5,5), (6,4), (5,6), (6,5), (6,6) }
```

$$P(C_2) = \frac{6}{36} = \frac{1}{6}$$

---

### Three Die Rolls

**$A_3$ — the sum of the results equals 10**

All ordered triples $(i, j, k)$ with $i + j + k = 10$, where each value is in $\{1,\ldots,6\}$:

| Composition | Ordered triples | Count |
|:---:|:---|:---:|
| $(1, 3, 6)$ | $(1,3,6),(1,6,3),(3,1,6),(3,6,1),(6,1,3),(6,3,1)$ | 6 |
| $(1, 4, 5)$ | $(1,4,5),(1,5,4),(4,1,5),(4,5,1),(5,1,4),(5,4,1)$ | 6 |
| $(2, 2, 6)$ | $(2,2,6),(2,6,2),(6,2,2)$ | 3 |
| $(2, 3, 5)$ | $(2,3,5),(2,5,3),(3,2,5),(3,5,2),(5,2,3),(5,3,2)$ | 6 |
| $(2, 4, 4)$ | $(2,4,4),(4,2,4),(4,4,2)$ | 3 |
| $(3, 3, 4)$ | $(3,3,4),(3,4,3),(4,3,3)$ | 3 |
| $(4, 3, 3)$ | already counted above | — |

Total outcomes: $6 + 6 + 3 + 6 + 3 + 3 = 27$

$$P(A_3) = \frac{27}{216} = \frac{1}{8}$$

---

**$B_3$ — exactly two rolls give the same number**

An outcome $(i, j, k)$ qualifies if **exactly two** of the three values are equal (not all three).

- Choose which number is repeated: 6 choices
- Choose which two positions it occupies: $\binom{3}{2} = 3$ choices
- Choose the third (different) value: 5 choices

$$|B_3| = 6 \times 3 \times 5 = 90$$

$$P(B_3) = \frac{90}{216} = \frac{5}{12}$$

---

**$C_3$ — the outcomes contain two twos and one three (in any order)**

All ordered arrangements of $(2, 2, 3)$:

```
C₃ = { (2,2,3), (2,3,2), (3,2,2) }
```

$$P(C_3) = \frac{3}{216} = \frac{1}{72}$$

---

### Additional Event on $\Omega_3$

**$D_3$ — all three rolls give the same number**

```
D₃ = { (1,1,1), (2,2,2), (3,3,3), (4,4,4), (5,5,5), (6,6,6) }
```

$$P(D_3) = \frac{6}{216} = \frac{1}{36}$$

> This is the complement perspective of $B_3$: outcomes split into three categories — all different, exactly two the same, or all three the same.

$$|B_3| + |D_3| + |\text{all different}| = 90 + 6 + 120 = 216 \checkmark$$

---

## 💡 Key Insights

- **Listing pairs/triples systematically** by fixing the sum avoids missing outcomes.
- **Counting arrangements** using $\binom{3}{2}$ is faster than listing all triples for $B_3$.
- **Complement rule** is useful for "at least" events:

$$P(A) = 1 - P(A^c)$$

- A useful **sanity check**: all outcome counts across mutually exclusive exhaustive events must sum to $|\Omega|$.

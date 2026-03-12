# Task 9 — Events and Probabilities in Weekly Weather Observation

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-events--and--probability-blue)
![Method](https://img.shields.io/badge/method-independence--and--binomial-orange)

---

## 🎯 Objective

Using the sample space $\Omega_7$ from Task 4, compute probabilities of events over a 7-day weather observation, where each day is independently Sunny (S), Cloudy (C), or Rainy (R) with equal probability $\frac{1}{3}$.

---

## 📐 Setup

From **Task 4**:

$$\Omega_7 = \{(d_1, d_2, d_3, d_4, d_5, d_6, d_7) \mid d_i \in \{S, C, R\}\}, \quad |\Omega_7| = 3^7 = 2{,}187$$

Each day is **independent**, and each weather state occurs with probability:

$$P(S) = P(C) = P(R) = \frac{1}{3}$$

Since days are independent, the probability of any specific 7-day sequence multiplies:

$$P(d_1, d_2, \ldots, d_7) = P(d_1) \times P(d_2) \times \cdots \times P(d_7)$$

The days of the week are labelled as:

| $d_1$ | $d_2$ | $d_3$ | $d_4$ | $d_5$ | $d_6$ | $d_7$ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Mon | Tue | Wed | Thu | Fri | Sat | Sun |

---

## ✅ Solutions

### Event $A$ — the entire weekend is sunny (Saturday and Sunday are both S)

Only $d_6$ and $d_7$ are fixed to S. The remaining 5 days are free.

$$P(A) = P(d_6 = S) \times P(d_7 = S) = \frac{1}{3} \times \frac{1}{3} = \frac{1}{9}$$

---

### Event $B$ — Wednesday, Thursday, and Friday are all rainy

Only $d_3$, $d_4$, and $d_5$ are fixed to R. The remaining 4 days are free.

$$P(B) = P(d_3 = R) \times P(d_4 = R) \times P(d_5 = R) = \frac{1}{3} \times \frac{1}{3} \times \frac{1}{3} = \frac{1}{27}$$

---

### Event $C$ — at least one day during the week is sunny

Using the **complement rule** — the complement of $C$ is that **no day is sunny**, meaning every day is either C or R:

$$P(\text{not sunny on one day}) = \frac{2}{3}$$

$$P(C^c) = \left(\frac{2}{3}\right)^7 = \frac{128}{2{,}187}$$

$$P(C) = 1 - \left(\frac{2}{3}\right)^7 = 1 - \frac{128}{2{,}187} = \frac{2{,}059}{2{,}187}$$

---

### Event $D$ — no rainy day occurs during the entire week

Every day must be either S or C:

$$P(\text{not rainy on one day}) = \frac{2}{3}$$

$$P(D) = \left(\frac{2}{3}\right)^7 = \frac{128}{2{,}187}$$

---

### Event $E$ — exactly two days during the week are sunny

This requires:
- Choosing **which 2 of the 7 days** are sunny: $\binom{7}{2}$ ways
- Each sunny day contributes probability $\frac{1}{3}$
- Each non-sunny day (5 days) contributes probability $\frac{2}{3}$

**Why $\binom{7}{2}$?**

We are choosing 2 days from 7 without caring about order. The formula is:

$$\binom{7}{2} = \frac{7!}{2! \cdot 5!} = \frac{7 \times 6}{2 \times 1} = 21$$

This counts all unique pairs of days that could be sunny:

| | | | | | |
|---|---|---|---|---|---|
| Mon-Tue | Mon-Wed | Mon-Thu | Mon-Fri | Mon-Sat | Mon-Sun |
| Tue-Wed | Tue-Thu | Tue-Fri | Tue-Sat | Tue-Sun | |
| Wed-Thu | Wed-Fri | Wed-Sat | Wed-Sun | | |
| Thu-Fri | Thu-Sat | Thu-Sun | | | |
| Fri-Sat | Fri-Sun | | | | |
| Sat-Sun | | | | | |

Each specific arrangement of exactly 2 sunny days has the same probability:

$$\left(\frac{1}{3}\right)^2 \times \left(\frac{2}{3}\right)^5 = \frac{1}{9} \times \frac{32}{243} = \frac{32}{2{,}187}$$

Therefore:

$$P(E) = \binom{7}{2} \times \left(\frac{1}{3}\right)^2 \times \left(\frac{2}{3}\right)^5 = 21 \times \frac{32}{2{,}187} = \frac{672}{2{,}187}$$

---

### Additional Event — exactly one day during the week is rainy

Choose which 1 of the 7 days is rainy: $\binom{7}{1} = 7$ ways.

$$P(F) = \binom{7}{1} \times \left(\frac{1}{3}\right)^1 \times \left(\frac{2}{3}\right)^6 = 7 \times \frac{1}{3} \times \frac{64}{729} = 7 \times \frac{64}{2{,}187} = \frac{448}{2{,}187}$$

---

## 💡 Key Insights

- **Independence** means we multiply probabilities across days — the weather on Monday does not affect Tuesday.

- **Complement rule** is the cleanest approach for "at least one" events:

$$P(\text{at least one sunny}) = 1 - P(\text{no sunny days}) = 1 - \left(\frac{2}{3}\right)^7$$

- **Binomial probability formula** handles "exactly $k$ out of $n$" events:

$$P(\text{exactly } k \text{ sunny days out of } n) = \binom{n}{k} \left(\frac{1}{3}\right)^k \left(\frac{2}{3}\right)^{n-k}$$

- Events $C$ and $D$ have the **same probability** $\frac{128}{2{,}187}$ — both fix 7 days to one of 2 states, so the structure is identical even though the events differ.

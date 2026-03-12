# Task 6 — Events and Probabilities in Coin Tossing

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-events--and--probability-blue)
![Method](https://img.shields.io/badge/method-classical--probability-orange)

---

## 🎯 Objective

Assign probabilities to all elementary outcomes in $\Omega_1$, $\Omega_2$, and $\Omega_3$, then describe and compute the probabilities of given events as subsets of the sample space.

---

## 📐 Setup

From **Task 1**, the sample spaces are:

$$\Omega_1 = \{H,\ T\}, \quad |\Omega_1| = 2$$

$$\Omega_2 = \{(H,H),\ (H,T),\ (T,H),\ (T,T)\}, \quad |\Omega_2| = 4$$

$$\Omega_3 = \{(H,H,H),\ (H,H,T),\ (H,T,H),\ (H,T,T),\ (T,H,H),\ (T,H,T),\ (T,T,H),\ (T,T,T)\}, \quad |\Omega_3| = 8$$

Since the coin is **fair**, all elementary outcomes are **equally likely**. The probability of any event $A$ is:

$$P(A) = \frac{|A|}{|\Omega|}$$

---

## 🎲 Probability Assignments

### $\Omega_1$ — One Toss

| Outcome | Probability |
|:---:|:---:|
| $H$ | $\dfrac{1}{2}$ |
| $T$ | $\dfrac{1}{2}$ |

### $\Omega_2$ — Two Tosses

| Outcome | Probability |
|:---:|:---:|
| $(H,H)$ | $\dfrac{1}{4}$ |
| $(H,T)$ | $\dfrac{1}{4}$ |
| $(T,H)$ | $\dfrac{1}{4}$ |
| $(T,T)$ | $\dfrac{1}{4}$ |

### $\Omega_3$ — Three Tosses

| Outcome | Probability |
|:---:|:---:|
| $(H,H,H)$ | $\dfrac{1}{8}$ |
| $(H,H,T)$ | $\dfrac{1}{8}$ |
| $(H,T,H)$ | $\dfrac{1}{8}$ |
| $(H,T,T)$ | $\dfrac{1}{8}$ |
| $(T,H,H)$ | $\dfrac{1}{8}$ |
| $(T,H,T)$ | $\dfrac{1}{8}$ |
| $(T,T,H)$ | $\dfrac{1}{8}$ |
| $(T,T,T)$ | $\dfrac{1}{8}$ |

---

## ✅ Solutions

### One Coin Toss

**$A_1$ — the result is heads**

```
A₁ = { H }
```

$$P(A_1) = \frac{1}{2}$$

---

**$B_1$ — the result is tails**

```
B₁ = { T }
```

$$P(B_1) = \frac{1}{2}$$

---

**$C_1$ — the result is not tails**

```
C₁ = { H }
```

> $C_1$ is the complement of $B_1$, so $C_1 = A_1$.

$$P(C_1) = \frac{1}{2}$$

---

### Two Coin Tosses

**$A_2$ — exactly one head occurs**

```
A₂ = { (H,T), (T,H) }
```

$$P(A_2) = \frac{2}{4} = \frac{1}{2}$$

---

**$B_2$ — at least one head occurs**

```
B₂ = { (H,H), (H,T), (T,H) }
```

> "At least one head" means everything except both tails.

$$P(B_2) = \frac{3}{4}$$

---

**$C_2$ — both tosses give the same result**

```
C₂ = { (H,H), (T,T) }
```

$$P(C_2) = \frac{2}{4} = \frac{1}{2}$$

---

### Three Coin Tosses

**$A_3$ — exactly two heads occur**

```
A₃ = { (H,H,T), (H,T,H), (T,H,H) }
```

$$P(A_3) = \frac{3}{8}$$

---

**$B_3$ — at least one tail occurs**

```
B₃ = Ω₃ \ { (H,H,H) } = { (H,H,T), (H,T,H), (H,T,T), (T,H,H), (T,H,T), (T,T,H), (T,T,T) }
```

> It is easier to use the complement: $P(B_3) = 1 - P(\text{no tails}) = 1 - P(\{(H,H,H)\})$.

$$P(B_3) = 1 - \frac{1}{8} = \frac{7}{8}$$

---

**$C_3$ — all three tosses give the same result**

```
C₃ = { (H,H,H), (T,T,T) }
```

$$P(C_3) = \frac{2}{8} = \frac{1}{4}$$

---

### Additional Event on $\Omega_3$

**$D_3$ — the first toss is heads**

```
D₃ = { (H,H,H), (H,H,T), (H,T,H), (H,T,T) }
```

$$P(D_3) = \frac{4}{8} = \frac{1}{2}$$

> This confirms the intuitive result: regardless of what happens on the other tosses, the first toss is heads with probability $\frac{1}{2}$.

---

## 💡 Key Insights

- **Complement rule** simplifies calculations for "at least one" events:

$$P(A) = 1 - P(A^c)$$

- All probabilities must sum to 1 over the full sample space — a useful check:

$$\sum_{\omega \in \Omega} P(\omega) = 1$$

- The probability of an event **grows** with the number of outcomes satisfying it and **shrinks** as the sample space gets larger.

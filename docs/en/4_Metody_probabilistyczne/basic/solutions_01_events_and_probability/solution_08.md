# Task 8 — Events and Probabilities in Card Drawing

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-events--and--probability-blue)
![Method](https://img.shields.io/badge/method-classical--probability-orange)

---

## 🎯 Objective

Assign probabilities to all elementary outcomes in $\Omega_1$, $\Omega_2$, and $\Omega_2'$, then describe and compute the probabilities of given events as subsets of the sample space.

---

## 📐 Setup

From **Task 3**, the sample spaces are:

$$\Omega_1 = \{c \mid c \in \mathcal{D}\}, \quad |\Omega_1| = 52$$

$$\Omega_2 = \{(c_1, c_2) \mid c_1, c_2 \in \mathcal{D}\}, \quad |\Omega_2| = 2{,}704 \quad \text{(with replacement)}$$

$$\Omega_2' = \{(c_1, c_2) \mid c_1, c_2 \in \mathcal{D},\ c_1 \neq c_2\}, \quad |\Omega_2'| = 2{,}652 \quad \text{(without replacement)}$$

The deck has:
- **4 suits**: Hearts (♥), Diamonds (♦), Clubs (♣), Spades (♠) — **13 cards each**
- **13 ranks**: A, 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K — **4 cards each**
- **Face cards**: J, Q, K — **12 face cards total** (3 per suit)
- **Aces**: 4 total (one per suit)

Since the deck is **well-shuffled**, all elementary outcomes are equally likely:

$$P(\omega) = \frac{1}{52} \text{ in } \Omega_1, \qquad P(\omega) = \frac{1}{2{,}704} \text{ in } \Omega_2, \qquad P(\omega) = \frac{1}{2{,}652} \text{ in } \Omega_2'$$

---

## ✅ Solutions

### One Card Drawn

**$A_1$ — the card is a heart**

There are 13 hearts in the deck.

$$P(A_1) = \frac{13}{52} = \frac{1}{4}$$

---

**$B_1$ — the card is a king**

There are 4 kings in the deck (one per suit).

$$P(B_1) = \frac{4}{52} = \frac{1}{13}$$

---

**$C_1$ — the card is not a face card**

Face cards are J, Q, K — that is $3 \times 4 = 12$ cards total. Non-face cards: $52 - 12 = 40$.

$$P(C_1) = \frac{40}{52} = \frac{10}{13}$$

---

### Two Cards Drawn (with replacement)

**$A_2$ — both cards are hearts**

Each draw independently picks a heart with probability $\frac{13}{52} = \frac{1}{4}$:

$$P(A_2) = \frac{13}{52} \times \frac{13}{52} = \frac{1}{4} \times \frac{1}{4} = \frac{1}{16}$$

---

**$B_2$ — both cards have the same rank**

- First card can be anything: 52 choices
- Second card must match the rank of the first: 4 cards of that rank out of 52

$$P(B_2) = \frac{52 \times 4}{52 \times 52} = \frac{4}{52} = \frac{1}{13}$$

> Alternatively: given any first card, the probability the second matches its rank is $\frac{4}{52} = \frac{1}{13}$.

---

**$C_2$ — at least one card is an ace**

Using the complement — probability of **no aces** in either draw:

$$P(\text{no ace on draw 1}) = \frac{48}{52}, \qquad P(\text{no ace on draw 2}) = \frac{48}{52}$$

$$P(C_2) = 1 - \frac{48}{52} \times \frac{48}{52} = 1 - \left(\frac{12}{13}\right)^2 = 1 - \frac{144}{169} = \frac{25}{169}$$

---

### Two Cards Drawn (without replacement)

**$A_3$ — both cards are hearts**

- First draw: 13 hearts out of 52 cards
- Second draw: 12 hearts remaining out of 51 cards

$$P(A_3) = \frac{13}{52} \times \frac{12}{51} = \frac{156}{2{,}652} = \frac{1}{17}$$

---

**$B_3$ — both cards have the same rank**

- First card can be anything: 52 choices
- Second card must match the rank of the first: only 3 remaining cards of that rank out of 51

$$P(B_3) = \frac{52 \times 3}{52 \times 51} = \frac{3}{51} = \frac{1}{17}$$

> Note: with replacement this was $\frac{1}{13}$, without replacement it drops to $\frac{1}{17}$ because one card of that rank is already removed.

---

**$C_3$ — one card is a king and the other is a queen (in any order)**

Two possible orderings: (King, Queen) or (Queen, King).

$$P(\text{King then Queen}) = \frac{4}{52} \times \frac{4}{51} = \frac{16}{2{,}652}$$

$$P(\text{Queen then King}) = \frac{4}{52} \times \frac{4}{51} = \frac{16}{2{,}652}$$

$$P(C_3) = \frac{16}{2{,}652} + \frac{16}{2{,}652} = \frac{32}{2{,}652} = \frac{8}{663}$$

---

### Additional Event on $\Omega_2'$

**$D_3$ — the two cards are from different suits**

Using the complement — probability both cards share the **same suit**:

$$P(\text{same suit}) = \frac{13}{52} \times \frac{12}{51} \times 4 = \frac{4 \times 156}{2{,}652} = \frac{624}{2{,}652} = \frac{12}{51}$$

> Multiply by 4 because there are 4 suits that could match.

$$P(D_3) = 1 - \frac{12}{51} = \frac{39}{51} = \frac{13}{17}$$

---

## 💡 Key Insights

- **With vs without replacement** changes probabilities significantly — the second draw depends on the first only in the without-replacement case:

$$\text{With replacement: } \frac{13}{52} \times \frac{13}{52} = \frac{1}{16} \qquad \text{Without replacement: } \frac{13}{52} \times \frac{12}{51} = \frac{1}{17}$$

- **Complement rule** simplifies "at least one" events considerably:

$$P(\text{at least one ace}) = 1 - P(\text{no aces})$$

- **Order matters** for events like $C_3$ — always account for all valid orderings.

- A useful **sanity check**: all computed probabilities must lie in $[0, 1]$.

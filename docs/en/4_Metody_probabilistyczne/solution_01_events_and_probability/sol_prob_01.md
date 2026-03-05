# Task 1 – Random Events and Probability

## Problem

The sample space of the experiment is

$$
\Omega = {\omega_1, \omega_2, \omega_3, \omega_4, \omega_5}
$$

Two events are defined:

$$
A = {\omega_1, \omega_3, \omega_5}
$$

$$
B = {\omega_2, \omega_3, \omega_4}
$$

We need to determine:

1. $A \cup B$ — union
2. $A \cap B$ — intersection
3. $B \setminus A$ — difference
4. $A \setminus B$

---

# Step 1 — Understanding the Events

An **event** is a subset of the sample space $\Omega$.

| Event | Elements                       |
| ----- | ------------------------------ |
| $A$   | ${\omega_1,\omega_3,\omega_5}$ |
| $B$   | ${\omega_2,\omega_3,\omega_4}$ |

---

# 1. Union of Events $A \cup B$

The **union** contains all elementary outcomes that belong to **at least one** of the events.

$$
A \cup B = {\omega \in \Omega : \omega \in A \text{ or } \omega \in B}
$$

Combining elements from both sets without repetition:

$$
A \cup B =
{\omega_1,\omega_2,\omega_3,\omega_4,\omega_5}
$$

Therefore

$$
A \cup B = \Omega
$$

---

# 2. Intersection of Events $A \cap B$

The **intersection** contains elements that belong to **both** sets.

$$
A \cap B = {\omega \in \Omega : \omega \in A \text{ and } \omega \in B}
$$

Comparing the sets:

* $A = {\omega_1,\omega_3,\omega_5}$
* $B = {\omega_2,\omega_3,\omega_4}$

The only common element is:

$$
A \cap B = {\omega_3}
$$

---

# 3. Difference $B \setminus A$

The difference contains elements in $B$ that are **not in $A$**.

$$
B \setminus A = {\omega \in B : \omega \notin A}
$$

From $B = {\omega_2,\omega_3,\omega_4}$ remove $\omega_3$.

$$
B \setminus A = {\omega_2,\omega_4}
$$

---

# 4. Difference $A \setminus B$

Similarly,

$$
A \setminus B = {\omega \in A : \omega \notin B}
$$

From $A = {\omega_1,\omega_3,\omega_5}$ remove $\omega_3$.

$$
A \setminus B = {\omega_1,\omega_5}
$$

---

# Final Results

$$
A \cup B = {\omega_1,\omega_2,\omega_3,\omega_4,\omega_5}
$$

$$
A \cap B = {\omega_3}
$$

$$
B \setminus A = {\omega_2,\omega_4}
$$

$$
A \setminus B = {\omega_1,\omega_5}
$$

---

✅ **Interpretation**

* The union gives **all outcomes**, so $A \cup B = \Omega$.
* The events share **only one element**, $\omega_3$.
* The difference operations remove elements belonging to both sets.

---

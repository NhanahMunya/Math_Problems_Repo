# Problem 1 — Coin × Coin

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-discovering--formalism-blue)
![Method](https://img.shields.io/badge/method-sample--space--and--events-orange)

---

## 🎯 Objective

Analyse the sample space of two coin tosses using a graphical grid representation. Mark events as subsets of the sample space and interpret graphically represented events as precise verbal statements.

---

## 📐 Sample Space

The experiment consists of two independent coin tosses. Each toss produces either **H** (heads) or **T** (tails). Since order matters — the first and second toss are distinct stages — each elementary outcome is an ordered pair $(i, j)$ where $i$ is the result of the first toss and $j$ is the result of the second toss.

The full sample space is:

$$\Omega = \{(H,H),\ (H,T),\ (T,H),\ (T,T)\}, \quad |\Omega| = 4$$

In the grid representation, **rows correspond to the first toss** and **columns correspond to the second toss**. Each cell represents exactly one elementary outcome:

```
         H      T        ← second toss
H     (H,H)  (H,T)
T     (T,H)  (T,T)
↑
first toss
```

An **event** is any subset of $\Omega$ — a collection of outcomes for which a given statement is true. Marking a cell with `X` means that outcome belongs to the event; `.` means it does not.

---

## ✅ Part A — Marking Events

---

### Statement 1 — Exactly one head

**Reasoning:** An outcome contains exactly one head when precisely one of the two tosses shows H and the other shows T. We examine each cell:

- $(H,H)$: two heads — does **not** satisfy the statement
- $(H,T)$: one head (first toss), one tail (second toss) — **satisfies**
- $(T,H)$: one tail (first toss), one head (second toss) — **satisfies**
- $(T,T)$: zero heads — does **not** satisfy the statement

```
      H   T
H     .   X
T     X   .
```

The event is $A = \{(H,T),\ (T,H)\}$.

---

### Statement 2 — Both tosses are the same

**Reasoning:** Both tosses are the same when either both show H or both show T — that is, when the two results are equal. We examine each cell:

- $(H,H)$: both heads — **satisfies**
- $(H,T)$: H and T — different results — does **not** satisfy
- $(T,H)$: T and H — different results — does **not** satisfy
- $(T,T)$: both tails — **satisfies**

```
      H   T
H     X   .
T     .   X
```

The event is $B = \{(H,H),\ (T,T)\}$. Notice this is the **main diagonal** of the grid — a geometric feature that reflects the equality condition $i = j$.

---

### Statement 3 — At least one head

**Reasoning:** "At least one head" means one or two heads — equivalently, the outcome is **not** $(T,T)$ (the only outcome with zero heads). We examine each cell:

- $(H,H)$: two heads — **satisfies**
- $(H,T)$: one head — **satisfies**
- $(T,H)$: one head — **satisfies**
- $(T,T)$: zero heads — does **not** satisfy

```
      H   T
H     X   X
T     X   .
```

The event is $C = \{(H,H),\ (H,T),\ (T,H)\}$.

> **Complement observation:** $C^c = \{(T,T)\}$ — the only outcome with no heads. It is easier to identify the complement (zero heads) and subtract it from $\Omega$:
> $$C = \Omega \setminus \{(T,T)\}$$

---

### Statement 4 — The first toss is tails

**Reasoning:** The first toss result is determined by the **row** of the grid. The statement is satisfied exactly when the first toss shows T — that is, for all outcomes in the bottom row, regardless of what the second toss shows.

- $(H,H)$: first toss is H — does **not** satisfy
- $(H,T)$: first toss is H — does **not** satisfy
- $(T,H)$: first toss is T — **satisfies**
- $(T,T)$: first toss is T — **satisfies**

```
      H   T
H     .   .
T     X   X
```

The event is $D = \{(T,H),\ (T,T)\}$ — the entire bottom row.

---

### Statement 5 — The second toss is heads

**Reasoning:** The second toss result is determined by the **column** of the grid. The statement is satisfied exactly when the second toss shows H — that is, for all outcomes in the left column, regardless of what the first toss shows.

- $(H,H)$: second toss is H — **satisfies**
- $(H,T)$: second toss is T — does **not** satisfy
- $(T,H)$: second toss is H — **satisfies**
- $(T,T)$: second toss is T — does **not** satisfy

```
      H   T
H     X   .
T     X   .
```

The event is $E = \{(H,H),\ (T,H)\}$ — the entire left column.

---

## ✅ Part B — Interpreting Graphical Events

---

### Case 1

```
      H   T
H     X   X
T     .   .
```

**Interpretation:** The marked cells are $(H,H)$ and $(H,T)$ — the entire top row. In both outcomes the first toss shows H, while the second toss can be anything.

> **Event: the first toss is heads.**

The row of the grid encodes the result of the first toss. Marking the entire top row means: no matter what the second toss produces, the first toss must be H. The second toss is unconstrained, which is why both cells in the row are marked.

This event is the complement of Statement 4 above: $D^c = \{(H,H),\ (H,T)\}$.

---

### Case 2

```
      H   T
H     .   X
T     X   .
```

**Interpretation:** The marked cells are $(H,T)$ and $(T,H)$ — the two off-diagonal positions. In both outcomes exactly one toss shows H and the other shows T.

> **Event: exactly one head** (the two tosses give different results).

This is the same event as Statement 1 above: $A = \{(H,T),\ (T,H)\}$.

Notice that this event corresponds to the **anti-diagonal** of the grid — the positions where $i \neq j$. Geometrically, it is the complement of Statement 2 (both tosses the same), which occupies the main diagonal.

---

## 💡 Key Insights

- **Rows encode the first toss, columns encode the second toss.** An event that constrains only the first toss fills entire rows; an event constraining only the second toss fills entire columns.

- **Diagonal structure reveals equality.** The main diagonal $\{(H,H),(T,T)\}$ corresponds to both tosses being equal; the anti-diagonal $\{(H,T),(T,H)\}$ corresponds to them being different.

- **Complement rule simplifies "at least" events.** Instead of listing all outcomes satisfying "at least one head," it is easier to identify the single outcome that fails ($(T,T)$) and take the complement.

- **Every event is a subset of $\Omega$.** The grid makes this visible: an event is simply a pattern of marked cells inside the $2 \times 2$ table. Set operations (union, intersection, complement) correspond to combining or subtracting these patterns.

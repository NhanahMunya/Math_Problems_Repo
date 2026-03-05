# Task 2 – Electrical Circuit Reliability

## Problem

Element **a₁** is connected **in series** with a block consisting of two elements **a₂** and **a₃** connected **in parallel**.

Let:

* **A₁** — event that element **a₁** is functional at time *t*
* **A₂** — event that element **a₂** is functional at time *t*
* **A₃** — event that element **a₃** is functional at time *t*

Describe the event **A**:

> "The current flows through the circuit without interruption during time *t*."

Use the operations:

* union **∪**
* intersection **∩**

---

# Step 1 — Understand the circuit

### Series connection

For components connected **in series**, **all components must work**.

So the condition for the first element is simply:

A₁

If **a₁ fails**, the entire circuit stops.

---

### Parallel connection

For components connected **in parallel**, the current flows if **at least one component works**.

For elements **a₂** and **a₃**:

A₂ ∪ A₃

---

# Step 2 — Combine the conditions

The circuit consists of:

* **a₁ in series**
* a **parallel block (a₂ and a₃)**

For the circuit to work:

* **a₁ must work**
* **and** at least one of **a₂ or a₃** must work

So we combine them using intersection.

A = A₁ ∩ (A₂ ∪ A₃)

---

# Final Result

The event describing uninterrupted current flow is

**A = A₁ ∩ (A₂ ∪ A₃)**

---

# Interpretation

The circuit works if:

| Condition      | Meaning                             |
| -------------- | ----------------------------------- |
| A₁             | element a₁ works                    |
| A₂ ∪ A₃        | at least one parallel element works |
| A₁ ∩ (A₂ ∪ A₃) | the whole circuit works             |

---

💡 **Quick intuition**

```
a1 ----+---- a2
       |
       +---- a3
```

* If **a₁ fails → circuit stops**
* If **a₁ works → current flows through a₂ or a₃**

---

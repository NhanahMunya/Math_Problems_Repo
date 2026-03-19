# Task 1 — Recognising Counting Models

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-combinatorics-blue)
![Method](https://img.shields.io/badge/method-model--identification-orange)

---

## 🎯 Objective

For each situation, identify the correct combinatorial counting model by applying a systematic set of questions.

---

## 📐 Decision Framework

Before choosing a model, answer these four questions:

| Question | Determines |
|:---|:---|
| Are we using **all** objects or only **some**? | Permutation vs Selection |
| Does **order** matter? | Permutation/k-Permutation vs Combination |
| Is **repetition** allowed? | Sequence vs k-Permutation |
| Are some objects **identical**? | Permutation with repeated elements |

### Decision Tree

```
START

Are we using ALL objects?

 ├─ YES
 │    Are objects arranged in a circle?
 │    ├─ YES → Circular permutation
 │    └─ NO
 │         Are some objects identical?
 │         ├─ YES → Permutation with repeated elements
 │         └─ NO  → Permutation
 │
 └─ NO (only SOME objects)
      Does order matter?
      ├─ NO  → Combination
      └─ YES
           Is repetition allowed?
           ├─ YES → Sequence with repetition
           └─ NO  → k-Permutation
```

---

## 📚 General Formulas

| Model | Formula | $n$ means | $k$ means |
|:---|:---:|:---|:---|
| Permutation | $n!$ | total objects | — (use all) |
| Combination | $\dfrac{n!}{k!(n-k)!}$ | total objects | chosen, order ignored |
| k-Permutation | $\dfrac{n!}{(n-k)!}$ | total objects | chosen, order matters |
| Sequence with repetition | $n^k$ | options per position | number of positions |
| Permutation with repeats | $\dfrac{n!}{n_1! \cdots n_r!}$ | total objects | sizes of identical groups |
| Circular permutation | $(n-1)!$ | total objects | — (use all) |

> **Key relationship:** A k-Permutation is a Combination multiplied by $k!$ — the only difference is whether order matters:
> $$P(n,k) = \binom{n}{k} \times k!$$

---

## ✅ Solutions

### Problem 1 — Arranging 7 students in a line

| Question | Answer |
|:---|:---:|
| All or some objects? | All 7 |
| Circular arrangement? | No |
| Identical objects? | No |

**Model: Permutation**

**General formula:**

$$P_n = n!$$

- $n$ = total number of distinct objects being arranged
- $n!$ = $n \times (n-1) \times \cdots \times 1$ — each position reduces choices by 1 since no repetition is allowed

**Applied:** $n = 7$

$$P_7 = 7! = 7 \times 6 \times 5 \times 4 \times 3 \times 2 \times 1 = 5040$$

> All students are arranged in a line, order matters (position is distinct), no student appears twice, all are distinguishable.

---

### Problem 2 — Choosing 4 members of a committee from 12 people

| Question | Answer |
|:---|:---:|
| All or some objects? | Some (4 of 12) |
| Order matters? | No |
| Repetition allowed? | No |

**Model: Combination**

**General formula:**

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

- $n$ = total number of objects to choose from
- $k$ = how many are being chosen
- $k!$ = divides out the orderings of the chosen group (order doesn't matter)
- $(n-k)!$ = cancels the unchosen objects from $n!$

**Applied:** $n = 12$, $k = 4$

$$\binom{12}{4} = \frac{12!}{4! \cdot 8!} = \frac{12 \times 11 \times 10 \times 9}{4 \times 3 \times 2 \times 1} = \frac{11{,}880}{24} = 495$$

> A committee has no internal ranking — choosing {A, B, C, D} is the same as choosing {D, C, B, A}, so we divide out the $k! = 4!$ orderings.

---

### Problem 3 — Assigning gold, silver, and bronze medals among 15 athletes

| Question | Answer |
|:---|:---:|
| All or some objects? | Some (3 of 15) |
| Order matters? | Yes |
| Repetition allowed? | No |

**Model: k-Permutation**

**General formula:**

$$P(n,k) = \frac{n!}{(n-k)!}$$

- $n$ = total number of objects
- $k$ = how many are being selected
- $(n-k)!$ = cancels the unselected objects from $n!$
- No $k!$ in the denominator because order **does** matter here

**Applied:** $n = 15$, $k = 3$

$$P(15,3) = \frac{15!}{12!} = 15 \times 14 \times 13 = 2{,}730$$

> The medals are distinct — gold $\neq$ silver $\neq$ bronze. Assigning gold to athlete A and silver to B is different from silver to A and gold to B.

---

### Problem 4 — Forming a 6-digit PIN code

| Question | Answer |
|:---|:---:|
| All or some objects? | Some (6 digits from 0–9) |
| Order matters? | Yes |
| Repetition allowed? | Yes |

**Model: Sequence with repetition**

**General formula:**

$$n^k$$

- $n$ = number of symbols available at each position
- $k$ = number of positions (length of the sequence)
- Each of the $k$ positions independently picks from $n$ options — repetition means choices never reduce

**Applied:** $n = 10$ digits, $k = 6$ positions

$$10^6 = 1{,}000{,}000$$

> Each position independently picks from $\{0,1,\ldots,9\}$. The same digit can appear more than once (e.g. 112233 is valid).

---

### Problem 5 — Arranging the letters of the word BANANA

| Question | Answer |
|:---|:---:|
| All or some objects? | All 6 letters |
| Circular arrangement? | No |
| Identical objects? | Yes |

**BANANA** contains:
- **B** — 1 time
- **A** — 3 times
- **N** — 2 times

**Model: Permutation with repeated elements**

**General formula:**

$$\frac{n!}{n_1! \cdot n_2! \cdots n_r!}$$

- $n$ = total number of objects
- $n_1, n_2, \ldots, n_r$ = count of each group of identical objects
- Each $n_i!$ divides out the overcounting from swapping identical objects
- Always satisfied: $n_1 + n_2 + \cdots + n_r = n$

**Applied:** $n = 6$, $n_1 = 1$ (B), $n_2 = 3$ (A), $n_3 = 2$ (N)

$$\frac{6!}{1! \cdot 3! \cdot 2!} = \frac{720}{1 \times 6 \times 2} = \frac{720}{12} = 60$$

> Using $6! = 720$ would overcount — swapping the 3 identical A's gives $3! = 6$ copies of each word, and swapping the 2 N's gives $2! = 2$ copies. Dividing both out gives the true count.

---

### Problem 6 — Seating 6 people around a round table

| Question | Answer |
|:---|:---:|
| All or some objects? | All 6 |
| Circular arrangement? | Yes |
| Identical objects? | No |

**Model: Circular permutation**

**General formula:**

$$(n-1)!$$

- $n$ = number of objects arranged in a circle
- We subtract 1 because one person is fixed to eliminate identical rotations
- Relationship to regular permutation: $\dfrac{n!}{n} = (n-1)!$ — divide by $n$ since there are $n$ identical rotations of any arrangement

**Applied:** $n = 6$

$$(6-1)! = 5! = 120$$

> In a line, 6 people give $6! = 720$ arrangements. In a circle, rotating everyone one seat produces the same arrangement — there are 6 such rotations, so $\frac{720}{6} = 120$.

---

## 📊 Summary Table

| Problem | Model | $n$ | $k$ | Formula | Result |
|:---|:---:|:---:|:---:|:---:|:---:|
| 7 students in a line | Permutation | $7$ | — | $7!$ | $5{,}040$ |
| Committee of 4 from 12 | Combination | $12$ | $4$ | $\binom{12}{4}$ | $495$ |
| 3 medals among 15 athletes | k-Permutation | $15$ | $3$ | $P(15,3)$ | $2{,}730$ |
| 6-digit PIN code | Sequence with repetition | $10$ | $6$ | $10^6$ | $1{,}000{,}000$ |
| Letters of BANANA | Permutation with repeats | $6$ | — | $\frac{6!}{1!\cdot3!\cdot2!}$ | $60$ |
| 6 people at round table | Circular permutation | $6$ | — | $5!$ | $120$ |

---

## 💡 Key Insights

- **Combination vs k-Permutation** — both select some objects, but k-Permutation cares about order (medals), Combination does not (committees):

$$P(n,k) = \binom{n}{k} \times k!$$

- **Permutation vs Permutation with repeated elements** — both arrange all objects, but identical objects reduce the count by dividing out repetitions.

- **Circular vs Linear permutation** — circular arrangements divide out $n$ rotations:

$$\text{Circular} = \frac{\text{Linear}}{n} = \frac{n!}{n} = (n-1)!$$

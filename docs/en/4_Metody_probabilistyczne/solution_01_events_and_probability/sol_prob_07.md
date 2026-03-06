# Task 7

## Problem

On a communication line, two types of signals are transmitted in the form of code combinations **111** or **000** with **a priori probabilities of 0.65 and 0.35 respectively**.

The signals are subject to random interference, as a result of which the symbol **1 can be received as 0 with a probability of 0.2**, and with the same probability, the symbol **0 can be received as 1**.

We assume that symbols **1 and 0 are subject to interference independently of each other**.

Calculate the probability of receiving the signal:

1. **111**
2. **000**
3. **010**

---

# Step 1 – Transmission probabilities

Given interference:

| Transmitted | Received             | Probability |
| ----------- | -------------------- | ----------- |
| 1 → 1       | correct transmission | 0.8         |
| 1 → 0       | error                | 0.2         |
| 0 → 0       | correct transmission | 0.8         |
| 0 → 1       | error                | 0.2         |

Symbols are **independent**, so probabilities multiply.

Also given:

P(transmit 111) = **0.65**
P(transmit 000) = **0.35**

---

# 1. Probability of receiving 111

There are **two ways** this can happen.

### Case 1 – 111 was transmitted

Each 1 must stay 1.

P(111 | transmit 111) = 0.8 × 0.8 × 0.8 = 0.512

Contribution:

0.65 × 0.512 = **0.3328**

---

### Case 2 – 000 was transmitted

Each 0 must flip to 1.

P(111 | transmit 000) = 0.2 × 0.2 × 0.2 = 0.008

Contribution:

0.35 × 0.008 = **0.0028**

---

### Total probability

P(receive 111) = 0.3328 + 0.0028

P(receive 111) = **0.3356**

---

# 2. Probability of receiving 000

Again consider both transmissions.

### Case 1 – 111 transmitted

Each 1 must flip to 0.

P(000 | transmit 111) = 0.2³ = 0.008

Contribution:

0.65 × 0.008 = **0.0052**

---

### Case 2 – 000 transmitted

Each 0 must stay 0.

P(000 | transmit 000) = 0.8³ = 0.512

Contribution:

0.35 × 0.512 = **0.1792**

---

### Total probability

P(receive 000) = 0.0052 + 0.1792

P(receive 000) = **0.1844**

---

# 3. Probability of receiving 010

Again evaluate both transmission possibilities.

---

### Case 1 – 111 transmitted

To receive **010**:

1 → 0
1 → 1
1 → 0

Probability:

0.2 × 0.8 × 0.2 = 0.032

Contribution:

0.65 × 0.032 = **0.0208**

---

### Case 2 – 000 transmitted

To receive **010**:

0 → 0
0 → 1
0 → 0

Probability:

0.8 × 0.2 × 0.8 = 0.128

Contribution:

0.35 × 0.128 = **0.0448**

---

### Total probability

P(receive 010) = 0.0208 + 0.0448

P(receive 010) = **0.0656**

---

# Final Results

| Received signal | Probability |
| --------------- | ----------- |
| 111             | **0.3356**  |
| 000             | **0.1844**  |
| 010             | **0.0656**  |

---

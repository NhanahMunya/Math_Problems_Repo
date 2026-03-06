# 📡 Communication Channel Signal Transmission Analysis

![Math](https://img.shields.io/badge/Math-Probability-blue)
![Topic](https://img.shields.io/badge/Topic-Signal_Processing-red)
![Difficulty](https://img.shields.io/badge/Difficulty-Advanced-orange)
![Status](https://img.shields.io/badge/Status-Complete-success)

> **Analyzing signal transmission probabilities through a noisy communication channel with interference**

---

## 📋 Problem Statement

Only **3 types** of letter sequences are transmitted via a communication channel:

- **AAAA** with probability `0.4`
- **BBBB** with probability `0.3`
- **CCCC** with probability `0.3`

These letters (signals) are subject to **independent random interference** (errors), as a result of which, for example, letter **A** can be received as **B** or **C**.

### Transmission Error Table

The probabilities of correct transmission or error for a **single letter** are:

| Transmitted ↓ / Received → | **A** | **B** | **C** |
|:-------------------------:|:-----:|:-----:|:-----:|
| **A** | 0.8 | 0.1 | 0.1 |
| **B** | 0.1 | 0.8 | 0.1 |
| **C** | 0.1 | 0.1 | 0.8 |

### Questions

Find the probability of receiving the signal at the output:

1. **AAAA**
2. **ACAA**

---

## 🔍 Understanding the Problem

### Key Concepts

1. **3 possible transmitted sequences:** AAAA, BBBB, CCCC
2. **Prior probabilities:** P(AAAA sent) = 0.4, P(BBBB sent) = 0.3, P(CCCC sent) = 0.3
3. **Independent errors:** Each letter is transmitted independently
4. **Symmetric error model:** Each letter has 80% correct transmission, 10% error to each other letter

### Important Notes

- 📌 Each position in the sequence is transmitted **independently**
- 📌 We use the **Law of Total Probability** over all possible transmitted sequences
- 📌 Each letter's transmission is **independent** of other letters in the sequence

---

## 🎯 Solution

### Question 1: Find P(Receive AAAA)

To receive **AAAA**, we consider all possible transmitted sequences:

```
P(Receive AAAA) = P(Receive AAAA | Sent AAAA) × P(Sent AAAA)
                + P(Receive AAAA | Sent BBBB) × P(Sent BBBB)
                + P(Receive AAAA | Sent CCCC) × P(Sent CCCC)
```

---

#### Case 1: Sent AAAA → Received AAAA

**Probability sent:** `0.4`

**Transmission:** Each of the 4 A's must be received as A

```
P(Receive AAAA | Sent AAAA) = P(A→A) × P(A→A) × P(A→A) × P(A→A)
                             = 0.8 × 0.8 × 0.8 × 0.8
                             = (0.8)⁴
                             = 0.4096
```

**Contribution:** `0.4 × 0.4096 = 0.16384`

---

#### Case 2: Sent BBBB → Received AAAA

**Probability sent:** `0.3`

**Transmission:** Each of the 4 B's must be received as A

```
P(Receive AAAA | Sent BBBB) = P(B→A) × P(B→A) × P(B→A) × P(B→A)
                             = 0.1 × 0.1 × 0.1 × 0.1
                             = (0.1)⁴
                             = 0.0001
```

**Contribution:** `0.3 × 0.0001 = 0.00003`

---

#### Case 3: Sent CCCC → Received AAAA

**Probability sent:** `0.3`

**Transmission:** Each of the 4 C's must be received as A

```
P(Receive AAAA | Sent CCCC) = P(C→A) × P(C→A) × P(C→A) × P(C→A)
                             = 0.1 × 0.1 × 0.1 × 0.1
                             = (0.1)⁴
                             = 0.0001
```

**Contribution:** `0.3 × 0.0001 = 0.00003`

---

#### Total Probability for AAAA

```
P(Receive AAAA) = 0.16384 + 0.00003 + 0.00003
                = 0.16390
```

### ✅ **Answer 1: P(Receive AAAA) = 0.1639 ≈ 16.39%**

---

### Question 2: Find P(Receive ACAA)

To receive **ACAA**, we again consider all possible transmitted sequences:

```
P(Receive ACAA) = P(Receive ACAA | Sent AAAA) × P(Sent AAAA)
                + P(Receive ACAA | Sent BBBB) × P(Sent BBBB)
                + P(Receive ACAA | Sent CCCC) × P(Sent CCCC)
```

---

#### Case 1: Sent AAAA → Received ACAA

**Probability sent:** `0.4`

**Transmission needed:**
- Position 1: A → A (probability = 0.8)
- Position 2: A → C (probability = 0.1)
- Position 3: A → A (probability = 0.8)
- Position 4: A → A (probability = 0.8)

```
P(Receive ACAA | Sent AAAA) = 0.8 × 0.1 × 0.8 × 0.8
                             = 0.0512
```

**Contribution:** `0.4 × 0.0512 = 0.02048`

---

#### Case 2: Sent BBBB → Received ACAA

**Probability sent:** `0.3`

**Transmission needed:**
- Position 1: B → A (probability = 0.1)
- Position 2: B → C (probability = 0.1)
- Position 3: B → A (probability = 0.1)
- Position 4: B → A (probability = 0.1)

```
P(Receive ACAA | Sent BBBB) = 0.1 × 0.1 × 0.1 × 0.1
                             = 0.0001
```

**Contribution:** `0.3 × 0.0001 = 0.00003`

---

#### Case 3: Sent CCCC → Received ACAA

**Probability sent:** `0.3`

**Transmission needed:**
- Position 1: C → A (probability = 0.1)
- Position 2: C → C (probability = 0.8)
- Position 3: C → A (probability = 0.1)
- Position 4: C → A (probability = 0.1)

```
P(Receive ACAA | Sent CCCC) = 0.1 × 0.8 × 0.1 × 0.1
                             = 0.0008
```

**Contribution:** `0.3 × 0.0008 = 0.00024`

---

#### Total Probability for ACAA

```
P(Receive ACAA) = 0.02048 + 0.00003 + 0.00024
                = 0.02075
```

### ✅ **Answer 2: P(Receive ACAA) = 0.02075 ≈ 2.075%**

---

## 📊 Summary Table

| Received Signal | Probability | Percentage |
|:---------------:|:-----------:|:----------:|
| **AAAA** | **0.1639** | **16.39%** |
| **ACAA** | **0.02075** | **2.075%** |

---

## 💡 Detailed Breakdown

### For AAAA (All same letters - no errors visible)

| Sent | P(Sent) | P(Receive AAAA \| Sent) | Calculation | Contribution |
|:----:|:-------:|:-----------------------:|-------------|:------------:|
| AAAA | 0.4 | (0.8)⁴ = 0.4096 | 0.4 × 0.4096 | **0.16384** |
| BBBB | 0.3 | (0.1)⁴ = 0.0001 | 0.3 × 0.0001 | 0.00003 |
| CCCC | 0.3 | (0.1)⁴ = 0.0001 | 0.3 × 0.0001 | 0.00003 |
| | | | **Total** | **0.16390** |

> 💡 **Insight:** The dominant contribution comes from sending AAAA (0.16384), with negligible contributions from BBBB and CCCC.

---

### For ACAA (Contains an error)

| Sent | P(Sent) | Position 1 | Position 2 | Position 3 | Position 4 | P(ACAA\|Sent) | Contribution |
|:----:|:-------:|:----------:|:----------:|:----------:|:----------:|:-------------:|:------------:|
| AAAA | 0.4 | A→A: 0.8 | A→C: 0.1 | A→A: 0.8 | A→A: 0.8 | 0.0512 | **0.02048** |
| BBBB | 0.3 | B→A: 0.1 | B→C: 0.1 | B→A: 0.1 | B→A: 0.1 | 0.0001 | 0.00003 |
| CCCC | 0.3 | C→A: 0.1 | C→C: 0.8 | C→A: 0.1 | C→A: 0.1 | 0.0008 | 0.00024 |
| | | | | | | **Total** | **0.02075** |

> 💡 **Insight:** Again, AAAA dominates (0.02048). The sequence CCCC contributes slightly more than BBBB because position 2 correctly transmits C→C.

---

## 🧮 Understanding the Mathematics

### Law of Total Probability

For any received sequence **R**:

```
P(R) = Σ P(R | Tᵢ) × P(Tᵢ)
```

Where:
- **Tᵢ** = transmitted sequence i (AAAA, BBBB, or CCCC)
- **P(Tᵢ)** = prior probability of transmitting sequence i
- **P(R | Tᵢ)** = probability of receiving R given Tᵢ was sent

---

### Independent Transmission

For a 4-letter sequence, if each letter is transmitted independently:

```
P(Receive r₁r₂r₃r₄ | Sent s₁s₂s₃s₄) = P(s₁→r₁) × P(s₂→r₂) × P(s₃→r₃) × P(s₄→r₄)
```

---

### Error Model Interpretation

| Transmission | Meaning | Probability |
|:------------:|---------|:-----------:|
| **A → A** | Correct transmission | 0.8 |
| **A → B** | Error (A becomes B) | 0.1 |
| **A → C** | Error (A becomes C) | 0.1 |

Each row sums to 1.0 (total probability).

---

## 📈 Probability Comparison

### Visualization of Contributions

**For AAAA:**
```
AAAA sent: ████████████████████████████████████████ 0.16384 (99.96%)
BBBB sent: ▏ 0.00003 (0.02%)
CCCC sent: ▏ 0.00003 (0.02%)
```

**For ACAA:**
```
AAAA sent: ████████████████████████████████████████ 0.02048 (98.70%)
CCCC sent: █ 0.00024 (1.16%)
BBBB sent: ▏ 0.00003 (0.14%)
```

> 📊 **Key Observation:** In both cases, the AAAA transmission dominates because it has the highest prior probability (0.4) and reasonable transmission probabilities.

---

## 🎯 Key Insights

### 1. Why is AAAA more likely than ACAA?

**AAAA (0.1639) vs ACAA (0.02075)**

- **AAAA:** All four letters are correctly transmitted from AAAA → Each has 0.8 probability → (0.8)⁴ = 0.4096
- **ACAA:** Three correct, one error from AAAA → 0.8³ × 0.1 = 0.0512

The difference: `0.4096 / 0.0512 = 8`, so AAAA is **8 times** more likely than ACAA (when both come from AAAA transmission).

### 2. Effect of Prior Probabilities

Even though BBBB and CCCC can produce AAAA or ACAA, their contributions are minimal because:
- Lower prior probabilities (0.3 each vs 0.4 for AAAA)
- Multiple errors needed (all four letters must be wrong)

### 3. Error Symmetry

The error model is **symmetric**:
- Any letter has 80% chance of correct transmission
- Any letter has 10% chance of error to each other letter
- This symmetry simplifies calculations

---

## 🧪 Verification

### Check: Do probabilities make sense?

**Expected behavior:**
- ✅ P(AAAA) > P(ACAA) — Fewer errors means higher probability
- ✅ Both probabilities < 1 — Valid probabilities
- ✅ Dominant contribution from AAAA sent — Highest prior probability

**Sanity check:**
```
If all transmissions were perfect (no errors):
P(Receive AAAA) would be exactly P(Sent AAAA) = 0.4

With errors:
P(Receive AAAA) = 0.1639 < 0.4 ✓
(Some AAAA get corrupted to other sequences)
```

---

## 🔬 Extended Analysis

### What if we received BBBB or CCCC?

**For BBBB:**
```
P(Receive BBBB) = 0.4 × (0.1)⁴ + 0.3 × (0.8)⁴ + 0.3 × (0.1)⁴
                = 0.4 × 0.0001 + 0.3 × 0.4096 + 0.3 × 0.0001
                = 0.00004 + 0.12288 + 0.00003
                = 0.12295
```

**For CCCC:**
```
P(Receive CCCC) = 0.4 × (0.1)⁴ + 0.3 × (0.1)⁴ + 0.3 × (0.8)⁴
                = 0.4 × 0.0001 + 0.3 × 0.0001 + 0.3 × 0.4096
                = 0.00004 + 0.00003 + 0.12288
                = 0.12295
```

| Received | Probability | Rank |
|:--------:|:-----------:|:----:|
| AAAA | 0.1639 | 1st |
| BBBB | 0.1230 | 2nd |
| CCCC | 0.1230 | 2nd |
| ACAA | 0.0208 | Lower |

---

## 📚 General Formula

For a received sequence **r₁r₂r₃r₄**:

```
P(r₁r₂r₃r₄) = Σ P(sent sᵢ) × ∏ P(sᵢⱼ → rⱼ)
               i           j=1 to 4
```

Where:
- **sᵢ** = transmitted sequence i (AAAA, BBBB, or CCCC)
- **sᵢⱼ** = j-th letter of sequence i
- **rⱼ** = j-th letter of received sequence
- **P(sᵢⱼ → rⱼ)** = transmission probability from error table

---

## 🎓 Key Concepts Summary

| Concept | Application |
|---------|-------------|
| **Law of Total Probability** | Sum over all possible transmitted sequences |
| **Independence** | Multiply probabilities for each letter position |
| **Conditional Probability** | P(Receive \| Sent) from error table |
| **Prior Probabilities** | P(Sent AAAA) = 0.4, P(Sent BBBB) = 0.3, P(Sent CCCC) = 0.3 |

---

## 🧮 Step-by-Step Calculation Template

For any received sequence **R**:

```
Step 1: List all possible sent sequences (AAAA, BBBB, CCCC)

Step 2: For each sent sequence S:
   a) Find P(Sent S) — the prior probability
   b) Calculate P(Receive R | Sent S):
      - Multiply transmission probabilities for each position
      - Use the error table
   c) Calculate contribution: P(Sent S) × P(R | S)

Step 3: Sum all contributions

Step 4: Final answer = Σ contributions
```

---

## 💼 Real-World Applications

This model applies to:

- 📡 **Digital Communications** - Error correction codes
- 🛰️ **Satellite Transmission** - Signal degradation
- 📞 **Telephone Networks** - Voice transmission errors
- 💾 **Data Storage** - Bit flips in memory
- 🔐 **Cryptography** - Channel noise in secure communication
- 🌐 **Internet Protocols** - Packet corruption

---

## 🎯 Final Answers

| Question | Received Signal | Probability | Percentage |
|:--------:|:---------------:|:-----------:|:----------:|
| **1** | **AAAA** | **0.1639** | **16.39%** |
| **2** | **ACAA** | **0.02075** | **2.075%** |

---


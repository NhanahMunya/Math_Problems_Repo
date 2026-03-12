# Task 5 — Buffon's Needle Experiment

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-continuous--sample--space-blue)
![Method](https://img.shields.io/badge/method-geometric--probability-orange)

---

## 🎯 Objective

Describe the sample space of Buffon's Needle experiment, identify the parameters that determine each outcome, and explain why this sample space is continuous — unlike those in the previous tasks.

---

## 📐 Setup

A needle of length $L$ is thrown randomly onto a floor with equally spaced parallel lines. The distance between neighbouring lines is $d$.

We assume:

$$
L \leq d
$$

This ensures the needle can cross **at most one line** per throw, simplifying the analysis.

---

## 🖼️ Visualising the Experiment

```
        |               |               |
        |               |               |
        |       /       |               |
        |      / ← needle               |
        |     /         |               |
        |               |               |
        |←——— d ————————|               |
              ↑
         x = distance from
         needle's center
         to nearest line
```

- The needle lands at some position and angle each throw.
- Two numbers fully describe every possible outcome: $x$ and $\theta$.

---

## ✅ Solutions

### 1. Description of the Sample Space Ω

The sample space Ω consists of all possible outcomes of a single needle throw. Each outcome is fully described by two continuous parameters (see Section 2 below), so Ω is represented as a **rectangle** in the (x, θ) plane:

```
Ω = { (x, θ) | x ∈ [0, d/2], θ ∈ [0, π/2] }
```

---


### 2. Parameters That Determine the Outcome

Each single throw of the needle is completely determined by exactly **two parameters**:

| Parameter | Symbol | Description | Range |
|:---:|:---:|:---|:---:|
| Distance to nearest line | $x$ | The distance from the **centre of the needle** to the **nearest parallel line** | $x \in \left[0,\ \dfrac{d}{2}\right]$ |
| Orientation angle | $\theta$ | The **acute angle** between the needle and the parallel lines | $\theta \in \left[0,\ \dfrac{\pi}{2}\right]$ |

---

### 3. Elementary Outcome

An **elementary outcome** is an ordered pair:

$$
\omega = (x,\ \theta)
$$

where:

- $x \in \left[0,\ \dfrac{d}{2}\right]$ is the distance from the needle's centre to the nearest line,
- $\theta \in \left[0,\ \dfrac{\pi}{2}\right]$ is the angle between the needle and the lines.

**Example elementary outcomes:**

$$
\omega_1 = \left(\frac{d}{4},\ \frac{\pi}{6}\right) \quad \text{— needle centre at } \tfrac{d}{4} \text{ from nearest line, tilted at } 30°
$$

$$
\omega_2 = \left(0,\ \frac{\pi}{2}\right) \quad \text{— needle centre directly on a line, perpendicular to lines}
$$

---

### 4. Sample Space as a Set

Using symmetry — the left/right and up/down halves of the throw are mirror images — we restrict to:

```
Ω = [0, d/2] × [0, π/2]
```
This is a **rectangle** in the $(x, \theta)$ plane with:

- width $= \dfrac{d}{2}$
- height $= \dfrac{\pi}{2}$
- area $= \dfrac{d}{2} \cdot \dfrac{\pi}{2} = \dfrac{\pi d}{4}$

Every point inside this rectangle corresponds to exactly one possible throw of the needle.

---

### 5. Why Is This Sample Space Continuous?

In all previous tasks, the sample space was **discrete** — it contained a finite, countable number of elementary outcomes that could be listed:

| Task | Sample Space | Type |
|:---:|:---:|:---:|
| Coin toss ($n=3$) | $\{HHH, HHT, \ldots, TTT\}$ | Discrete — 8 outcomes |
| Die roll ($n=2$) | $\{(1,1), (1,2), \ldots, (6,6)\}$ | Discrete — 36 outcomes |
| Weather ($n=7$) | All 7-tuples of $\{S, C, R\}$ | Discrete — 2,187 outcomes |
| **Buffon's Needle** | $\left[0, \frac{d}{2}\right] \times \left[0, \frac{\pi}{2}\right]$ | **Continuous — uncountably infinite** |

In Buffon's experiment, both $x$ and $\theta$ are **real numbers** chosen from continuous intervals. Between any two outcomes, there are **infinitely many** other possible outcomes. It is therefore impossible to list or count the elementary outcomes.

> **Key distinction:** In a discrete sample space, probabilities are assigned to **individual outcomes**. In a continuous sample space, individual outcomes have probability zero — instead, probabilities are assigned to **regions** (subsets) of $\Omega$, computed as areas or integrals.

---

## 💡 Key Insight

Buffon's Needle introduces a fundamentally new type of sample space. Rather than counting outcomes, we reason **geometrically**:

- The full sample space $\Omega$ is a rectangle of area $\dfrac{\pi d}{4}$.
- An event $A$ corresponds to a **region inside this rectangle**.
- The probability of $A$ is the **ratio of areas**:

$$
P(A) = \frac{\text{area of region } A}{\text{area of } \Omega} = \frac{\text{area of } A}{\dfrac{\pi d}{4}}
$$

This geometric approach to probability will be used directly in **Task 10**.

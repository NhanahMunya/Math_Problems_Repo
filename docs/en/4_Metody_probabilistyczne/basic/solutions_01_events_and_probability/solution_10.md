# Task 10 — Events and Probabilities in Buffon's Needle Experiment

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Topic](https://img.shields.io/badge/topic-continuous--probability-blue)
![Method](https://img.shields.io/badge/method-geometric--probability--and--integration-orange)

---

## 🎯 Objective

Using the continuous sample space $\Omega$ from Task 5, compute probabilities of events in Buffon's Needle experiment using geometric probability — the ratio of areas.

---

## 📐 Setup

From **Task 5**, the sample space is:

```
Ω = { (x, θ) | x ∈ [0, d/2], θ ∈ [0, π/2] }
```

A needle of length $L \leq d$ is thrown randomly. The two parameters are:

- $x \in \left[0, \frac{d}{2}\right]$ — distance from needle's centre to nearest line
- $\theta \in \left[0, \frac{\pi}{2}\right]$ — angle between needle and the lines

Both are **independent** and **uniformly distributed**.

**Area of $\Omega$:**

$$|\Omega| = \frac{d}{2} \times \frac{\pi}{2} = \frac{\pi d}{4}$$

Since the distribution is uniform, the probability of any event $A$ is:

$$P(A) = \frac{\text{area of region } A}{\text{area of } \Omega} = \frac{\text{area of } A}{\dfrac{\pi d}{4}}$$

---

## 🔑 Key Geometric Condition

The needle **crosses a line** when the distance $x$ from its centre to the nearest line is less than or equal to the half-projection of the needle perpendicular to the lines:

$$x \leq \frac{L}{2}\sin\theta$$

**Why?** The needle has length $L$. Its perpendicular projection onto the direction crossing the lines has length $L\sin\theta$. Half of this projection extends on each side of the centre, so crossing occurs when:

```
x ≤ (L/2)·sin(θ)
```

---

## ✅ Solutions

### Event $A$ — the needle intersects one of the lines

The crossing region is:

```
Region A = { (x, θ) | 0 ≤ x ≤ (L/2)·sin(θ), θ ∈ [0, π/2] }
```

**Area of region $A$** (integrate over $\theta$):

$$\text{area}(A) = \int_0^{\pi/2} \frac{L}{2}\sin\theta \, d\theta = \frac{L}{2} \Big[-\cos\theta\Big]_0^{\pi/2} = \frac{L}{2}(-\cos\tfrac{\pi}{2} + \cos 0) = \frac{L}{2}(0 + 1) = \frac{L}{2}$$

$$\boxed{P(A) = \frac{L/2}{\pi d/4} = \frac{2L}{\pi d}}$$

> This is the **classical Buffon result** — it can be used to estimate $\pi$ experimentally by counting how many throws cross a line.

---

### Event $B$ — the needle does not intersect any line

$B$ is the complement of $A$:

$$P(B) = 1 - P(A) = 1 - \frac{2L}{\pi d}$$

---

### Event $C$ — the angle between the needle and the lines is smaller than $\frac{\pi}{6}$

This event depends only on $\theta$, not on $x$. The region is a horizontal strip:

```
Region C = { (x, θ) | x ∈ [0, d/2], θ ∈ [0, π/6] }
```

$$\text{area}(C) = \frac{d}{2} \times \frac{\pi}{6} = \frac{\pi d}{12}$$

$$P(C) = \frac{\pi d / 12}{\pi d / 4} = \frac{4}{12} = \frac{1}{3}$$

> Intuitive check: $\frac{\pi/6}{\pi/2} = \frac{1}{3}$ — the angle range $[0, \frac{\pi}{6}]$ is exactly one third of the full range $[0, \frac{\pi}{2}]$.

---

### Event $D$ — the centre of the needle falls at a distance less than $\frac{d}{4}$ from the nearest line

This event depends only on $x$. The region is a vertical strip:

```
Region D = { (x, θ) | x ∈ [0, d/4], θ ∈ [0, π/2] }
```

$$\text{area}(D) = \frac{d}{4} \times \frac{\pi}{2} = \frac{\pi d}{8}$$

$$P(D) = \frac{\pi d / 8}{\pi d / 4} = \frac{1}{2}$$

> Intuitive check: $\frac{d/4}{d/2} = \frac{1}{2}$ — the distance range $[0, \frac{d}{4}]$ is exactly half of the full range $[0, \frac{d}{2}]$.

---

### Event $E$ — the needle intersects a line AND the angle with the lines is greater than $\frac{\pi}{4}$

This is the intersection of the crossing condition and the angle restriction:

```
Region E = { (x, θ) | 0 ≤ x ≤ (L/2)·sin(θ), θ ∈ [π/4, π/2] }
```

**Area of region $E$** (integrate over the restricted angle range):

$$\text{area}(E) = \int_{\pi/4}^{\pi/2} \frac{L}{2}\sin\theta \, d\theta = \frac{L}{2}\Big[-\cos\theta\Big]_{\pi/4}^{\pi/2}$$

$$= \frac{L}{2}\left(-\cos\frac{\pi}{2} + \cos\frac{\pi}{4}\right) = \frac{L}{2}\left(0 + \frac{\sqrt{2}}{2}\right) = \frac{L\sqrt{2}}{4}$$

$$P(E) = \frac{L\sqrt{2}/4}{\pi d/4} = \frac{L\sqrt{2}}{\pi d}$$
---

### Additional Event F — the needle intersects a line AND the centre is within d/4 of the nearest line

This combines the crossing condition with the restricted distance range:

```
Region F = { (x, θ) | 0 ≤ x ≤ min((L/2)·sin(θ), d/4), θ ∈ [0, π/2] }
```

We split the integral at the angle θ* where (L/2)·sin(θ*) = d/4, i.e. sin(θ*) = d/(2L):

* For θ < θ*: the crossing bound (L/2)·sin(θ) < d/4, so the full crossing region lies within the strip.
* For θ ≥ θ*: the strip bound d/4 is the tighter constraint.

```
area(F) = ∫₀^{θ*} (L/2)·sin(θ) dθ + ∫_{θ*}^{π/2} (d/4) dθ
```

```
= (L/2)[−cos(θ)]₀^{θ*} + (d/4)(π/2 − θ*)
```

```
= (L/2)(1 − cos(θ*)) + (d/4)(π/2 − θ*)
```

```
P(F) = area(F) / (πd / 4)
```

---

## 💡 Key Insights

- In **continuous probability**, individual outcomes have probability zero — probabilities are assigned to **regions** via area ratios.

- The **classical Buffon result** $P(A) = \frac{2L}{\pi d}$ is remarkable — it connects a geometric experiment to $\pi$:

$$\pi \approx \frac{2L \cdot n}{d \cdot k}$$

where $n$ is the total number of throws and $k$ is the number of crossings observed.

- Events involving **only $x$** or **only $\theta$** reduce to simple strip area ratios — no integration needed.

- Events involving **both $x$ and $\theta$** (like $A$, $E$, $F$) require integration because the boundary curve $x = \frac{L}{2}\sin\theta$ is not a straight line.

| Event | Type | Method |
|:---:|:---|:---:|
| $A$ | Crossing | Integration over full $\theta$ range |
| $B$ | No crossing | Complement of $A$ |
| $C$ | Angle only | Strip area ratio |
| $D$ | Distance only | Strip area ratio |
| $E$ | Crossing + angle | Integration over restricted $\theta$ range |
| $F$ | Crossing + distance | Split integral |

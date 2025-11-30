---
layout: post
title: "Real Analysis Lecture 7: Product Measure"
date: 2025-10-19
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.


# (07a) Double Integral and Iterated Integral <!-- % 이중적분과 반복적분 -->

## Definition 
Let $\lbrace X, \mathcal{S}, \mu \rbrace$ and $\lbrace Y, \mathcal{T}, \nu \rbrace$ be measure spaces.

For $E \subset X \times Y$, $x \in X$, $y \in Y$, define  
\[
E_x = \lbrace y \in Y : \lbrace x, y \rbrace \in E \rbrace,  
\qquad
E^y = \lbrace x \in X : \lbrace x, y \rbrace \in E \rbrace.
\]

## Properties

1. $E \in \mathcal{S} \times \mathcal{T} \;\Rightarrow\; E_x \in \mathcal{T}, \; E^y \in \mathcal{S}$.

2. Define $\varphi(x) = \nu(E_x), \, \psi(y) = \mu(E^y)$. 
   
   Then $\varphi$ is $\mu$-measurable and $\psi$ is $\nu$-measurable.

3. $\int_X \varphi \, d\mu = \int_Y \psi \, d\nu$.



\[ \text{i.e.} \;
\int_X \int_Y \chi_E(x,y) \, d\nu(y) \, d\mu(x)
=
\int_Y \int_X \chi_E(x,y) \, d\mu(x) \, d\nu(y).
\]

---

Let  
\[
(X \times Y,\; \mathcal{S} \times \mathcal{T},\; \mu \times \nu).
\]
For $S \in \mathcal{S}$ and $T \in \mathcal{T}$, $\mathcal{R} = S \times T \subset X \times Y$ is a **measurable rectangle**.

- $\mathcal{S} \times \mathcal{T}$ is the **smallest $\sigma$-algebra containing all measurable rectangles**.

---
---

# (07b) Product Measure and Measurable Set <!-- % 곱측도와 잴 수 있는 집합 -->

Assume $(X, \mu)$ and $(Y, \nu)$ are **$\sigma$-finite**.

i.e.

- $X = \bigcup_{n=1}^\infty X_n, \; \mu(X_n) < \infty$

- $Y = \bigcup_{m=1}^\infty Y_m, \; \nu(Y_m) < \infty$

## Definition 
\[
\mathcal{A} = \lbrace E \in \mathcal{S} \times \mathcal{T} : E_x \in \mathcal{T},\ \forall x \in X \rbrace,
\]
\[
\mathcal{B} = \lbrace E \in \mathcal{S} \times \mathcal{T} : \varphi \;\&\; \psi \; \text{is measureable},  \int_X \varphi \, d\mu = \int_Y \psi \, d\nu \ \rbrace.
\]


### Property 7-1.
If $E_n \in \mathcal{B}$ is increasing, then $\bigcup_{n=1}^\infty E_n \in \mathcal{B}$.

#### pf)

- $\varphi_n$ increase pointwise $\Rightarrow$ $\varphi$ is measurable.  
- $\psi_n$ increase pointwise $\Rightarrow$ $\psi$ is measurable.

Let  
\[
E = \bigcup_{n=1}^\infty E_n.
\]

Since $\lbrace E_n \rbrace$ is increasing, for each fixed $x \in X$,
\[
\varphi_n(x)
= \int_Y \chi_{E_n}(y)\, d\nu(y)
\nearrow
\int_Y \chi_{E}(y)\, d\nu(y)
= \varphi(x).
\]

Likewise, for each fixed $y \in Y$,
\[
\psi_n(y)
= \int_X \chi_{E_n}(x)\, d\mu(x)
\nearrow
\int_X \chi_{E}(x)\, d\mu(x)
= \psi(y).
\]

By the Monotone Convergence Theorem,
\[
\int_X \varphi \, d\mu
=
\lim_{n\to\infty} \int_X \varphi_n \, d\mu,
\quad
\int_Y \psi \, d\nu
=
\lim_{n\to\infty} \int_Y \psi_n \, d\nu.
\]

Since $E_n \in \mathcal{B}$,
\[
\int_X \varphi_n \, d\mu
=
\int_Y \psi_n \, d\nu
\quad \text{for all } n.
\]

Taking limits,
\[
\int_X \varphi \, d\mu
=
\lim_{n\to\infty} \int_X \varphi_n \, d\mu
=
\lim_{n\to\infty} \int_Y \psi_n \, d\nu
=
\int_Y \psi \, d\nu.
\]


Thus $E$ satisfies the defining property of $\mathcal{B}$ and hence  
\[
E \in \mathcal{B}.
\]


### Property 7-2.
If $E_n \in \mathcal{B}$, then $\bigcup_{n=1}^\infty E_n \in \mathcal{B}$.

#### pf)

First reduce to the **pairwise disjoint** case.

Define
\[
F_1 = E_1,\qquad
F_n = E_n \setminus \bigcup_{k=1}^{n-1} E_k \quad (n \ge 2).
\]
Then $\lbrace F_n \rbrace \in \mathcal{B}$ are pairwise disjoint and
\[
\bigcup_{n=1}^\infty F_n = \bigcup_{n=1}^\infty E_n.
\]

Now set
\[
G_n = \bigcup_{k=1}^n F_k \quad (n \ge 1).
\]
Then $\lbrace G_n \rbrace$ is an **increasing** sequence and
each $G_n \in \mathcal{B}$.
Moreover,
\[
\bigcup_{n=1}^\infty G_n = \bigcup_{n=1}^\infty F_n
= \bigcup_{n=1}^\infty E_n.
\]

By **Property 7-1**, the increasing union of sets in $\mathcal{B}$
again belongs to $\mathcal{B}$, so
\[
\bigcup_{n=1}^\infty E_n
= \bigcup_{n=1}^\infty G_n \in \mathcal{B}.
\]

---

## Definition 
\[
\mathcal{C} = \lbrace E \in \mathcal{S} \times \mathcal{T} : E \cap (X_n \times Y_m) \in \mathcal{B}, \; \forall m,n = 1,2,\dots \rbrace,
\]

### Property 7-3.
If $E_n \in \mathcal{C}$ is increasing, then $\bigcup_{n=1}^\infty E_n \in \mathcal{C}$.

#### pf) Apply the MCT.

### Property 7-4.
If $E_n \in \mathcal{C}$ is decreasing, then $\bigcap_{n=1}^\infty E_n \in \mathcal{C}$.

#### pf)  Apply the Lebesgue Dominated Convergence Theorem.

### Property 7-5.
If $E_1, \dots, E_n \in \mathcal{R}$, then $\bigcup_{i=1}^N E_i \in \mathcal{C}$.

---

## Definition 

Let $\mathcal{D}$ ($\subseteq \varphi \subseteq \mathcal{S} \times \mathcal{T}$) be the smallest family satisfying

1. $\mathcal{D} \supset \mathcal{R}$

2. Satisties **Property 7-3 ~ 7-5**


Let $\mathcal{E}$ be finite disjoint unions of measurable rectangles.

Then $\mathcal{D}$ be the smallest family containing $\mathcal{E}$ with

\[
E_n \in \mathcal{D} \nearrow \; \Rightarrow \; \bigcup_{n=1}^\infty \in \mathcal{D}
\]
\[
E_n \in \mathcal{D} \searrow \; \Rightarrow \; \bigcap_{n=1}^\infty \in \mathcal{D}
\]


- $E, F \in \mathcal{E} \Rightarrow E \setminus F \in \mathcal{E}, \; F \setminus E \in \mathcal{E}, \; E \cup F \in \mathcal{E}$
  
- For $E \subset X \times Y$, define
\[
\Omega(E) = \lbrace F \subset X \times Y :
E \setminus F \in \mathcal{D}, \; F \setminus E \in \mathcal{D}, \; E \cup F \in \mathcal{D} \rbrace
\]

- $E, F \in \mathcal{E} \Rightarrow F \in \Omega(E)$
  
  $E \in \mathcal{E} \Rightarrow \mathcal{E} \subseteq \Omega(E) \Rightarrow \mathcal{D} \subseteq \Omega(E)$

  $E \in \mathcal{D} \Rightarrow \mathcal{D} \subseteq \Omega(E)$

- $E_n \in \mathcal{D} \Rightarrow F_N = E_1 \cup \ldots \cup E_N \in \mathcal{D}$
  
  $\bigcup_{n=1}^\infty E_n = \bigcup_{n=1}^\infty F_n \in \mathcal{D}$

- $\mathcal{D} = \varphi = \mathcal{S} \times \mathcal{T}$ is **$\sigma$-algebra**

### Property 7-6.

We conclude:
$
(\mu \times \nu)(E) 
= \int_X \nu(E_x)\, d\mu(x)
= \int_Y \mu(E^y)\, d\nu(y).
$

\[
\Rightarrow E = \bigcup_{n=1}^\infty E_n, \; \sum_{n=1}^\infty (\mu \times \nu) (E_n) = (\mu \times \nu)(E)
\]

#### pf)


Since $\mathcal{D}$ was constructed to satisfy Properties 7-3–7-5 and contains all measurable rectangles, it follows (from the previous steps in the construction) that:

1. If $E_n\nearrow E$ with $E_n\in\mathcal{D}$, then  
   \[
   \nu((E_n)_x)\nearrow\nu(E_x)
   \quad\text{for all }x,
   \]
   and 
   \[
   \mu((E_n)^y)\nearrow\mu(E^y)
   \quad\text{for all }y.
   \]

2. Each $E_n$ satisfies the defining identity of $\mathcal{D}$:
   \[
   (\mu\times\nu)(E_n)
   =\int_X \nu((E_n)_x)\,d\mu
   =\int_Y \mu((E_n)^y)\,d\nu.
   \]



If $E_n$ are pairwise disjoint,
\[
\chi_E=\sum_{n=1}^{\infty}\chi_{E_n}.
\]
Integrating both sides over $X\times Y$:
\[
(\mu\times\nu)(E)
=\int_{X\times Y}\chi_E\,d(\mu\times\nu)
=\int_{X\times Y}\sum_{n=1}^{\infty}\chi_{E_n}\,d(\mu\times\nu).
\]

Apply MCT again:
\[
\int_{X\times Y}\sum_{n=1}^{\infty}\chi_{E_n}
=
\sum_{n=1}^{\infty}\int_{X\times Y}\chi_{E_n}
=
\sum_{n=1}^{\infty}(\mu\times\nu)(E_n).
\]

Thus,
\[
(\mu\times\nu)(E)
=\sum_{n=1}^{\infty}(\mu\times\nu)(E_n).
\]

---
---

# (07c) Two-Dimensional Lebesgue Measure <!-- % 이차원 르벡측도 -->

Consider $(\mathbb{R}^2, \mathcal{L} \times \mathcal{L}, m \times m)$.

- Every open set is in $\mathcal{L} \times \mathcal{L}$.
- Let $\mathcal{B}_2$ be the smallest $\sigma$-algebra containing all open sets.  
  Then **Borel sets** $\in \mathcal{B}_2$.

## Definition: Complete measure 

$(X, \mathcal{S}, \mu)$ is a **complete measure space**, if

$E \subset F$, $F \in \mathcal{S}$, and $\mu(F)=0$,  $\Rightarrow E \in \mathcal{S}$.

## Definition: Positive measure 

$(X, \mathcal{S}, \mu)$ is a **positive measure space**, if
\[
\mathcal{S}^\ast = \lbrace E \subset X : \exists A, B \in \mathcal{S},\ A \subset E \subset B,\ \mu(B\setminus A)=0 \rbrace.
\]
Then for $E \in \mathcal{S}^\ast$, define $\mu^\ast(E) = \mu(A)$.

Thus $(X, \mathcal{S}^\ast, \mu^\ast)$ is complete measure.

---

## Borel vs Product Completion

Claim:
\[
\mathcal{B}_2^\ast = (\mathcal{L} \times \mathcal{L})^\ast.
\]

**pf)**  
($\subseteq$) If $B \in \mathcal{B}_2$, then $B \subset L \times L$ and completion preserves inclusion.

($\supseteq$)  For $S \in \mathcal{L}$, 
Let $A$ be an $F_\sigma$- set and $B$ a $G_\delta$- set, $A \subset S \subset B$, $\mu(B\setminus A)=0$.  

Thus $A \times \mathbb{R}$ and $B \times \mathbb{R}$ are Borel sets in $\mathbb{R}^2$.  

Hence
\[
m \times m \lbrack (B \times \mathbb{R}) \setminus (A \times \mathbb{R}) \rbrack
= m \times m \lbrack (B \setminus A) \times \mathbb{R} \rbrack = 0.
\]
Thus $S \times \mathbb{R} \in \mathcal{B}_2^\ast$.

And $S \times T = (S \times \mathbb{R}) \cap (\mathbb{R} \times T) \in \mathcal{B}_2^\ast $

Therefore
\[
(\mathcal{L} \times \mathcal{L})^\ast \subseteq \mathcal{B}_2^\ast
\]

- $(\mathbb{R}^2, (\mathcal{L} \times \mathcal{L})^\ast, (m \times m)^\ast)$: **Lebesgue measure in the plane**

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

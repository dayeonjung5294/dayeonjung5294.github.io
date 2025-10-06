---
layout: post
title: "Real Analysis Lecture 1: Countable Sets and Measure"
date: 2025-10-05
categories: [Real_analysis]
use_math: True
---


## (01a) Length of Open Sets <!-- % 열린집합의 길이 -->

### Proposition 1.

Let $U \subset \mathbb{R}$ be open.  
Then
\[
U = \bigcup_{n=1}^{\infty} (a_n, b_n),
\]
and define
\[
\lambda(U) := \sum_{n=1}^{\infty} (b_n - a_n).
\]

> *Note: For non-negative terms, the sum is independent of the order of addition.*  
<!-- % 비음수 항의 무한합은 순서 바꿔도 동일 -->
 

### Proposition 2.

For $S \subset \mathbb{R}$, define
\[
\mu(S) := \inf \lbrace \lambda(U) \mid U \supset S, \, U \text{ open} \rbrace.
\]

#### Properties:
1. <span style="color:blue">Monotonicity</span>: $S \subset T \Rightarrow \mu(S) \le \mu(T)$ <!-- % 단조성 -->
2. If $I$ is an interval, $\mu(I) =$ length of $I$. <!-- % 구간의 길이 -->
3. $ x + S = \lbrace x + y \mid y \in S \rbrace \Rightarrow \mu(x + S) = \mu(S)$
4. <span style="color:blue">Subadditivity</span>:
   \[
   \mu\left( \bigcup_{n=1}^{\infty} S_n \right) \le \sum_{n=1}^{\infty} \mu(S_n).
   \]
   <!-- % 가산부등식 (subadditivity) -->

---
---

## (01b) Properties of Length <!-- % 길이의 성질 -->

Let $A \subseteq \mathbb{R}$, then
\[
\lambda = \inf A 
\]
\[
\Leftrightarrow 
(i) \; \lambda \le a, \forall a \in A 
\quad \& \quad 
(ii) \; \lambda_1 \le a, \forall a \in A \Rightarrow \lambda_1 \le \lambda
\]
\[
\Leftrightarrow 
(i) \; \lambda \le a, \forall a \in A 
\quad \& \quad 
(ii) \; \forall \varepsilon > 0, \exists a \in A \; \textit{s.t.} \; a < \lambda + \varepsilon
\]
\[\color{blue}{
\Leftrightarrow 
(i) \; \lambda \le \inf A
\quad \& \quad 
(ii) \; \inf A \le \lambda
}
\]

---

### pf) Properties 1. Monotonicity <!-- % 증명 -->
\[S \subset T \Rightarrow \mu(S) \le \mu(T)\]

1. Let $\mu(S)$: fixed. ($(i)$ method) 

   Let $U$ open with $U \supset T$, then $S \subset U$.  

   by def of $\\mu(S) := \inf \lbrace \lambda(U) \mid U \supset S, \, U \text{ open} \rbrace$, $\mu(S) \le \lambda(U)$ for $\forall U$ 
   
   $\therefore \mu(S) \le \mu(T) := \inf \lbrace \lambda(U) \mid U \supset T, \, T \text{ open} \rbrace$



2. Similarly, Let $\mu(T)$: fixed. ($(ii)$ method) 
   
   Given $\varepsilon > 0$, let $U$ open with $U \supset T$, Then $S \subset U$.
   
   by def of $\\mu(T) := \inf \lbrace \lambda(U) \mid U \supset T, \, T \text{ open} \rbrace$, $\lambda(U) < \mu(T) + \varepsilon$.
   
   $\therefore \mu(T) \ge \inf \lbrace \lambda(U) \mid U \supset S, \, U \text{ open} \rbrace = \mu(S)$.

---

### pf) Properties 4. Subadditivity

\[
\mu\left( \bigcup_{n=1}^{\infty} S_n \right) \le \sum_{n=1}^{\infty} \mu(S_n).
\]

#### Case (I): $S_n$: open interval

1. $\bigcup_{n=1}^{\infty} S_n = (a,b)$: open inverval 

   $\forall \varepsilon > 0, \; \exists N \; \textit{s.t.} \; [a + \varepsilon, b - \varepsilon] \subset \bigcup_{n=1}^N S_n$. <span style="color:blue">(* Definition of compact set)</span> 
   
   Then
   $b - a - 2\varepsilon \le \mu\left( \bigcup_{n=1}^N S_n \right) \le \sum_{n=1}^N \mu(S_n) \le \sum_{n=1}^{\infty} \mu(S_n)$.
   
   <span style="color:blue">(measure inequality holds for any finite or countable collection of sets)</span> 
   
   Since $\varepsilon > 0$ is arbitrary, $b - a \le \sum_{n=1}^{\infty} \mu(S_n)$. 
   
   Thus $\mu(\bigcup_{n=1}^{\infty} S_n) \le \sum_{n=1}^{\infty} \mu(S_n)$.

2. If $\bigcup_{n=1}^{\infty} S_n$ is **not a single interval** but rather a union of disjoint open intervals $I_m$ ($\bigcup_{n=1}^{\infty} S_n = \bigcup_{m=1}^{\infty} I_m$),  
   
   Let $A(m) = \lbrace n \in \mathcal{N} \mid S_n \in I_m \rbrace$, then $\bigcup_{n \in A(m)} S_n = I_m$.
   
   Then \[
   \mu \left(\bigcup_{n=1}^{\infty} S_n\right) 
   = \mu \left(\bigcup_{m=1}^{\infty} I_m\right)
   = \sum_{m=1}^{\infty} \mu (I_m) 
   \le \sum_{m=1}^{\infty} \sum_{n \in A(m)} \mu(S_n) 
   \le \sum_{n=1}^{\infty} \mu(S_n) 
   \]

> *Note: The first inequality follows from Case (I)-1, second follows for non-negative terms, the sum is independent of the order of addition.*


#### Case (II): $S_n$: open set
Each open set can be written as a countable union of disjoint open intervals:
\[
S_n = \bigcup_{k=1}^{\infty} I_{nk}.
\]
Then
\[
\mu\left( \bigcup_{n=1}^{\infty} S_n \right)
= \mu\left( \bigcup_{n,k=1}^{\infty} I_{nk} \right)
\le \sum_{n,k=1}^{\infty} \mu(I_{nk})
= \sum_{n=1}^{\infty} \left( \sum_{k=1}^{\infty} \mu(I_{nk}) \right)
= \sum_{n=1}^{\infty} \mu(S_n).
\]

> *Note: The inequality follows from Case (I).*



#### Case (III): General case
Given $\varepsilon > 0$, choose open sets $U_n \supset S_n$ s.t.
$\mu(U_n) \le \mu(S_n) + \frac{\varepsilon}{2^n}$.

Let $U = \bigcup_{n=1}^{\infty} U_n$.  

Then by Case (II),
\[
\lambda(U) \le \sum_{n=1}^{\infty} \mu(U_n) \le \sum_{n=1}^{\infty} \mu(S_n) + \varepsilon.
\]
Then 
\[
\inf \lambda(U) \le \sum_{n=1}^{\infty} \mu(S_n)
\]

Let $\sum_{n=1}^{\infty} \mu(S_n)$ be assumed to be a fixed finite value.

Since $\inf \lambda(U) = \inf \lbrace \lambda(U) \mid U \supset \bigcup S_n,\, U \text{ open} \rbrace := \mu \left( \bigcup_{n=1}^{\infty} S_n \right)$,
we conclude.

---

## [1c] Measurable Sets and Measure <!-- % 가측집합과 측도 -->

### Definition
A set $E \subset \mathbb{R}$ is **measurable** if
\[
\forall A \subset \mathbb{R}, \quad \mu(A) = \mu(A \cap E) + \mu(A \cap E^c).
\]
<!-- % 측도의 분할공식 -->

Let $\mathcal{M}$ denote the collection of all measurable sets.

Then for disjoint measurable sets $E_n$,
\[
\mu\left( \bigcup_{n=1}^{\infty} E_n \right) = \sum_{n=1}^{\infty} \mu(E_n).
\]
<!-- % 가산가법성 -->

---

### Properties of Measurable Sets

1. $\mathbb{R} \in \mathcal{M}$  
2. If $E \in \mathcal{M}$, then $E^c \in \mathcal{M}$  
3. If $\{E_n\} \subset \mathcal{M}$, then $\bigcup E_n \in \mathcal{M}$  
   <!-- % 시그마 대수 성질 -->

Thus $\mathcal{M}$ is a **σ-algebra**. <!-- % 시그마-대수 -->

---

### Proof Sketch
Let $E, F \in \mathcal{M}$.  
Then both $E \cup F$ and $E \cap F$ are measurable.

Indeed,
\[
\mu(A) = \mu(A \cap (E \cup F)) + \mu(A \cap (E \cup F)^c)
\]
can be expanded using subadditivity and the fact that $E, F$ are measurable.  
Hence $E \cup F \in \mathcal{M}$.

---

### Countable Additivity
Let $E_n$ be disjoint measurable sets and $E = \bigcup E_n$.  
Then
\[
\mu(A) = \mu(A \cap E) + \mu(A \cap E^c)
= \mu\left( A \cap \bigcup E_n \right) + \mu(A \cap E^c)
= \sum_n \mu(A \cap E_n) + \mu(A \cap E^c).
\]
Thus,
\[
\mu(E) = \sum_n \mu(E_n).
\]


## [1d] Further Properties of Measurable Sets <!-- % 절수 있는 집합과 측도의 성질 -->

Let $n \to \infty$.

If $\{E_n\}$ is an **increasing sequence** of measurable sets,  
then
\[
\mu\left( \bigcup_{n=1}^{\infty} E_n \right) = \lim_{n \to \infty} \mu(E_n).
\]

If $\{F_n\}$ is a **decreasing sequence** of measurable sets with $\mu(F_1) < \infty$,  
then
\[
\mu\left( \bigcap_{n=1}^{\infty} F_n \right) = \lim_{n \to \infty} \mu(F_n).
\]
<!-- % 연속성: 증가/감소하는 집합열에서의 측도 극한 -->

---

### Definition
Let $X$ be a set and $\mathcal{L} \subset 2^X$.  
If $\mu$ is defined on $\mathcal{L}$ and satisfies the above properties,  
then we call $\mathcal{L}$ a **σ-algebra** and $\mu$ a **measure** on $\mathcal{L}$.  
<!-- % 시그마 대수와 측도의 정의 -->

---

### Countable and Uncountable Sets
A **countable set** has measure zero. <!-- % 셀 수 있는 집합의 측도는 0 -->
An **uncountable set** may have positive or zero measure depending on its structure.  

Let $\{E_n\}$ be increasing. Then
\[
\mu\left( \bigcup_n E_n \right) = \lim_{n \to \infty} \mu(E_n).
\]
Let $\{F_n\}$ be decreasing with $\mu(F_1) < \infty$. Then
\[
\mu\left( \bigcap_n F_n \right) = \lim_{n \to \infty} \mu(F_n).
\]

---

### Theorem: Equivalent Characterizations of Measurability
For $E \subset \mathbb{R}$, the following are equivalent:

1. $E \in \mathcal{L}$ (i.e., $E$ is measurable).  
2. For every $\varepsilon > 0$, there exist an open set $U$ and a closed set $F$ such that  
   \[
   F \subset E \subset U, \quad \mu(U \setminus F) < \varepsilon.
   \]
   <!-- % 외부근사/내부근사에 의한 가측성 등가조건 -->

---

### Definition: $F_\sigma$ and $G_\delta$ Sets
A set $A \subset \mathbb{R}$ is:

- **$F_\sigma$ set** if it is a **countable union of closed sets**:  
  \[
  A = \bigcup_{n=1}^{\infty} F_n, \quad F_n \text{ closed.}
  \]

- **$G_\delta$ set** if it is a **countable intersection of open sets**:  
  \[
  A = \bigcap_{n=1}^{\infty} U_n, \quad U_n \text{ open.}
  \]
  <!-- % F_sigma, G_delta 집합의 정의 -->

---

### Theorem: Approximation by $F_\sigma$ and $G_\delta$ Sets
For any measurable set $E$, there exist a $G_\delta$ set $A$ and an $F_\sigma$ set $B$  
such that
\[
B \subset E \subset A, \quad \mu(A \setminus B) = 0.
\]
<!-- % 가측집합의 근사: F_sigma와 G_delta로부터 -->

---

### Proof Sketch
Let $\mathbb{R} = \bigcup_{k=-\infty}^{\infty} I_k$,  
where $I_k = [k, k + 1)$ (a partition of $\mathbb{R}$ into bounded intervals).

Define $E_k = E \cap I_k$ for each $k$.

For each $E_k$, take open sets $U_k \supset E_k$ such that
\[
\mu(U_k) < \mu(E_k) + \frac{\varepsilon}{2^{k+1}}.
\]
Let
\[
U = \bigcup_k U_k.
\]
Then
\[
\mu(U) < \mu(E) + \varepsilon.
\]
Similarly, one can construct closed sets $F_k \subset E_k$ with
\[
\mu(F_k) > \mu(E_k) - \frac{\varepsilon}{2^{k+1}},
\]
and set $F = \bigcup_k F_k$.
Thus,
\[
F \subset E \subset U, \quad \mu(U \setminus F) < \varepsilon.
\]
✅ Hence, measurable sets can be approximated arbitrarily closely by $F_\sigma$ and $G_\delta$ sets.

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

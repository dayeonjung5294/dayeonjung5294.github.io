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
---

## (01c) Measurable Sets and Measure <!-- % 가측집합과 측도 -->

### Definition
$E \subset \mathbb{R}$ is **measurable**
\[
\Leftrightarrow \forall A \subset \mathbb{R}, \quad \mu(A) = \mu(A \cap E) + \mu(A \cap E^c).
\]

Let $\mathcal{M}$: the collection of all measurable sets.

---

### Properties of Measurable Sets

1. $\emptyset \in \mathcal{M}, \mathbb{R} \in \mathcal{M}$  
2. If $E \in \mathcal{M}$, then $E^c \in \mathcal{M}$  
3. If $E_1, E_2, \ldots \in \mathcal{M}$, then $\bigcup_{n=1}^{\infty} E_n \in \mathcal{M}$  <span style="color:blue">(closed under countable unions)</span>
   <!-- % 시그마 대수 성질 -->

Thus $\mathcal{M}$ is a **σ-algebra**. 

---

### Additivity
For disjoint measurable sets $E_n$,
\[
\mu\left( \bigcup_{n=1}^{\infty} E_n \right) = \sum_{n=1}^{\infty} \mu(E_n).
\]

### pf Step 1)

Let $E, F \in \mathcal{M}$. ($E, F$ are disjoint)
   
Then 
$
\mu(A \cap (E \cup F)) 
= \mu(A \cap (E \cup F) \cap E) + \mu(A \cap (E \cup F) \cap E^c)
= \mu(A \cap E) + \mu(A \cap F)
$

### pf Step 2)
Let $E_1, E_2, \ldots, E_n \in \mathcal{M}$.

Then $\mu\left(A \cap \left( \bigcup_{i=1}^n E_i \right)\right) = \sum_{i=1}^n \mu(A \cap E_i)$, by mathematical induction

### pf Step 3)

**Step 3-1 ($\le$).**  

Since $(A \cap E_i)$ are pairwise disjoint and $\mu$ is subadditive,  $\mu\left( A \cap \bigcup_{i=1}^{\infty} E_i \right) = \mu\left( \bigcup_{i=1}^{\infty} (A \cap E_i) \right) \le \sum_{i=1}^{\infty} \mu(A \cap E_i)$.  


**Step 3-2 ($\ge$).**  

Let $F_N := \bigcup_{i=1}^{N} E_i$ and $F := \bigcup_{i=1}^{\infty} E_i$.  

Then $F_N \uparrow F$ and $F_N, F \in \mathcal{M}$ (Property 3).  

By **finite additivity** on disjoint sets (proved in Step 2), $\mu\left( A \cap F_N \right) = \sum_{i=1}^{N} \mu(A \cap E_i)$.  

By monotonicity, $\mu(A \cap F_N) \le \mu(A \cap F)$ for all $N$; hence $\sum_{i=1}^{N} \mu(A \cap E_i) \le \mu(A \cap F)$ for all $N$.  

Taking the supremum over $N$, $\sum_{i=1}^{\infty} \mu(A \cap E_i) \le \mu(A \cap F)$.  

---

### Measure

Let $X$ be a set, and let $\mathcal{M} \subseteq 2^{X}$.  

Suppose there exists a function $\mu : \mathcal{M} \to \lbrack 0, \infty \rbrack$ that satisfies the following three properties of measurable sets:

1. $\emptyset \in \mathcal{M}$.  
2. If $E \in \mathcal{M}$, then $E^{c} \in \mathcal{M}$.  
3. If $E_1, E_2, \ldots \in \mathcal{M}$, then $\bigcup_{n=1}^{\infty} E_n \in \mathcal{M}$.  

In addition, if for any pairwise disjoint sequence $E_1, E_2, \ldots \in \mathcal{M}$, $\mu\left( \bigcup_{n=1}^{\infty} E_n \right) = \sum_{n=1}^{\infty} \mu(E_n)$,  

then $\mu$ is called a **measure** on $\mathcal{M}$.



---
---

## (01d) Measurable Sets and Topology <!-- % 잴 수 있는 집합과 위상 -->

### Cantor Set

The **Cantor set** $C$ is a subset of the closed interval $\lbrack 0, 1 \rbrack$ constructed as follows:

1. **Start:** Begin with the closed interval $\lbrack 0, 1 \rbrack$.
2. **Remove:** Delete the open middle third interval $\left( \frac{1}{3}, \frac{2}{3} \right)$.
   The remaining set is $\lbrack 0, \frac{1}{3} \rbrack \cup \lbrack \frac{2}{3}, 1 \rbrack$.
3. **Iterate:** From each remaining closed interval, remove its open middle third.
   After the second step, the set is  
   $\lbrack 0, \frac{1}{9} \rbrack \cup \lbrack \frac{2}{9}, \frac{1}{3} \rbrack \cup \lbrack \frac{2}{3}, \frac{7}{9} \rbrack \cup \lbrack \frac{8}{9}, 1 \rbrack$.
4. **Continue indefinitely:** Repeat this process infinitely many times.

The resulting set is  
\[
C = \bigcap_{n=1}^{\infty} C_n,
\]
where $C_n$ is the union of $2^n$ closed intervals remaining after the $n$-th step.

$C$ is **uncountable** but has **measure zero**.


---

Let $\{E_n\}$ be increasing. Then
\[
\mu\left( \bigcup_{n=1}^{\infty} E_n \right) = \lim_{n \to \infty} \mu(E_n).
\]

Let $\{E_n\}$ be decreasing with $\mu(E_1) < \infty$. Then
\[
\mu\left( \bigcap_{n=1}^{\infty} E_n \right) = \lim_{n \to \infty} \mu(E_n).
\]

### pf)
Let $E_1 = F_1$ and define $F_n := E_n \setminus E_{n-1}$ for $n\ge 2$.  
Then $\{F_n\}$ are pairwise disjoint and measurable, and for each $n$,
\[
E_n \;=\; \bigcup_{k=1}^{n} F_k, 
\qquad
\bigcup_{n=1}^{\infty} E_n \;=\; \bigcup_{n=1}^{\infty} F_n.
\]
<!-- % 증가열에서의 층별 분해: Fn이 서로소이고 En의 분해 및 합집합 일치 -->

By **finite additivity** on disjoint measurable sets,
\[
\mu(E_n) \;=\; \sum_{k=1}^{n} \mu(F_k).
\]
Taking $n\to\infty$ (monotone limit of partial sums),
\[
\lim_{n\to\infty} \mu(E_n) 
\;=\; \sum_{k=1}^{\infty} \mu(F_k).
\]
On the other hand, by **countable additivity** on the disjoint family $\{F_k\}$,
\[
\sum_{k=1}^{\infty} \mu(F_k)
\;=\; \mu\left(\bigcup_{n=1}^{\infty} F_n\right)
\;=\; \mu\left(\bigcup_{n=1}^{\infty} E_n\right).
\]

Therefore,
\[
\mu\left(\bigcup_{n=1}^{\infty} E_n\right) 
\;=\; \lim_{n\to\infty} \mu(E_n).
\]


---

### Definition: $F_\delta$ and $G_\delta$ Sets <!-- % F_delta, G_delta 집합의 정의 -->
A set $A \subset \mathbb{R}$ is:

- **$F_\delta$ - set** $\Leftrightarrow$ **union of countable closed sets**:  
  \[
  A = \bigcup_{n=1}^{\infty} F_n, \quad F_n \text{ closed.}
  \]

- **$G_\delta$ - set** $\Leftrightarrow$ **intersection of countable open sets**:  
  \[
  A = \bigcap_{n=1}^{\infty} U_n, \quad U_n \text{ open.}
  \]
  


---

### Theorem: Equivalent Characterizations of Measurability
For $E \subset \mathbb{R}$, the following are equivalent (TFAE):

1. $E \in \mathcal{M}$.
2. $\forall \varepsilon > 0$, $\exists$ a open set $U$ and a closed set $F$ s.t.
   \[
   F \subset E \subset U, \quad \mu(U \setminus F) < \varepsilon.
   \]
3. $\exists \; G_\delta$ - set $A$ & $F_\delta$ - set $B$ s.t. $B \subset E \subset A, \; \mu(A \setminus B) = 0$.

### pf 1) $\rightarrow$ 2)
Let $\mathbb{R} = \bigcup_{n=1}^{\infty} k_n$, $\mu(k_n) < \infty$.

Define $E_n = E \cap k_n$ for each $n$.

Take open set $U_n$ s.t. $U_n \supset E_n$ & $\mu(U_n) < \mu(E_n) + \frac{\varepsilon}{2^{n+1}}$.

Put $U = \bigcup_{n=1}^{\infty} U_n$, then $\mu(U) < \mu(E) + \frac{\varepsilon}{2}$.

Similarly, take closed set $F_n$ s.t. $F_n \subset E_n$ & $\mu(F_n) > \mu(E_n) - \frac{\varepsilon}{2^{n+1}}$, and set $F = \bigcup_{n=1}^{\infty} F_n$. Then $\mu(E) < \mu(F) +\frac{\varepsilon}{2}$.

### pf 2) $\rightarrow$ 3)

For each $m \in \mathbb{N}$, choose open $U_m$ and closed $F_m$ such that
$F_m \subset E \subset U_m$ and $\mu(U_m \setminus F_m) < 2^{-m}$.

Define
\[
A := \bigcap_{m=1}^{\infty} U_m \quad(\text{$G_\delta$ set}), 
\qquad
B := \bigcup_{m=1}^{\infty} F_m \quad(\text{$F_\delta$ set}).
\]
Then $B \subset E \subset A$.

Note that
\[
A \setminus B 
\;\subset\; \bigcap_{m=1}^{\infty} U_m \setminus \bigcup_{m=1}^{\infty} F_m
\;\subset\; \bigcap_{m=1}^{\infty} \bigcup_{k \ge m} \left(U_k \setminus F_k\right).
\]

Hence, since $\bigcup_{k \ge m} \left(U_k \setminus F_k\right)$ is a decreasing sequence of sets and by subadditivity, we have
\[
\mu(A \setminus B) 
\;\le\; \lim_{m\to\infty} \sum_{k \ge m} \mu\left(U_k \setminus F_k\right)
\;\le\; \lim_{m\to\infty} \sum_{k \ge m} 2^{-k}
\;=\; 0.
\]


### pf 3) $\rightarrow$ 1)


- Open sets are measurable; hence closed sets are measurable; thus every $G_\delta$ and $F_\delta$ set is measurable (the measurable sets form a $\sigma$-algebra).
- Since $A$ and $B$ are measurable and $\mu(A \setminus B)=0$, any subset of $A \setminus B$ is **null** and hence measurable.
- Decompose
  \[
  E \;=\; B \,\cup\, \big(E \setminus B\big), 
  \quad \text{with } E \setminus B \subset A \setminus B.
  \]
  Here $B$ is measurable and $E \setminus B$ is a subset of a null set, so measurable.

Therefore $E$ is measurable, i.e., $E \in \mathcal{M}$.

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

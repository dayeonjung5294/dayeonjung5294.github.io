---
layout: post
title: "Real Analysis Lecture 2: Measurable Functions and Integral"
date: 2025-09-14
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.

# (02a) Measurable Functions


- **Riemann Sum:**  
  $\sum_{i=1}^n f(\alpha_i)(x_i - x_{i-1}), \quad x_{i-1} \le \alpha_i \le x_{i}$  

- **Step Function:**  
  A linear combination of characteristic functions on intervals.  
  ($c \chi_I$: a characteristic function on interval $I$)


- **Characteristic Function:**  
  Has value on interval $I$ and 0 otherwise



- **Legesque Integral:**
  Replace "interval" with **measurable set**



<!-- % f: measurable의 정의 -->
Let $E \subseteq \mathbb{R}$ be measurable.  
A function $f : E \to \mathbb{R}^* = \mathbb{R} \cup \lbrace \pm \infty \rbrace$ is **measurable**  

$\Leftrightarrow \forall a \in \mathbb{R}$, the set $\lbrace x \in E \mid f(x) > a \rbrace \in \mathcal{M}$


In this section, we discuss four cases of **integral of a measurable function**:

1. **$\lbrack$ Case 1 $\rbrack$ Simple Function**  

2. **$\lbrack$ Case 2 $\rbrack$ Nonnegative Measurable Function ($f \ge 0$)**  

3. **$\lbrack$ Case 3 $\rbrack$ Real-Valued Measurable Function**  

4. **$\lbrack$ Case 4 $\rbrack$ Complex-Valued Measurable Function**  


---

## $\lbrack$ Case 1 $\rbrack$ $f$ is Simple Function 

$f : E \to \mathbb{R}$ is **simple** if
- $f = \sum_{i=1}^{n} c_i \chi_{E_i}$ is measurable, and  
- its range is finite.  


### Def.
\[
\int_E f = \sum_{i=1}^{n} c_i \mu(E_i).
\]
<!-- % 단순함수의 적분 정의 -->


---

### Basic Properties of Integral

If $f, g$ are and measurable, then:

- $f \le g \Rightarrow \int_E f \le \int_E g$

- $\int_E (f + g) = \int_E f + \int_E g$

- $\int_E (c f) = c \int_E f$

- $\int_a^b f = \int_a^c f + \int_c^b f $



### pf) for Simple Function $f$
Let $f, g$ be **simple measurable functions** on a measurable set $E \subset \mathbb{R}$:
\[
f = \sum_{i=1}^{n} a_i \chi_{A_i}, 
\qquad 
g = \sum_{j=1}^{m} b_j \chi_{B_j}.
\]
Then by definition,
\[
\int_E f = \sum_{i=1}^{n} a_i \mu(A_i),
\quad 
\int_E g = \sum_{j=1}^{m} b_j \mu(B_j).
\]


#### (1) Monotonicity  
If $f \le g$ on $E$, then for all $x$, $f(x) \le g(x)$.  
Construct a **common measurable partition**
\[
C_{ij} = A_i \cap B_j, \quad (i=1,\dots,n,\; j=1,\dots,m).
\]
On each $C_{ij}$, $f = a_i$, $g = b_j$, and $a_i \le b_j$.  
Then
\[
\int_E f = \sum_{i,j} a_i \mu(C_{ij}),
\quad
\int_E g = \sum_{i,j} b_j \mu(C_{ij}).
\]
Since $a_i \le b_j$ and $\mu(C_{ij}) \ge 0$ for all $(i,j)$,
\[
\int_E f \le \int_E g.
\]
<!-- % 공통분할에서 항별비교로 단조성 증명 -->


#### (2) Additivity
For $f$ and $g$ as above, on the same partition $C_{ij} = A_i \cap B_j$ we have  
\[
(f + g)(x) = a_i + b_j \quad \text{for } x \in C_{ij}.
\]
Hence,
\[
\int_E (f + g)
= \sum_{i,j} (a_i + b_j) \mu(C_{ij})
= \sum_{i,j} a_i \mu(C_{ij}) + \sum_{i,j} b_j \mu(C_{ij})
= \int_E f + \int_E g.
\]
<!-- % 단순함수의 합은 공통분할 위에서 항별합으로 표현 가능 -->


#### (3) Homogeneity
For $c \in \mathbb{R}$,
\[
(cf)(x) = c a_i \quad \text{on } A_i.
\]
Then by the definition of the integral,
\[
\int_E (cf)
= \sum_{i=1}^{n} (c a_i) \mu(A_i)
= c \sum_{i=1}^{n} a_i \mu(A_i)
= c \int_E f.
\]
<!-- % 정의에 직접 대입하면 성립 -->


#### (4) Additivity over Intervals
Let $E = \lbrack a, b \rbrack$ and $c \in (a, b)$.  
Define $E_1 = \lbrack a, c \rbrack$ and $E_2 = \lbrace c, b \rbrack$.  
Since $E = E_1 \cup E_2$ and $E_1 \cap E_2 = \emptyset$,
\[
\int_{a}^{b} f = \sum_{i=1}^{n} a_i \mu(A_i \cap E)
= \sum_{i=1}^{n} a_i \big( \mu(A_i \cap E_1) + \mu(A_i \cap E_2) \big)
= \int_{a}^{c} f + \int_{c}^{b} f.
\]
<!-- % 단순함수 정의에서 교집합 분할로부터 즉시 성립 -->


---

### Continuous Function

$f$ is continuous function iff
$\forall \varepsilon > 0, \; \exists \delta > 0 \; $ s.t. 
$\; |x-c| < \delta \Rightarrow |f(x) - f(c)| < \varepsilon$

If $M \subset \mathcal{R}$ is open, $f^{-1}(M)$ is open



### Theorem 
1. If $f$ is continuous, then $f$ is measurable

2. If $f$ is measurable and $g$ is continuous, then $g \circ f$ is measurable.  

3. If $f, g$ are measurable, then $f + g$, $\alpha f$, and $f \cdot g$ are measurable.  


### pf) $f + g$ is measurable

For measurable $f, g$, consider the set
\[
\lbrace x : f(x) + g(x) < a \rbrace
= \bigcup_{r \in \mathbb{Q}} \Big( \lbrace x : f(x) < r \rbrace \cap \lbrace x : g(x) < a - r \rbrace \Big).
\]


**(⊆)**  
Since $f(x) < a - g(x)$ and $\mathbb{Q}$ is **dense** in $\mathbb{R}$,  
there exists a rational number $r \in \mathbb{Q}$ such that  
\[
f(x) < r < a - g(x).
\]
Then $f(x) < r$ and $g(x) < a - r$,  
hence
\[
x \in \lbrace f < r \rbrace \cap \lbrace g < a - r \rbrace
\]
for that $r$,  
so $x$ belongs to the union on the right-hand side.


**(⊇)**  
Conversely, if $x \in \lbrace f < r \rbrace \cap \lbrace g < a - r \rbrace$ for some $r \in \mathbb{Q}$, then  
\[
f(x) + g(x) < r + (a - r) = a,
\]
so $x \in \lbrace f + g < a \rbrace$.


Since $f, g$ are measurable, each term on the right-hand side is measurable, and countable unions of measurable sets are measurable.  
Hence $f + g$ is measurable.  

### pf) $f \cdot g$ is measurable

Since $f, g$ are measurable and $f \cdot g = \tfrac{1}{2} \lbrack (f + g)^2 - f^2 - g^2 \rbrack$,

it suffices to show that $f \in \mathcal{M} \Rightarrow f^2 \in \mathcal{M}$

$\forall \alpha > 0$, $f(x)^2 < \alpha \quad \Leftrightarrow \quad - \sqrt{\alpha} < f(x) < \sqrt{\alpha}$

Therefore,
\[
\lbrace x : f(x)^2 < \alpha \rbrace
= \lbrace x : f(x) < \sqrt{\alpha} \rbrace
\cap
\lbrace x : f(x) > -\sqrt{\alpha} \rbrace.
\]

Since $f$ is measurable,
both sets $\lbrace f < \sqrt{\alpha} \rbrace$ and $\lbrace f > -\sqrt{\alpha} \rbrace$
are measurable.
Note that
\[
\lbrace f > -\sqrt{\alpha} \rbrace
= E \setminus \lbrace f \le -\sqrt{\alpha} \rbrace,
\]
and complements of measurable sets are measurable.
Hence their intersection,
\[
\lbrace f^2 < \alpha \rbrace
= \lbrace f < \sqrt{\alpha} \rbrace
\cap
\lbrace f > -\sqrt{\alpha} \rbrace,
\]
is measurable.


---

### Theorem

If $f_n$ are measurable, then
$\sup f_n$, $\inf f_n$, $\limsup f_n$, and $\liminf f_n$ are measurable.  


### pf)

\[
\lbrace x : \sup f_n(x) < a \rbrace 
= \bigcup_{N=1}^{\infty} \bigcap_{n\ge N} \lbrace x : f_n(x) < a \rbrace,
\]
which is measurable since it is formed by countable unions and intersections
of measurable sets.  


---

## $\lbrack$ Case 2 $\rbrack$ Measurable Function $f \ge 0$

$f : E \to \mathbb{R}$ be measurable and nonnegative.  

### Def.
\[
\int_E f = \sup \left\lbrace \int_E s : s \text{ is simple},\; 0 \le s \le f \right\rbrace.
\]


---

### Theorem
If $f \ge 0$ and measurable,  
$\exists$ an **increasing sequence** <$S_n$> of simple functions $\lbrace s_n \rbrace$ such that $s_n(x) \uparrow f(x)$

---

### Basic Properties of integra on $f \ge 0$

Let $A = \bigcup_{n=1}^{\infty} A_n$, where each $A_n$ is measurable and $f \ge 0$ on $A$.

\[
\int_A f = \sum_{n=1}^{\infty} \int_{A_n} f.
\]

### pf)

1. **Case 1: $f$ is simple.**  
   For a simple function $f = \sum c_i \chi_{E_i}$,
   \[
   \int_A f 
   = \sum_i c_i \mu(E_i \cap A)
   = \sum_i c_i \mu \left(\bigcup_{n=1}^{\infty} (E_i \cap A_n)\right)
   \]
   \[
   = \sum_i c_i \sum_{n=1}^{\infty} \mu(E_i \cap A_n)
   = \sum_n \int_{A_n} f,
   \]
   by countable additivity of measure.  
   

2. **Case 2: $f \ge 0$.**  
   **($\Rightarrow$)** $\forall s$ simple function s.t. $0 \le s \le f$,
   \[
   \int_A s = \sum \int_{A_n} s \le \sum \int_{A_n} f
   \]

   by definition of $\int_A f = \sup \lbrace \int_A s \rbrace$,
   \[
   \int_A f \le \sum \int_{A_n} f
   \]

   **($\Leftarrow$)** Given $\varepsilon \ge 0$ and given $n$,

   take a simple function $s_i$ defined on $A_i$ s.t.
   \[
   \int_{A_i} f < \int_{A_i} s_i + \frac{\varepsilon}{n}
   \]
   
   
   Define
   \[
   s(x) =
   \begin{cases}
   s_i(x), x \in A_i, i = 1, 2, \ldots, n \quad \\
   0, \text{otherwise}.
   \end{cases}
   \]

   Then $0 \le s \le f$, and $\int_{A_i} f < \int_{A_i} s < \frac{\varepsilon}{n}$.

   \[
   \sum_{i=1}^n \int_{A_i} f 
   < \sum_{i=1}^n \int_{A_i} s + \varepsilon
   = \int_{\bigcup_{i=1}^n A_i} s + \varepsilon
   \le \int_A s + \varepsilon
   \le \int_A f + \varepsilon.
   \]

   Since the above equation holds for all $n$ and $\varepsilon$,
   \[ \sum_{n=1}^{\infty} \int_{A_n} f \le \int_A f \]. $\square$

---
---

# (02b) Definition of Lebesgue Integral

## $\lbrack$ Case 3 $\rbrack$ $f$ is Real Value

$f : E \to \mathbb{R}^*$ be measurable and $f = f^+ - f^-$, where
\[
f_+ = \max \lbrace f, 0 \rbrace, \quad f_- = \min \lbrace f, 0 \rbrace
\]

### Def.
\[
\int_E f = \int_E f^+ - \int_E f^-.
\]

We say $f$ is **integrable** if both $\int_E f^+ < \infty$ and $\int_E f^- < \infty$.


---

### Comparison — Lebesgue vs Riemann



| Lebesgue | Riemann |
| -------- | -------- |
| measurable | Riemann integrable |
| integrable (absolutely summable) | improper integral converges |



> *Note:* Every Lebesgue integrable function is absolutely summable (integrable),  
but not for improper Riemann integral converges 
(partial sum converges to a finite value).


---

### Theorem 

Let $f : E \to \mathbb{R}^*$ be measurable.  

**Thm 1** $f$ is integrable $\; \Leftrightarrow \; \lvert f \rvert$ is integrable

**pf)**

Let $A = \lbrace x \in E : f(x) \ge 0 \rbrace$ and $B = \lbrace x \in E : f(x) < 0 \rbrace$.  
Then $E = A \cup B$, and  
\[
\int_E |f| = \int_A |f| + \int_B |f| = \int_A f_+ + \int_B f_-.
\]
Since both $\int_A f_+$ and $\int_B f_-$ are finite, $\int_E |f| < \infty$. 


**Thm 2** If $f$ is integrable, then $\lvert \int_E f \rvert \le \int_E \lvert f \rvert$

**pf)**

\[
\int_E f = \int_E f_+ - \int_E f_- \le \int_E f_+ \le \int_E \lvert f \rvert
\]
\[
\- \int_E f = \int_E f_- - \int_E f_+ \le \int_E f_- \le \int_E \lvert f \rvert
\]

Since $\int_E |f| < \infty$, $\int_E f < \infty$ and $-\int_E f < \infty$.
\[\Rightarrow \lvert \int_E f \rvert < \infty\].


---
---

# (02c) Integral of Complex-Valued Function

## $\lbrack$ Case 4 $\rbrack$ $f$ is Complex Value

$f : E \to \mathbb{C}$, where $f = u + iv$.

- $f$ is **measurable** if $u$ and $v$ are measurable.  
- $f$ is **integrable** if $\lvert f \rvert = \sqrt{u^2 + v^2}$ is integrable.  
- Denote by $L^1(E)$ the set of all integrable function $f : E \to \mathbb{C}$.


### Def.
\[
\int_E f = \int_E u + i \int_E v.
\]

---

### Theorem

$f : E \to \mathbb{C}$ is integrable, then $\lvert \int_E f \rvert \le \int_E \lvert f \rvert$

> *Note:* <span style="color:red">Refer to how the **Cauchy–Schwarz inequality** is proved in a **complex vector space over a measure space** when writing this proof.</span>


---


### Definition — Almost Everywhere (a.e.)
<!-- % 거의 모든 점에서 (a.e.) 정의 -->

Let $P(x)$ be a property about $x$.  
We say that **$P$ holds almost everywhere (a.e.)** if  
\[
\mu(\lbrace x \mid P(x) \text{ does not hold at } x \rbrace) = 0.
\]

### Theorem 1.
If $f \ge 0$ and $\int_E f = 0$, then $f = 0$ a.e.

**pf)**  
Let $E_n = \lbrace x : f(x) > 1/n \rbrace$.  

Then $0 \le \frac{1}{n}\mu(E_n) \le \int_{E_n} f \le \int_E f = 0$,  

which implies $\mu(E_n) = 0$ for all $n$.  

Hence,
\[
\mu(\lbrace x : f(x) > 0 \rbrace)
= \mu \left( \bigcup_{n=1}^{\infty} E_n \right)
= 0 \; \square
\]

### Theorem 2.

If $f \in L^1(E)$ and $\int_D f = 0$ for every measurable set $D \subseteq E$, then $f = 0$ a.e.

**pf)**  

If $f = \operatorname{Re}(f) + i \operatorname{Im}(f)$,  
then
\[
\int_E f = \int_E \operatorname{Re}(f) + i \int_E \operatorname{Im}(f)
\]

Let $D = \lbrace x \in E \mid Ref(x) \ge 0 \rbrace \; \Rightarrow \; (Ref)_+ = 0$ a.e. on $D$

Then $\operatorname{Re}(f)$ and $\operatorname{Im}(f)$ are $0$ a.e., and $f = 0$ a.e.


### Theorem 3.

If $f : \lbrack a, b \rbrack \to \mathbb{R}^*$ is measurable and $\int_{\lbrack a, x \rbrack} f = 0$ for all $x$,  
then $f = 0$ a.e.  

**pf)** 

> *Note:* <span style="color:red">Do it yourself</span>

---
---

# (02d) Example of Non-Measurable Set

Let $x, y \in \lbrack 0, 1 )$, and define  
\[
x \sim y \quad \Longleftrightarrow \quad x - y \in \mathbb{Q}.
\]

- $\sim$ is an **equivalence relation** on $\lbrack 0, 1 \rbrack$.

---

### Construction

Let $P$ denote a set obtained by choosing **exactly one representative** from each equivalence class of $\sim$ within $\lbrack 0, 1 \rbrack$.  
In other words, when the interval $\lbrack 0, 1 \rbrack$ is partitioned into equivalence classes under $\sim$,  
we pick one element from each class and collect them together to form $P$.  



For each rational number $r \in \mathbb{Q} \cap \lbrack 0, 1 )$, define  
\[
P_r = \lbrack P_{r1} \;\cup\; P_{r2} \rbrack 
= \lbrack r + P \cap \lbrack 0, 1-r) \rbrack \;\cup\; \lbrack (r - 1) + P \cap \lbrack 1-r, 1 ) \rbrack.
\]

$P$         |············· r ························· 1-r ···················|
$P_{r1}$    |·················■■■■■■■■■■■|
$P_{r2}$    |■■■·······································································|


Then
\[
\bigcup_{r \in \mathbb{Q} \cap \lbrack 0, 1 )} P_r = \lbrack 0, 1 ).
\]


---

### Contradiction Argument
Assume $P$ is measurable.  
Since translation preserves measure, $\mu(P_r) = \mu(P)$ for all $r$.  
Hence,
\[
1 = \mu \, \left(\lbrack 0, 1 ) \right)
= \sum_{r \in \mathbb{Q} \cap \lbrack 0, 1 \rbrack} \mu(P_r).
\]
However, the set of rationals in $\lbrack 0, 1 )$ is **countable**,  
so if $\mu(P) > 0$, the right-hand side diverges (countable sum),  
and if $\mu(P) = 0$, it sums to $0$.  

In either case, contradiction.  
Therefore, $P$ is **non-measurable**.  
$\square$
<!-- % 평행이동 불변성과 가산 합 성질이 모순을 일으킴 -->

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

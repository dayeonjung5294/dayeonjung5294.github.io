---
layout: post
title: "Real Analysis Lecture 4: Lebesgue Integration and Differentiation"
date: 2025-09-28
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.

# (04a) Differentiation of Monotone Increasing Functions <!-- % 단조증가함수의 미분 -->

## Theorem 4-1 (Lebesgue)
If $f$ is monotone increasing on $I \subset \mathbb{R}$, then $f$ is **differentiable almost everywhere (a.e.)** on $I$.



### pf)

For $f : I \to \mathbb{R}$, define
\[
D^+ f(x) = \limsup_{h \to 0^+} \frac{f(x+h) - f(x)}{h}, \quad
D_- f(x) = \liminf_{h \to 0^+} \frac{f(x) - f(x-h)}{h}.
\]

Let  
\[
A = \lbrace x \in I : D_- f(x) < D^+ f(x) \rbrace.
\]
For $r < s \in \mathbb{R}$, put  
\[
A_{r,s} = \lbrace x \in I : D_- f(x) < r < s < D^+ f(x) \rbrace.
\]
We want to show that $\mu(A_{r,s}) = \alpha$.


### Step (i)

Given $\varepsilon > 0$, take an open set $U$ such that  
\[
A_{r,s} \subset U, \quad \mu(U) < \alpha + \varepsilon.
\]

For $x \in A_{r,s}$, choose $h_1^x, h_2^x, \dots \to 0$ such that $[x-h_i^x, x] \subset U$.

Then $D_- f(x) < r$ implies $f(x) - f(x - h_i^x) < r h_i^x$.

Apply **Vitali’s Covering Lemma** to  
\[
\bigcup_{x \in A_{r,s}} \lbrace \lbrack x - h_i^x, x \rbrack, i = 1,2,\dots \rbrace,
\]
to obtain finitely many disjoint intervals  
\[
I_A := \lbrack x_1 - h_1, x_1 \rbrack \cup \lbrack x_2 - h_2, x_2 \rbrack \cup \dots \cup \lbrack x_n - h_n, x_n \rbrack
\]
such that $\mu(A_{r,s} \backslash I_A) < \varepsilon$.

Then
$
\sum_{i=1}^n [f(x_i) - f(x_i - h_i)] < r \sum_{i=1}^n h_i
< r \mu(U) < r (\alpha + \varepsilon).
$


### Step (ii)

Let $B = A_{r,s} \cap I_A$. Then $\mu(B) > \alpha - \varepsilon$.

For $y \in B$, take $k_1^y, k_2^y, \dots \to 0$ such that  $[y, y+k^y] \subset I_A$.

Then $D^+ f(x) > s$ implies 
$
f(y + k_j^y) - f(y) > s k_j^y.
$

Apply Vitali again to obtain finitely many disjoint intervals   
\[
I_B := \lbrack y_1, y_1 + k_1 \rbrack \cup \lbrack y_2, y_2 + k_2 \rbrack \cup \dots \cup \lbrack y_m, y_m + k_m \rbrack
\]
such that  $\mu(B \backslash I_B) < \varepsilon$.

Then
$
\sum_{j=1}^m [f(y_j + k_j) - f(y_j)] > s \sum_{j=1}^m k_j.
$

Since $\mu(B \cap I_B) > \alpha - 2\varepsilon$,
$
\sum_{j=1}^m [f(y_j + k_j) - f(y_j)] > s (\alpha - 2\varepsilon).
$


### Step (iii)

By Step (i) and (ii), since
\[
\sum_{j=1}^m \lbrack f(y_j + k_j) - f(y_j) \rbrack < \sum_{i=1}^n \lbrack f(x_i) - f(x_i - h_i) \rbrack,
\]

$s(\alpha - 2\varepsilon) < r(\alpha + \varepsilon)$,  which implies $\alpha = 0 \quad a.e.$



Therefore $D^- f(x) = D^+ f(x)$ for almost every $x \in I$,  
and thus $f$ is differentiable a.e.

<span style="color:red">(Do it yourself for all below situation)</span> 
\[
D^- f(x) = \limsup_{h \to 0^+} \frac{f(x) - f(x-h)}{h},
\quad
D_+ f(x) = \liminf_{h \to 0^+} \frac{f(x+h) - f(x)}{h}.
\]

---
---

# (04b) Differentiation of Integrals <!-- % 적분의 미분 -->

## Theorem 4-2
Let $f : [a,b] \to \mathbb{R}$ be monotone increasing.  
Then $f'$ is measurable and
\[
\int_a^b f'(x)\,dx \le f(b) - f(a).
\]
<!-- % 단조함수의 미분가능성과 적분 부등식 -->

### pf)
Let
\[
g_n(x) = \frac{f(x+h_n) - f(x)}{h_n}, \quad h_n \to 0.
\]
Since $f$ is measurable, $g_n$ is measurable, and $g_n \to f'$ implies $f'$ is measurable.

By **Fatou’s Lemma**, since $g_n \ge 0$,
\[
\int_a^b f' \le \liminf_n \int_a^b g_n
= \liminf_n \lbrace \frac{1}{h_n} \int_b^{b+h_n} f - \frac{1}{h_n} \int_a^{a+h_n} f \rbrace
\le f(b) - f(a).
\]

---

## Theorem 4-3
Let $f : E \to \mathbb{R}$ be integrable ($f \in L^1(E)$).  
Then $\forall \; \varepsilon > 0$, $ \exists \; \delta > 0$ such that  
\[
A \subset E, \ \mu(A) < \delta \Rightarrow \int_A \lvert f \rvert < \varepsilon.
\]
<!-- % 적분가능함수의 절대연속성 -->

### pf)
Let $f_n(x) = \min \lbrace f(x), n \rbrace$.

Then $f_n$ is bounded and 
$
\lvert f_n(x) \rvert \nearrow \lvert f(x) \rvert \quad \text{as } n \to \infty.
$


Hence, by the Monotone Convergence Theorem,
\[
\int_E (|f|-|f_n|)\,d\mu \;\downarrow\; 0 .
\]

Fix $N$ so large that
\[
\int_E (|f|-|f_N|)\,d\mu < \frac{\varepsilon}{2}.
\]

Set $\delta:=\dfrac{\varepsilon}{2N}$. For any measurable $A\subset E$ with $\mu(A)<\delta$,
\[
\int_A |f|\,d\mu
= \int_A |f_N|\,d\mu + \int_A (|f|-|f_N|)\,d\mu
\le \int_A N\,d\mu + \int_E (|f|-|f_N|)\,d\mu
\le N\,\mu(A) + \frac{\varepsilon}{2}
< N\cdot\frac{\varepsilon}{2N} + \frac{\varepsilon}{2}
= \varepsilon .
\]


---

## Theorem 4-4
Let $f : [a,b] \to \mathbb{R}$ be integrable, and define
\[
F(x) = f(a) + \int_a^x f(t)\,dt.
\]
Then $F'(x) = f(x)$ **almost everywhere (a.e.)**.
<!-- % 적분함수의 미분 정리 -->

### pf)
Let $f \ge 0$ and $h_n \to 0$. Define
\[
f_n(x) = \frac{F(x+h_n) - F(x)}{h_n}
= \frac{1}{h_n} \int_x^{x+h_n} f(t)\,dt.
\]
By the **Lebesgue Differentiation Theorem**, $f_n \to F'$ a.e.  

### Step (i)
Let $0 < f \le M$. (Bounded)

\[
\int_a^x f_n
= \frac{1}{h_n} \int_x^{x+h_n} f - \frac{1}{h_n} \int_a^{a+h_n} f \;
\rightarrow \; F(x) - F(a) = \int_a^x f_n
\]

Since $\int_a^b f_n \to \int_a^b f$ when bounded, $\int_a^x(F' - f) = 0$

This satisfies for all $x$,
\[
F'(x) = f(x) \text{ a.e.}
\]

### Step (ii)
Let $f_n(x) = \min \lbrace f(x), n \rbrace$.

Then
\[
F(x) - F(a) = \int_a^x (f - f_n) + \int_a^x f_n.
\]
Since $(f - f_n) \ge 0$ and $f_n$ is bounded, $F'(x) \ge f_n(x)$.  
Taking $n \to \infty$ gives $F' \ge f$, and since we already know
$
\int_a^b F' \le \int_a^b f = F(b) - F(a),
$

we conclude 
\[
\int_a^b F' = \int_a^b f = F(b) - F(a) 
\;\Rightarrow\;
\int_a^b (F' - f) = 0.  
\]

Since the integral of a non-negative function is zero,
\[
F'(x) = f(x) \text{ a.e.}
\]


---

## Fubini Theorem
If $f_n : [a,b] \to \mathbb{R}$ is increasing for all $n$ and  $\sum f_n = s$ converges pointwise,  
then \[S' = \sum f_n' \text{ a.e.}\]
<!-- % 증가함수열의 도함수 합 공식 -->

---
---

# (04c) Absolutely Continuous Functions <!-- % 절대연속함수 -->

## Definition (Bounded Variation)
A function $f : [a,b] \to \mathbb{R}$ is of **bounded variation**  
if for a partition $P = \lbrace x_0, x_1, \dots, x_n \rbrace$,
\[
V_a^b(f,P) = \sum_{i=1}^n \lvert f(x_i) - f(x_{i-1}) \rvert \le V
\]
for all $P$.  
<!-- % 유계변동함수 정의 -->

---

## Definition (Absolutely Continuous)
$F$ is **absolutely continuous** if

$\forall \varepsilon > 0$, $\exists \delta > 0$ s.t. for any finite disjoint intervals $\lbrack x_i, y_i \rbrack$ with  
$\\mu \left([x_1,y_1] \cup [x_2,y_2] \cup \ldots \cup [x_n,y_n] \right) < \delta$, we have
\[
\sum_{i=1}^n \lvert F(y_i) - F(x_i) \rvert < \varepsilon.
\]

---

## Properties

- Every **monotone increasing function** is of **bounded variation**.  
- The **difference of two monotone functions** can represent any function of **bounded variation**.  
- If $F$ is absolutely continuous, then $F$ is uniformly continuous.  

\[
\forall \varepsilon > 0, \exists \delta > 0
\ \text{s.t. } \mu(\lbrack x,y \rbrack) < \delta \Rightarrow \lvert F(y) - F(x) \rvert < \varepsilon.
\]

- Every **absolutely continuous function** is of **bounded variation**.


---
---

# (04d) Integration of Differentials <!-- % 미분의 적분 -->

## Lemma 4-1
If $f : [a,b] \to \mathbb{R}$ is **absolutely continuous** and $f'(x) = 0$ a.e.,  
then $f$ is **constant**.  
<!-- % 절대연속함수의 도함수가 0이면 상수함수 -->


### pf)
Let $c \in [a,b]$, $\varepsilon > 0$, and $\alpha > 0$.  
Define
\[
E = \lbrace x \in \lbrack a,c \rbrack : f'(x) = 0 \rbrace.
\]
For each $x \in E$, choose $h_x > 0$ such that  
\[
\lbrack x, x + h_x \rbrack \subset \lbrack a,c \rbrack, \quad \lvert f(x+h_x) - f(x) \rvert < \alpha h_x < \alpha(c-a).
\]

By **Vitali’s covering lemma**, choose finitely many disjoint intervals  
\[
\lbrack x_1, x_1 + h_1 \rbrack, \lbrack x_2, x_2 + h_2 \rbrack, \dots, \lbrack x_n, x_n + h_n \rbrack
\]
s.t.
\[
\mu\big(\lbrack a,c \rbrack \setminus \bigcup_i \lbrack x_i, x_i + h_i \rbrack\big) < \delta.
\]

By absolute continuity,
\[
\sum_i \lvert f(x_i + h_i) - f(x_i) \rvert < \varepsilon.
\]
Then
\[
\lvert f(c) - f(a) \rvert < \varepsilon + \alpha (c - a).
\]
Since $\varepsilon, \alpha$ are arbitrary, $f(c) = f(a)$, hence $f$ is constant.

---

## Theorem 4-5
A function $f : [a,b] \to \mathbb{R}$ is **absolutely continuous** if and only if  
- (i) $ f \text{ is differentiable a.e.}$
- (ii) $ f' \in L^1([a,b])$
- (iii) $ \int_a^x f'(t)\,dt = f(x) - f(a) , \quad \forall x \in [a,b]$


### pf)

#### (⇐)
If $f$ satisfies the three conditions, then $\forall \varepsilon > 0$, $\exists \delta > 0$ s.t. for any disjoint intervals  $\lbrack x_i, y_i \rbrack$ with $\sum_i (y_i - x_i) < \delta$,  
\[
\sum_i \lvert f(y_i) - f(x_i) \rvert
= \sum_i \left\lvert \int_{x_i}^{y_i} f'(t)\,dt \right\rvert
\le \int_{\cup_i [x_i,y_i]} \lvert f'(t) \rvert \,dt < \varepsilon.
\]
Hence $f$ is absolutely continuous. 


#### (⇒)

**(i)**
If $f$ is absolutely continuous, then it is of bounded variation,  
and thus it can be expressed as the difference of two increasing functions $f_1, f_2$ that are differentiable a.e.

**(ii)**
Let $f = f_1 - f_2$.  
Then both $f_1', f_2' \in L^1([a,b])$, and
\[
\int_a^b \lvert f' \rvert \le \int_a^b \lvert f_1' \rvert + \int_a^b \lvert f_2' \rvert
\le \lvert f_1(b) - f_1(a) \rvert + \lvert f_2(b) - f_2(a) \rvert < \infty.
\]
Thus $f' \in L^1([a,b])$.


**(iii)**
Let $g(x) = f(a) + \int_a^x f'(t)\,dt.$

Then $g$ is absolutely continuous and $g' = f'$ a.e. Hence $(f - g)' = 0$ a.e., 

By the **Lemma 4-1**, $f - g$ is constant.  
Then we get
\[
f(x) = g(x) = f(a) + \int_a^x f'(t)\,dt.
\]

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

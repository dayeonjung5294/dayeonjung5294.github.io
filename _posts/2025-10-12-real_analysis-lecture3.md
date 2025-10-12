---
layout: post
title: "Real Analysis Lecture 3: Convergence Theorem of Integral"
date: 2025-10-12
categories: [Real_analysis]
use_math: True
---

# (03a) Monotone Convergence Theorem <!-- % 단조수렴정리 -->

## Monotone Convergence Theorem

Let $\lbrace f_n \rbrace$ be a sequence of measurable functions s.t. $0 \le f_n \nearrow f$.
\[
\Rightarrow \quad
\lim_{n \to \infty} \int_E f_n = \int_E \left( \lim_{n \to \infty} f_n \right).
\]


### pf)

Let $\int_E f_n \nearrow L$ ($\lim_{n \to \infty} \int_E f_n := L$)

**($\Rightarrow$)**

$\forall n, f_n \le f \;\Rightarrow\; \int_E. f_n \le \int_E f$

Then, 
\[ L ( = \lim_{n \to \infty} \int_E f_n) \le \int_E f \]

**($\Leftarrow$)**

Let $s$ be a simple function such that $0 \le s \le f$, and take $c \in (0,1)$ and define
\[
E_n = \lbrace x \in E \mid c \cdot s(x) < f_n(x) \rbrace.
\]
Then
\[
E_n \nearrow E = \bigcup_{n=1}^{\infty} E_n.
\]

Since $0 \le c \cdot s \cdot \chi_{E_n} \le f_n$ for all $n$, we have
\[
\int_E c s \chi_{E_n} \le \int_E f_n.
\]

By continuity of measure ($\lim_n \mu(E_n) = \mu(\lim_n E_n)$),
\[
\lim_{n \to \infty} \int_E c s \chi_{E_n}
= c \lim_{n \to \infty} \int_{E_n} s
= c \int_E s.
\]

Thus,
\[
c \int_E s
\le \lim_{n \to \infty} \int_E f_n
= L.
\]

Letting $c \to 1$, we get $\int_E s \le L$ for all simple $s \le f$.

Hence,
\[
\int_E f = \sup \lbrace \int_E s \rbrace \le L.
\]

---

## Fatou’s Lemma <!-- % Fatou 보조정리 -->

If $0 \le f_n$, then
\[
\int_E \left( \liminf_{n \to \infty} f_n \right) \le \liminf_{n \to \infty} \int_E f_n.
\]


### pf)

Let $f = \liminf f_n$ and define
\[
g_k = \inf \lbrace f_k, f_{k+1}, f_{k+2}, \dots \rbrace,
\quad \text{so that } g_k \nearrow f.
\]

By MCT,
\[
\int_E f 
= \int_E \left( \lim_{k \to \infty} g_k \right)
= \lim_{k \to \infty} \int_E g_k.
\]

Since $g_k \le f_n$ for all $n \ge k \; (\forall k)$,
\[
\int_E g_k \le \int_E f_n
\;\Rightarrow\;
\int_E g_k \le \inf_{n \ge k} \int_E f_n.
\]
Taking limits,
\[
\lim_{k \to \infty} \int_E g_k
= \int_E f 
\le \lim_{k \to \infty} \inf_{n \ge k} \int_E f_n
= \liminf_{n \to \infty} \int_E f_n.
\]

---

## Corollary

If $f_n \ge 0$, then
\[
\int_E \Big( \sum_{n=1}^\infty f_n \Big)
= \sum_{n=1}^\infty \int_E f_n.
\]

### pf)
Let the partial sums be
\[
s_N(x)=\sum_{n=1}^N f_n(x), \qquad x\in E.
\]

Then each $s_N$ is measurable and nonnegative, and
\[
s_N(x)\nearrow s(x):=\sum_{n=1}^\infty f_n(x) \in \lbrack 0, \infty \rbrack
\quad \forall x \in E.
\]

By MCT,
\[
\int_E s \,
= \lim_{N\to\infty} \int_E s_N.
\]

By linearity, for each finite $N$,
\[
\int_E s_N \, d\mu
= \int_E \sum_{n=1}^N f_n \, d\mu
= \sum_{n=1}^N \int_E f_n \, d\mu,
\]
so taking limits and using monotonicity of the partial sums yields
\[
\int_E \Big( \sum_{n=1}^\infty f_n \Big) \, d\mu
= \lim_{N\to\infty} \sum_{n=1}^N \int_E f_n \, d\mu
= \sum_{n=1}^\infty \int_E f_n \, d\mu .
\]


---
---

# (03b) Lebesgue Dominated Convergence Theorem <!-- % 르벡 수렴정리 -->

## Theorem

Let $\lbrace f_n \rbrace$ be a sequence of measurable functions on $E$ such that  

\[
\exists g \in L^1(E) \text{ with } \lvert f_n \rvert \le g \text{ for all } n, 
\; \text{and} \; \lim_{n \to \infty} f_n(x) = f(x).
\]

Then
\[
\int_E f = \lim_{n \to \infty} \int_E f_n.
\]


### pf)

Since $\lvert f - f_n \rvert \le 2g$, $\; 2g - \lvert f - f_n \rvert \ge 0$.

By **Fatou’s lemma**,  
\[
\int_E \liminf_n (2g - \lvert f - f_n \rvert)
\le
\liminf_n \int_E (2g - \lvert f - f_n \rvert).
\]

Thus,
\[
\int_E 2 g \le \int_E 2 g - \int_E \limsup_n \lvert f - f_n \rvert.
\]

Since $\int_E g < \infty$, we get
\[
\limsup_n \int_E \lvert f - f_n \rvert \le 0.
\]

i.e.
\[
0 \le \liminf_n \int_E \lvert f - f_n \rvert \le \limsup_n \int_E \lvert f - f_n \rvert \le 0.
\]

Therefore,
\[
\int_E \lvert f - f_n \rvert \to 0.
\]
---

## Levi’s Convergence Theorem

If $\sum_{n=1}^\infty \int_E \lvert f_n \rvert < \infty$, then

1. $f(x) = \sum_{n=1}^\infty f_n(x)$ exists a.e.,  
2. \[
   \int_E f = \sum_{n=1}^\infty \int_E f_n.
   \]
<!-- % 절대적 수렴이면 적분의 급수와 함수의 급수가 교환 가능 -->

---

## Applications and Related Results

1. If $\sum_{n=1}^{\infty} \lvert a_n \rvert < \infty$, then $\sum_{n=1}^{\infty} a_n$ converges. 
2. If $\sum_{n=1}^{\infty}  {\lvert \lvert f_n \rvert \rvert}_{\sup} < \infty$,  then $f(x) = \sum_{n=1}^{\infty} f_{n}(x)$ is continuous.
3. If $\sum_{n=1}^{\infty}  {\lvert \lvert f_n \rvert \rvert}_{1} < \infty$,  then $f(x) = \sum_{n=1}^{\infty} f_{n}(x) \in L^1$.


> *Note:*  
> Application 3. is a new tool that defines a suitable integrable function.

---

## Differentiation Under the Integral Sign

Let $f : I \times J \to \mathbb{C}$, and define  
\[
F(x) = \int_J f(x, y) \, dy.
\]

Suppose there exists $g \in L^1(J)$ such that  
\[
\lvert D_x f(x, y) \rvert = \left\lvert \frac{\partial f}{\partial x}(x, y) \right\rvert \le g(y).
\]
Then $F'(x)$ exists and
\[
\frac{d}{dx} \int_J f(x, y) \, dy = \int_J D_x f(x, y) \, dy.
\]
<!-- % 적분기호 아래 미분: 지배수렴정리를 이용한 미분과 적분의 교환 정리 -->

### Proof Sketch

Let $h_n \to 0$, and write
\[
\frac{F(x_n) - F(x)}{x_n - x}
= \int_J \frac{f(x_n, y) - f(x, y)}{x_n - x} \, dy.
\]
By **LDCT (Lebesgue Dominated Convergence Theorem)**,
\[
\lim_{n \to \infty} \frac{F(x_n) - F(x)}{x_n - x}
= \int_J D_x f(x, y) \, dy.
\]
<!-- % LDCT를 사용한 미분과 적분의 교환 증명 -->

# (03c) Riemann and Lebesgue Integrals <!-- % 리만적분과 르벡적분 -->

## Definition

Let a partition  
\[
P = \lbrace a = x_0, x_1, x_2, \dots, x_{n-1}, x_n = b \rbrace
\]
of the interval $[a,b]$ be given.

Then the **lower sum** and **upper sum** of $f$ with respect to $P$ are  
\[
L_P = L^a_b(f, P), \quad U_P = U^a_b(f, P).
\]
<!-- % 리만 하합/상합 -->

Here, $L_P$ can be viewed as a step function constructed from the **lower sums** of $f$.  
<!-- % low sum으로 만든 step 함수 -->

Let $\lVert P \rVert = \max_i (x_i - x_{i-1})$.  
If $P_1 \subset P_2 \subset \cdots$ and $\lVert P_n \rVert \to 0$,  
then
\[
L_{P_n} \nearrow f, \quad U_{P_n} \searrow f.
\]
By the **Monotone Convergence Theorem**, we have
\[
\lim_{n \to \infty} \int_{[a,b]} L_{P_n}
= \int_{[a,b]} f
= \lim_{n \to \infty} \int_{[a,b]} U_{P_n}.
\]
<!-- % 단조수렴정리를 이용한 리만적분과 르벡적분의 연결 -->

---

## Relationship Between Integrals

The function $f$ is **Riemann integrable** on $[a,b]$ if and only if
\[
\int_a^b f = \int_a^b f.
\]

Equivalently,
\[
\int_a^b (U - L) = 0,
\]
which implies $U = L$ a.e.  
Hence, $f$ is Riemann integrable iff $f$ is **continuous almost everywhere**.
<!-- % 불연속점이 measure 0이면 리만적분 가능 -->

> *Riemann integrability criterion:*  
> $f$ is Riemann integrable $\iff$ the set of discontinuities of $f$ has measure $0$.

---

# (03d) Vitali Covering Lemma <!-- % 비탈리 덮음정리 -->

## Statement

Let $E$ be a measurable set with $\mu(E) < \infty$,  
and let $\mathcal{F}$ be a family of closed intervals.

Then, for every $\varepsilon > 0$,  
there exist finitely many **disjoint intervals** $I_1, I_2, \dots, I_n \in \mathcal{F}$  
such that
\[
\mu\Big( E \setminus \bigcup_{k=1}^n I_k \Big) < \varepsilon.
\]
<!-- % 유한 개의 서로소한 닫힌구간으로 거의 다 덮을 수 있음 -->

---

## Proof Sketch

Let $U$ be an open set such that $E \subset U$ and $\mu(U) < \infty$.  
By the Vitali property of $\mathcal{F}$, for each $x \in E$, there exists $I_x \in \mathcal{F}$ such that $x \in I_x \subset U$.

By countable additivity,
\[
\sum_k \mu(I_k) < \mu(U) < \infty.
\]
We construct intervals inductively:

- Choose $I_1$ from $\mathcal{F}$ arbitrarily.  
- Let $I_2$ be chosen so that $\mu(I_2) > \frac{1}{2} \mu(I_1)$ and $I_2 \cap I_1 = \emptyset$.  
- Continue selecting intervals $I_3, I_4, \dots$ satisfying  
  $\mu(I_{k+1}) > \frac{1}{2} \mu(I_k)$ and $I_j \cap I_i = \emptyset$ for $i < j$.  

If this process terminates, the measure of uncovered points is $0$.  
Otherwise, since $\sum \mu(I_k) < \infty$, there exists $n$ such that  
\[
\sum_{k=n+1}^\infty \mu(I_k) < \frac{\varepsilon}{5}.
\]

Let
\[
D = E \setminus \bigcup_{k=1}^n I_k.
\]
For $y \in D$, define $I_y$ as an interval in $\mathcal{F}$ centered at $y$.

By the choice of $n$,
\[
\mu(D) \le \sum_{k>n} \mu(I_k) < \varepsilon.
\]
Thus,
\[
\mu\Big( E \setminus \bigcup_{k=1}^n I_k \Big) < \varepsilon.
\]
$\square$
<!-- % 비탈리 덮음정리 증명 개요 -->

---

> *Note:*  
> The Vitali covering lemma is essential in the proof of the **Lebesgue Differentiation Theorem**,  
> providing a method to approximate measurable sets by disjoint intervals.
<!-- % 르벡 미분정리 증명에 사용되는 핵심 도구 -->




---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

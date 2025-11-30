---
layout: post
title: "Real Analysis Lecture 6: Two-sided Measure and Integration"
date: 2025-10-12
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.


# (06a) Pointwise Convergence and Uniform Convergence <!-- % 점별수렴과 고른수렴 -->

## Lemma 6-1
Let $E \subset \mathbb{R}$ with $\mu(E) < \infty$.  

Let $\{f_n\}$ be a sequence of measurable functions on $E$ such that $f_n \to f$ pointwise a.e.  

Then $\forall \varepsilon > 0$,  $\exists\;\delta > 0, \; N \in \mathbb{N}$ s.t.

\[
\mu(A) < \delta \Rightarrow n \ge N, \ x \in E \setminus A \ \Rightarrow\ \lvert f_n(x) - f(x) \rvert < \varepsilon.
\]

### pf)

Fix $\varepsilon>0$ and define
\[
A_n \;=\; \bigcup_{k \ge n} \,\lbrace x \in E : \lvert f_k(x)-f(x) \rvert \ge \varepsilon \rbrace .
\]

Then $\{A_n\}$ is decreasing and
\[
\bigcap_{n=1}^\infty A_n \;\subseteq\; \lbrace x \in E : \lim_{n\to\infty} f_n(x) \neq f(x) \rbrace .
\]

Since $f_n \to f$ a.e., $\;\mu \left(\bigcap_{n=1}^\infty A_n\right)=0$, hence $\mu(A_n)\downarrow 0$.

Let $\delta>0$ be arbitrary. Choose $N$ so that $\mu(A_N)<\delta$, and set $A:=A_N$. 

Then:

1) $\mu(A)=\mu(A_N)<\delta$.

2) If $x \in E \setminus A=E \setminus A_N$, 
\[
x \notin \bigcup_{k\ge N} \lbrace \lvert f_k(x)-f(x) \rvert \ge \varepsilon \rbrace
\;\Longrightarrow\;
\lvert f_k(x)-f(x) \rvert < \varepsilon \ \text{for all } k\ge N .
\]

In particular, for every $n\ge N$ and every $x\in E\setminus A$, $\lvert f_n(x)-f(x) \rvert < \varepsilon$.

Thus the convergence is uniform on $E\setminus A$.

---

## Egoroff’s Theorem
Let $E \subset \mathbb{R}$ with $\mu(E) < \infty$ and $f_n \to f$ pointwise a.e. on $E$.

Then $\forall \varepsilon > 0$, $\exists \; A \subset E$ s.t.
\[
\mu(A) < \varepsilon, \quad
f_n \to f \text{ uniformly on } E \setminus A.
\]

### pf)
Using the previous **Lemma 6-1** with fixed $\varepsilon = 1/m > 0$ and let $\varepsilon_m = \varepsilon / 2^m$, $\exists \, A_m, N_m$ s.t. $\mu(A_m) < \varepsilon / 2^m$.

For $x \in E \setminus A_m, \; n \ge N_m \Rightarrow \lvert f_m (x) - f(x) \rvert < 1/m$



Let
\[
A = \bigcup_{m=1}^\infty A_m.
\]

Then $n \ge N_m$:
\[
\Rightarrow \sup_{x \in E \setminus A} \lvert f_m(x) - f(x) \rvert
\le \sup_{x \in E \setminus A_m} \lvert f_m(x) - f(x) \rvert
< \frac{1}{m}.
\]

Thus for $x \in A \setminus E$, $f_n(x) \to f(x)$ **uniformly**. 

---
---

# (06b) Definition of Two-sided Measure <!-- % 양측도의 정의 -->

Let $(X, \mathcal{S}, \mu)$ be a **measure space**, where:

1. $\mathcal{S} \subset 2^X$ is a **σ-algebra**, satisfying  
   - \emptyset \in \mathcal{S}, \; X \in \mathcal{S}
   - $E \in \mathcal{S} \Rightarrow E^c \in \mathcal{S}$
   - $\{E_i\} \subset \mathcal{S} \Rightarrow \bigcup_i E_i \in \mathcal{S}$

2. $\mu : \mathcal{S} \to [0,\infty]$ satisfies  
   - $\mu\left(\bigcup_i E_i\right) = \sum_i \mu(E_i)$ for disjoint $\{E_i\}$ (**countable additivity**)

---
---

# (06c) Two-sided Measure and Integration <!-- % 양측도와 적분 -->

## Examples
1. $(X, 2^X, c)$ with $c(A) = \text{#}A$ (**counting measure**)
2. $(X, 2^X, \delta_x)$ with $x \in X$, $\delta_x(A) = I(x \in A)$ (**indicator measure**)
3. for $f : \mathcal{R} \to [0, \infty]$, then the **integral with respect to a measure** is written
\[
\int_{ \bigcup_{n} E_n } f = \sum_n \int_{E_n} f,
\quad
\mathcal{V} (E) = \int_E f.
\]

---

## Definition (Measurable and Simple Functions)
1. $f : X \to [0,\infty]$ is **measurable** if  
   \[
   f^{-1}((a,\infty)) \in \mathcal{S}, \quad \forall a > 0.
   \]

2. A function $s : X \to [0,\infty]$ is **simple** if it is measurable and has finite range:  
   \[
   s = \sum_{i=1}^{\infty} c_i \chi_{E_i}, \, E_i \in \mathcal{S} \;
   \longrightarrow \; \int_E s = \sum_{i=1}^{\infty} c_i \mu(E_i).
   \]

3. For a measurable $f : X \to [0,\infty]$, define  
   \[
   \int_X f = \sup \Big \lbrace \int_E s : 0 \le s \le f,\ s \text{ is simple} \Big \rbrace .
   \]

4. For $f : X \to \mathcal{C}$ and for non-negative real-valued functions $f_1, f_2, f_3, f_4$,  
   \[
   f = (f_1 - f_2) + i (f_3 - f_4)
   \]

---
---

# (06d) Various Lebesgue Spaces <!-- % 여러가지 르벡공간 -->

## Theorem
Let $\mu(X) < \infty$ and $F \subset \mathbb{C}$ closed,$f \in L^1(X, \mathcal{S}, \mu)$.

If $F \in \mathcal{S}, \; \mu(E) > 0$ and $\frac{1}{\mu(E)} \int_E f \, d\mu \in F$,
\[
f(x) \in F \text{ a.e.}
\]

### pf)
Suppose $f(x)$ takes values outside $F$ on a set $A_{\alpha, r}$ with $\mu(A_{\alpha, r}) > 0$ s.t. $A_{\alpha, r} = \lbrace x : f(x) \in N(\alpha, r) \rbrace$.

Then
\[
\left| \frac{1}{\mu(A_{\alpha, r})} \int_{A_{\alpha, r}} f \, d\mu - \alpha \right|
= \frac{1}{\mu(A_{\alpha, r})} \left| \int_{A_{\alpha, r}} (f - \alpha) \, d\mu  \right|
\le \frac{1}{\mu(A_{\alpha, r})} \int_{A_{\alpha, r}} \lvert f - \alpha \rvert \, d\mu 
\le r,
\]

This contradicts the assumption, so $\mu(A_{\alpha, r}) = 0$. 

---

## Definition
For a measure space $(X, 2^X, c)$ and $1 \le p < \infty$,
\[
L^p(X, 2^X, c) = \ell^p(X)
\]

When $X = \mathbb{N}$ with counting measure and $1 \le p < q < \infty$,
\[
\ell^p(\mathbb{N}) \subseteq \ell^p(\mathbb{N}),
\]
\[
\ell^p(\lbrack 0,1 \rbrack) \subseteq \ell^p(\lbrack 0,1 \rbrack) 
\]
by **Hölder’s inequality**

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

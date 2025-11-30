---
layout: post
title: "Real Analysis Lecture 11: Dual Space"
date: 2025-11-16
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.


# (11a) Bounded Linear Maps <!-- % 유계 선형 사상 -->

## Definition
Let $X, Y$ be normed vector spaces and let $T: X \to Y$ be linear. The following are equivalent:

1. $T$ is continuous at $0$.  
2. $\sup\limits_{\lVert x\rVert \le 1} \lVert T(x)\rVert < \infty$.  
3. $T$ is uniformly continuous on $X$.

We denote by $\mathcal{B}(X, Y)$ the normed space of all bounded linear maps.

If $Y$ is complete, then the operator space $\mathcal{B}(X, Y)$ is also complete.

The **dual space** of $X$ is
\[
X^\*, 
\]
the set of all bounded linear functionals on $X$.  

If $\mathbb{F} = \mathbb{R}$ or $\mathbb{C}$ denotes the scalar field, then
\[
X^\* = \mathcal{B}(X, \mathbb{F}).
\]

---
---

# (11b) Dual Space Examples <!-- % 쌍대공간 예시 -->

## 1. $\ell^p(\lbrack 1,2\rbrack)$ for $1 \le p \le \infty$
For the vector $(x, y)$:

- If $1 \le p < \infty$:
\[
\lVert (x, y)\rVert\_p = \lbrace \lvert x\rvert^p + \lvert y\rvert^p \rbrace^{1/p}.
\]

- If $p = \infty$:
\[
\lVert (x, y)\rVert\_\infty = \max\lbrace \lvert x\rvert , \lvert y\rvert \rbrace.
\]

---

## 2. $\varphi\_{a,b}(x,y) = ax + by$

\[
\sup\limits_{\lVert (x,y)\rVert\_p \le 1} \lbrace \lvert ax + by\rvert \rbrace = 
\lVert \varphi\_{a,b}\rVert = \lVert (a,b)\rVert\_q,  1 < p \le \infty, \; \tfrac{1}{p} + \tfrac{1}{q} = 1
\]

---
## 3. $L^p(\mu)$ dual space
For $1 \le p < \infty$, the dual is
\[
(L^p)^\* = L^q, \qquad \tfrac{1}{p} + \tfrac{1}{q} = 1.
\]

Given $g \in L^q$, define the functional
\[
\varphi_g \;:\; f \mapsto \int f g \, d\mu.
\]

Then:
\[
\lvert \varphi_g(f) \rvert =
\lvert \int f g\, d\mu \rvert \le \lVert f\rVert\_p \lVert g\rVert\_q.
\]

Thus every functional is bounded $\lVert \varphi_g \rVert \le \lVert g\rVert\_q$.

### To show $\lVert \varphi_g \rVert = \lVert g\rVert\_q$
We choose $f$ to approximate the sign of $g$:

1. If $g \ne 0$ and $1 < p < \infty$:
\[
f = \operatorname{sgn}(g)\, \lvert g\rvert^{q-1},  
\quad \text{scaled so that } \int \lvert f\rvert^p = 1.
\]

2. If $q=1$ and $p=\infty$:
\[
f = \operatorname{sgn}(g) = \frac{\lvert g(x) \rvert}{g(x)} I(g(x) \ne 0)
\]

3.  If $p=1$ and $q=\infty$:
\[
\int f g \ge \lVert f \rVert_1 \cdot (\lVert g \rVert_\infty - \epsilon)
\]

---
---


# (11c) Hahn–Banach Theorem <!-- % 한–바나흐 정리 -->

## Theorem 11-1. (Hahn–Banach)
Let $X$ be a normed space, $Y$ a subspace of $X$, and let $\varphi: Y \to \mathbb{C}$ be a bounded linear functional.  

Then there exists an bounded linear functional
\[
\tilde{\varphi}: X \to \mathbb{C}
\]
such that

1. $\tilde{\varphi}\lvert\_Y = \varphi$,  
2. $\lVert \tilde{\varphi} \rVert = \lVert \varphi\rVert$.

### pf)
For any $x\_0 \notin Y$ with $\lVert \varphi \rVert = 1$, let $X = \lbrace ax_0 + y : a \in \mathbb{R}, y \in Y \rbrace$, $\psi_1: X \to \mathbb{C}$.

Since $\psi\_1 ( \alpha x\_0 + y) = \alpha \psi_1(x_0) + \varphi(y)$ and $\lVert \psi_1 \rVert = 1$,

\[
\lvert \psi\_1 (x\_0) - \varphi(y)\rvert
\le \lVert y - x\_0\rVert.
\]

Thus
\[
\lvert \psi\_\alpha (x\_0) \rvert 
\le \lvert \varphi(y)\rvert + \lVert y - x\_0\rVert.
\]

Taking the infimum over all $y \in Y$ gives
\[
\lvert \psi\_\alpha (x\_0) \rvert 
\le \inf\_{y\in Y} \lbrace \lvert \varphi(y)\rvert + \lVert y - x\_0\rVert\rbrace.
\]


---
---

# (11d) Open Mapping Theorem <!-- % 열린사상 정리 -->

## Theorem 11-2. (Baire Category Theorem)
Let $X$ be a complete metric space and $\lbrace C\_n\rbrace\_{n=1}^{\infty}$ a sequence of closed sets such that  
\[
X = \bigcup\_{n=1}^{\infty} C\_n.
\]
Then at least one $C\_n$ has nonempty interior.

### pf)
Assume to the contrary that every $C\_n$ has empty interior.

Take a ball $N(x\_1, r\_1)$ with $\overline{N(x\_1, r\_1)} \cap C\_1 = \varnothing$.  
Since $C\_1$ has empty interior, we choose
\[
\overline{N(x\_2, r\_2)} \subset N(x\_1, r\_1) \setminus (C\_1 \cup C\_2).
\]

Inductively:
\[
\overline{N(x\_{n}, r\_{n})} \subset N(x\_n-1, r\_n-1) \setminus (C\_1 \cup \cdots \cup C\_n)
\]

Since $X$ is complete, $x\_n \to x$.  
Then $x \in \overline{N(x\_n, r\_n)}$ for all $n$, so
\[
x \notin \bigcup\_{n=1}^{\infty} C\_n,
\]
contradicting $X = \bigcup C\_n$. 

---

## Theorem 11-3. (Open Mapping Theorem)
Let $X, Y$ be Banach spaces and let  $T: X \to Y$ be a bounded onto linear map.
\[
\Rightarrow \exists\; \delta > 0 \text{ s.t. } T(X_1) \supset Y_\delta. \;\;
(X_r = \lbrace x \in X: \lVert x \rVert < r \rbrace)
\]

### pf)

### 1. To Show $Y_\delta \subset \overline{T(X\_1)}$: 

Let $X = \bigcup_{n=1}^\infty X_n$ and $Y = \bigcup_{n=1}^\infty \overline{T(X_n)}$.

By **Baire’s theorem**, one $Y\_n$ must have nonempty interior.  

Thus $\exists r>0$ and $y\_0 \in Y$ such that
\[
N(y\_0,r) \subset Y\_n = \overline{T(X_n)}.
\]

Hence for all $y$ with $\lVert y\rVert < r$,
\[
y \in \overline{T(X\_n)} - y\_0.
\]
\[
\Rightarrow Y_r \subset \overline{T( X_{n + \lVert x_o \rVert} )} \text{ for } f(x_0)=y_0.
\]

Choose $\delta = \frac{r}{n + \lVert x\_0\rVert}$, then
\[
Y_\delta \subset \overline{T(X\_1)}.
\]

### 2. To Show $Y_\delta \subset T(X\_1)$:

For all $s > 0$, $Y_s \subset \overline{T(X_{\frac{s}{\delta}})}$.

For $\varepsilon\in (0,1)$ and $y \in Y_1$,
\[
\exists \; x_1 \in X_{\frac{1}{\delta}} \text{ s.t. } \lVert y - T(x\_1)\rVert < \varepsilon.
\]

Since $y - T(x\_1) \in Y_\varepsilon$, 
\[
\exists \; x_2 \in X_{\frac{\varepsilon}{\delta}} \text{ s.t. } \lVert y - T(x\_1) - T(x\_2)\rVert < \varepsilon^2.
\]

Inductively,
\[
\exists \; x_n \in X_{\frac{\varepsilon^{n-1}}{\delta}} \text{ s.t. } \lVert y - T(x\_1) - T(x\_2) - \ldots - T(x_n) \rVert < \varepsilon^n.
\]

Because $X$ is Banach, $x = \sum\_{k=1}^{\infty} x\_k$ converges in $X$, and
\[
y = \sum\_{k=1}^{\infty} T(x\_k) = T(x) \in T(X_{\frac{1}{\delta(1-\varepsilon)}}).
\]

Thus:
\[
Y_1 \subset T(X_{\frac{1}{\delta(1-\varepsilon)}}), 
\;\Rightarrow\;
Y_\delta \subset T(X_1).
\]



---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

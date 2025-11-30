---
layout: post
title: "Real Analysis Lecture 12: Banach Spaces and Hilbert Spaces"
date: 2025-11-23
categories: [Real_analysis]
use_math: true
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.

# (12a) Uniform Boundedness Principle <!-- % 고른 유계 원칙 -->

## Theorem 12-1. (Closed Graph Theorem)
Let $X, Y$ be Banach spaces and let $T: X \to Y$ be linear. 

Suppose that whenever $x\_n \in X$ satisfies
\[
x\_n \to x,  
\qquad T(x\_n) \to y,
\]
then $T(x) = y$ (graph is closed).  

Then **$T$ is bounded**.

### pf)
Define a new norm on $X$ by
\[
\lVert x\rVert' = \lVert x\rVert + \lVert T(x)\rVert.
\]

Then $(X, \lVert\cdot\rVert')$ is a normed space, and
\[
\lVert x\rVert \le \lVert x\rVert' \le M \lVert x\rVert
\]
for some $M>0$, because the graph is closed and $X$ is complete.

Thus the norms $\lVert\cdot\rVert$ and $\lVert\cdot\rVert'$ are equivalent.  

Since the map $x \mapsto T(x)$ is continuous under $\lVert\cdot\rVert'$, it is also continuous under $\lVert\cdot\rVert$. Therefore $T$ is bounded.

---

## Theorem 12-2. (Uniform Boundedness Principle, Banach–Steinhaus)

Let $X$ be a Banach space and $Y$ a normed space.  
Let $\lbrace T\_\alpha : \alpha \in A \rbrace$ be a family of bounded linear maps from $X$ to $Y$.

Assume that for each $x \in X$,
\[
M(x) := \sup\_{\alpha \in A} \lVert T\_\alpha(x)\rVert < \infty.
\]

Then
\[
\sup\_{\alpha \in A} \lVert T\_\alpha\rVert < \infty.
\]

### pf)
For $n = 1,2,\ldots$ and define the closed sets
\[
C\_n = \bigcap\_{\alpha \in A} 
\lbrace x \in X : \lVert T\_\alpha(x)\rVert \le n \rbrace.
\]
Each $C\_n$ is closed (as an intersection of inverse of closed sets), and by assumption $X = \bigcup\_{n=1}^{\infty} C\_n.$

By the **Baire category theorem**, some $C\_N$ contains a ball  
\[
N(x\_0, r) \subset C\_N.
\]

Thus, if $\lVert x - x\_0\rVert < r$, then for all $\alpha \in A$,
\[
\lVert T\_\alpha(x)\rVert \le N.
\]

Let $x \in X$ with $\lVert x\rVert < r$. Then
\[
\lVert T\_\alpha(x)\rVert 
\le \lVert T\_\alpha(x) - T\_\alpha(x\_0)\rVert + \lVert T\_\alpha(x\_0)\rVert
\le \lVert T\_\alpha\rVert \lVert x - x\_0\rVert + N \le N + M(x\_0).
\]

Hence
\[
\sup\_{\alpha \in A} \lVert T\_\alpha\rVert < \infty.
\]

---
---

# (12b) Dual Space of a Hilbert Space <!-- % 힐베르트 공간의 쌍대공간 -->

## Definition 12-1.
Let $H$ be a Hilbert space and $C \subset H$ a nonempty subset.

1. $C$ is **convex** if for all $x,y \in C$ and $t \in \lbrack 0,1\rbrack$,
   \[
   tx + (1-t)y \in C.
   \]

2. For $x\_0 \in H$ we define the distance from $x\_0$ to $C$ by
   \[
   d\left(x\_0,C\right)
   = \inf\limits\_{y\in C} \lVert x\_0 - y\rVert.
   \]

A point $y\_0 \in C$ with $\lVert x\_0 - y\_0\rVert = d\left(x\_0,C\right)$ is called a **best approximation** (or the metric projection of $x\_0$ onto $C$).


---

## Theorem 12-3. (Projection onto a Closed Convex Set)
Let $H$ be a Hilbert space and let $C \subset H$ be nonempty, closed, and convex.  
For $x\_0 \in H \setminus C$ set
\[
d = d\left(x\_0,C\right) = \inf\limits\_{y\in C} \lVert x\_0 - y\rVert.
\]
Then there exists unique $y\_0 \in C$ such that
\[
\lVert x\_0 - y\_0\rVert = d.
\]

### pf)
By translating $C$ we may assume $x\_0 = 0$; it suffices to find $y\_0 \in C$ with
\[
\lVert y\_0\rVert = \inf\limits\_{y\in C} \lVert y\rVert =: d.
\]

Choose a sequence $\lbrace y\_n\rbrace \subset C$ such that $\lVert y\_n\rVert \to d$.  
We show that $\lbrace y\_n\rbrace$ is Cauchy.  

In a Hilbert space we have, for all $x,y \in H$,
\[
\frac{1}{4}\,\lVert x-y\rVert^2
\le \frac{1}{2}\,\lVert x\rVert^2 + \frac{1}{2}\,\lVert y\rVert^2 - \left\lVert \frac{x+y}{2} \right\rVert^2.
\]

Since $C$ is convex, the midpoint $\frac{y\_n + y\_m}{2}$ belongs to $C$, and hence
\[
\left\lVert \frac{y\_n + y\_m}{2} \right\rVert^2
\ge d^2.
\]
Therefore
\[
\frac{1}{4}\,\lVert y\_n - y\_m\rVert^2
\le \frac{1}{2}\,\lVert y\_n\rVert^2 + \frac{1}{2}\,\lVert y\_m\rVert^2 - d^2.
\]

Letting $n,m \to \infty$ and using $\lVert y\_n\rVert, \lVert y\_m\rVert \to d$, we get
\[
\limsup\_{n,m\to\infty} \lVert y\_n - y\_m\rVert^2 \le 0,
\]
so $\lbrace y\_n\rbrace$ is Cauchy.  
Since $H$ is complete and $C$ is closed, there exists $y\_0 \in C$ with $y\_n \to y\_0$.  
By continuity of the norm,
\[
\lVert y\_0\rVert = \lim\_{n\to\infty} \lVert y\_n\rVert = d.
\]
Thus $y\_0$ is a best approximation of $0$ (and hence of $x\_0$ before translation).

---

## Theorem 12-4. (Orthogonal Decomposition w.r.t. a Closed Subspace)
Let $E$ be a closed subspace of a Hilbert space $H$ and let $x\_0 \in H \setminus E$.  
Then there exists a unique $y\_0 \in E$ such that
\[
\lVert x\_0 - y\_0\rVert \le \lVert x\_0 - y\rVert \quad \text{for all } y \in E.
\]
Moreover,
\[
x\_0 - y\_0 \perp E.
\]

### pf)
Apply **Theorem 12-3** to the closed convex set $C = E$ to obtain $y\_0 \in E$ with
\[
\lVert x\_0 - y\_0\rVert \le \lVert x\_0 - y\rVert \quad \text{for all } y \in E.
\]

Put $z\_0 = x\_0 - y\_0$. We prove $z\_0 \perp E$.  
Fix $y \in E$ and consider, for $\alpha \in \mathbb{R}$,
\[
\lVert x\_0 - (y\_0 + \alpha y)\rVert^2
= \lVert z\_0 - \alpha y\rVert^2 + \alpha^2 \lVert y\rVert^2.
\]

By minimality of $y\_0$, the function
\[
f(\alpha) = \lVert z\_0 - \alpha y\rVert^2
\]
has a minimum at $\alpha = 0$. Hence $f'(0) = 0$, which gives
\[
-2 \operatorname{Re}\langle z\_0, y\rangle = 0.
\]

Since this holds for all $y \in E$, we obtain $\langle z\_0, y\rangle = 0$ for all $y \in E$, i.e.,
\[
z\_0 \perp E.
\]

Uniqueness: if $x\_0 = y\_0 + z\_0 = y\_1 + z\_1$ with $y\_0,y\_1 \in E$ and $z\_0,z\_1 \perp E$, then
\[
(y\_0 - y\_1) = (z\_1 - z\_0) \in E \cap E^\perp = \lbrace 0\rbrace,
\]
so $y\_0 = y\_1$ and $z\_0 = z\_1$.

---

## Theorem 12-5. (Riesz Representation Theorem)
Define, for $y \in H$, the functional
\[
\varphi\_y : H \to H^\ast, 
\quad \varphi\_y(x) = \langle x, y\rangle.
\]
Then $\varphi\_y$ is a bounded linear functional and
\[
\lVert \varphi\_y\rVert = \lVert y\rVert.
\]

Conversely, for every bounded linear functional $\varphi \in H^\*$ there exists a unique $y \in H$ such that
\[
\varphi(x) = \langle x, y\rangle \quad \text{for all } x \in H.
\]
Hence the map
\[
H \ni y \longmapsto \varphi\_y \in H^\*
\]
is an isometric isomorphism.

### pf)
For $y \in H$ we clearly have linearity and, by Cauchy–Schwarz,
\[
\lvert \varphi\_y(x)\rvert
= \lvert \langle x,y\rangle\rvert
\le \lVert x\rVert\, \lVert y\rVert,
\]
so $\varphi\_y$ is bounded and $\lVert \varphi\_y\rVert \le \lVert y\rVert$.  
Taking $x = y/\lVert y\rVert$ (for $y \ne 0$) gives equality, so $\lVert \varphi\_y\rVert = \lVert y\rVert$.

Now let $\varphi \in H^\*$ be nonzero. Its kernel
\[
E = \ker \varphi = \lbrace x \in H : \varphi(x) = 0\rbrace
\]
is a closed subspace of $H$. Choose $z \in E^\perp$ with $\lVert z\rVert = 1$ (possible since $\varphi \ne 0$ implies $E \ne H$).  

For arbitrary $x \in H$ write the orthogonal decomposition
\[
x = x\_E + \lambda z,
\quad x\_E \in E, \ \lambda \in \mathbb{F}.
\]
Then
\[
\varphi(x) = \varphi(x\_E) + \lambda \varphi(z)
= \lambda \varphi(z).
\]

Note that
\[
\lambda = \langle x, z\rangle,
\]
because $x - \langle x,z\rangle z \perp z$ and lies in $E$.  
Hence
\[
\varphi(x) = \varphi(z)\, \langle x, z\rangle
= \langle x, \overline{\varphi(z)}\, z\rangle
\]
(in the real case simply $\varphi(z) z$).  

Thus if we define
\[
y = \overline{\varphi(z)}\, z,
\]
we obtain
\[
\varphi(x) = \langle x, y\rangle \quad \text{for all } x \in H.
\]

Uniqueness: if $\langle x, y\_1\rangle = \langle x, y\_2\rangle$ for all $x$, then
\[
\langle x, y\_1 - y\_2\rangle = 0 \quad \forall x.
\]
Taking $x = y\_1 - y\_2$ gives $\lVert y\_1 - y\_2\rVert^2 = 0$, so $y\_1 = y\_2$.

Therefore every bounded linear functional arises uniquely from an inner product with some $y \in H$, and the correspondence $y \mapsto \varphi\_y$ is an isometric isomorphism $H \cong H^\*$.

---
---

# (12c) Orthonormal Bases in a Hilbert Space <!-- % 정규직교기저 -->

## Definition 12-2.
Let $H$ be a Hilbert space.  
A family $\mathcal{A} = \lbrace u\_\alpha : \alpha \in A\rbrace$ is called **orthonormal** in $H$ if

1. $\langle u\_\alpha, u\_\beta\rangle = 0$ for $\alpha \ne \beta$,  
2. $\lVert u\_\alpha\rVert = 1$ for all $\alpha$.

We say that $\mathcal{A}$ is an **orthonormal basis** (or complete orthonormal system) if the following equivalent conditions hold:

### (i) Parseval identity
For all $x \in H$,
\[
\sum\_{\alpha \in A} \lvert \langle x, u\_\alpha\rangle\rvert^2 = \lVert x\rVert^2.
\]

### (ii) Reproducing formula
For all $x,y \in H$,
\[
\sum\_{\alpha \in A} \langle x, u\_\alpha\rangle \langle u\_\alpha, y\rangle
= \langle x, y\rangle.
\]

### (iii) Maximality
$\mathcal{A}$ is maximal among orthonormal families;  
no further nonzero vector can be added without losing orthonormality.

### (iv) Density
Let
\[
P\_{\mathcal{A}} = \text{span}\_{\text{fin}} \lbrace u\_\alpha : \alpha\in A\rbrace
\]
be the set of all finite linear combinations of $u\_\alpha$.  
Then $P\_{\mathcal{A}}$ is dense in $H$.

---

## Bessel Inequality
Let $F \subset A$ be a finite subset. For any $x \in H$,
\[
\left\lVert x - \sum\_{\alpha \in F} \langle x, u\_\alpha\rangle u\_\alpha \right\rVert^2
\le \lVert x - y\rVert^2
\quad\text{for all } y \in P\_F.
\]

In particular:
\[
\sum\_{\alpha \in F} \lvert \langle x, u\_\alpha\rangle\rvert^2
\le \lVert x\rVert^2.
\]

Equality holds when
\[
y = \sum\_{\alpha \in F} \langle x, u\_\alpha\rangle u\_\alpha.
\]

---

## Coefficient Map
Given an orthonormal basis $\mathcal{A}$, define the coefficient map
\[
x \longmapsto \widehat{x}(\alpha) := \langle x, u\_\alpha\rangle.
\]

This map is an isometry of $H$ into $\ell^2(A)$ via Parseval identity.

---
---

# (12d) Plancherel Transform <!-- % 플랑셰렐 변환 -->

## Definition 12-3. (Fourier Transform on $\mathbb{R}$)
For $f \in L^1(\mathbb{R})$ define its Fourier transform by
\[
\widehat{f}(\xi)
= \frac{1}{2\pi}\int\_{\mathbb{R}} f(x)\, e^{-i \xi x}\, dx.
\]

Parseval/Plancherel theory extends this to $L^2(\mathbb{R})$.

---

## Fourier Series Representation
Let $f \in L^1(\mathbb{R})$ be $2\pi$–periodic.  
Define the Fourier series
\[
F(t) = \sum\_{n=-\infty}^{\infty} f(t-2n\pi) = \sum\_{n=-\infty}^{\infty} \widehat{f}(n)\, e^{i n t},
\qquad F \in L^1(\lbrack -\pi,\pi\rbrack).
\]

The coefficients satisfy
\[
\widehat{f}(n)
= \frac{1}{2\pi}\int\_{-\pi}^{\pi} f(t)\, e^{-i n t}\, dt.
\]

---

## Plancherel Formula (Compact Support Case)
If $f \in C\_c(\mathbb{R})$, then $f \in L^1(\mathbb{R}) \cap L^2(\mathbb{R})$ and
\[
\int\_{\mathbb{R}} \lvert f(x)\rvert^2\, dx
= \frac{1}{2\pi} \int\_{\mathbb{R}} \lvert \widehat{f}(\xi)\rvert^2\, d\xi.
\]

### Sketch of Argument
If $\operatorname{supp} f \subset \lbrack -\pi,\pi\rbrack$, then by Fourier series computation,
\[
\frac{1}{2\pi}\int\_{-\pi}^{\pi} \lvert f(t)\rvert^2\, dt
= \sum\_{n=-\infty}^{\infty} \left\lvert \frac{1}{2\pi} \widehat{f}(n) \right\rvert^2.
\]

Let $g(x) = f(x)\, e^{-i x \xi}$.  
Applying orthogonality,
\[
\int\_{-\pi}^{\pi} \lvert f(x)\rvert^2\, dx
= \frac{1}{2\pi} \sum\_{n=-\infty}^{\infty}
  \left\lvert \int\_{\mathbb{R}} f(x)\, e^{-i (n+\xi)x}\, dx \right\rvert^2.
\]

Taking the limit as the period grows and using Riemann sum approximation gives
\[
\int\_{\mathbb{R}} \lvert f(x)\rvert^2 \, dx
= \frac{1}{2\pi}\int\_{-\infty}^{\infty} \lvert \widehat{f}(\xi)\rvert^2\, d\xi.
\]

Thus the Fourier transform extends to an isometry on $L^2(\mathbb{R})$.


---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

---
layout: post
title: "Real Analysis Lecture 5: Space of Integrable Functions"
date: 2025-10-05
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.



# (05a) Lebesgue Spaces <!-- % 르벡 공간 -->

## Definition

\[
L^1(E) = \lbrace f : \int_E \lvert f \rvert < \infty \rbrace, \quad
L^2(E) = \lbrace f : \int_E \lvert f \rvert^2 < \infty \rbrace.
\]

---

## Jensen’s Inequality <!-- % 젠센 부등식 -->

Let $\phi : (a,b) \to \mathbb{R}$ be **convex**, and let $f : [0,1] \to (a,b)$ be integrable.  
Then
\[
\phi \left(\int_0^1 f(t)\,dt\right) \le \int_0^1 \phi(f(t))\,dt.
\]

### pf)
Let $\alpha = \int_0^1 f(x)\,dx$, and $\beta = \sup \lbrace \frac{\phi(\alpha) - \phi(s)}{\alpha - s} \rbrace$ for $a < s < \alpha < b$.  
\[
\Rightarrow \phi(s) - \phi(\alpha) \ge \beta(s - \alpha), \; \forall s \in (a,b)
\]
\[
\Rightarrow \phi(f(x)) - \phi(\alpha) \ge \beta(f(x) - \alpha).
\]

Hence
\[
\int_0^1 \phi(f(t))\,dt - \phi \left(\int_0^1 f(t)\,dt\right) \ge 0.
\]


## Example (Exponential Case)

Let $a_i>0$ with $\sum_{i=1}^n a_i = 1$, and let $s_1 \le s_2 \le \cdots \le s_n$,

$t_0 := 0,\; t_k := \sum_{i=1}^k a_i \ \ (k=1,\dots,n)$, so that $0=t_0 < t_1 < \cdots < t_n = 1$ .

Define the step function $f:\lbrack 0,1 \rbrack \to \mathbb{R}$ s.t.
\[
f(x)= \sum_{i=1}^n s_i \,\chi_{\lbrack t_{i-1},\, t_i )}(x).
\]

Define $\phi(x) = e^x$.  

Then

1. $e^{a_1 s_1 + a_2 s_2 + \dots + a_n s_n} \le a_1 e^{s_1} + a_2 e^{s_2} + \dots + a_n e^{s_n}$

2. $t_1^{a_1} \dots t_b^{a_n} \le a_1 t_1 + \dots + a_n t_n \; (t_i > 0)$

3. $s^{\frac{1}{p}} \cdot t^{\frac{1}{q}} \le \frac{1}{p} \cdot s + \frac{1}{q} \cdot t (\frac{1}{p} + \frac{1}{q} = 1, \; 0<p,q< \infty)$

4. $S \cdot T \le \frac{1}{p} \cdot S^p + \frac{1}{q} \cdot T^q \; (S, T \ge 0)$


---

## Hölder’s Inequality <!-- % 홀더 부등식 -->

For $f,g : E \to [0,\infty]$ and $1 < p, q < \infty$ with $\frac{1}{p} + \frac{1}{q} = 1$,  
\[
\int_E f g \le \left(\int_E f^p\right)^{1/p} \left(\int_E g^q\right)^{1/q}.
\]

### pf)
Let
\[
A = \left(\int_E f^p\right)^{1/p}, \quad
B = \left(\int_E g^q\right)^{1/q}.
\]
Define
\[
F = \frac{f}{A}, \quad G = \frac{g}{B}.
\]
Then $\int_E F^p = \int_E G^q = 1$.  

By Jensen’s inequality,
\[
F(x) G(x) \le \frac{F(x)^p}{p} + \frac{G(x)^q}{q},
\]
and integrating both sides gives
\[
\int_E F G \le \frac{1}{p} + \frac{1}{q} = 1.
\]
Multiplying both sides by $AB$ yields Hölder’s inequality.

---

## Minkowski’s Inequality <!-- % 민코프스키 부등식 -->

For $p > 1$,
\[
\left(\int_E (f+g)^p \right)^{1/p} \le 
\left(\int_E f^p \right)^{1/p} + \left(\int_E g^p \right)^{1/p}.
\]

### pf)
First,
\[
\int_E (f+g)^p
= \int_E (f+g)\,(f+g)^{p-1}
= \int_E f\,(f+g)^{p-1} + \int_E g\,(f+g)^{p-1}.
\]

Apply **Hölder’s inequality** to each term with exponents $(p,q)$:
\[
\int_E f\,(f+g)^{p-1}
\le \lVert f\rVert_p \,\lVert (f+g)^{p-1}\rVert_q,
\qquad
\int_E g\,(f+g)^{p-1}
\le \lVert g\rVert_p \,\lVert (f+g)^{p-1}\rVert_q.
\]

Since $q=\dfrac{p}{p-1}$, we have
\[
\lVert (f+g)^{p-1}\rVert_q
= \Big(\int_E (f+g)^{(p-1)q}\Big)^{1/q}
= \Big(\int_E (f+g)^p\Big)^{1/q}
= \lVert f+g\rVert_p^{\,p-1}.
\]

Combining the estimates,
\[
\int_E (f+g)^p
\le \big(\lVert f\rVert_p+\lVert g\rVert_p\big)\, \lVert f+g\rVert_p^{\,p-1}.
\]

Divide both sides by $\lVert f+g\rVert_p^{\,p-1}$ to obtain
\[
\lVert f+g\rVert_p \le \lVert f\rVert_p + \lVert g\rVert_p,
\]
which is Minkowski’s inequality. $\square$

---

## Definition (Lp Space)

For a measurable set $E \subset \mathbb{R}$, define
\[
L^p(E) = \lbrace f : E \to \mathbb{C} \text{ measurable and } \int_E \lvert f \rvert^p < \infty \rbrace.
\]

### Properties
1. $L^p(E)$ is a **vector space** for $1 \le p < \infty$.  

2. The **norm**
   \[
   \lVert f \rVert_p = \left( \int_E \lvert f \rvert^p \right)^{1/p}
   \]
   satisfies:

    1. $\lVert f \rVert_p = 0 \Rightarrow f = 0 \text{ a.e.}$

    2. $\lVert a f \rVert_p = \lvert a \rvert \lVert f \rVert_p$

    3. $\lVert f + g \rVert_p \le \lVert f \rVert_p + \lVert g \rVert_p$


Thus $L^p(E)$ is a **normed space**.

---
---

# (05b) Completeness of Lebesgue Spaces <!-- % 르벡공간의 완비성 -->

For $f : E \to [0,\infty]$, define 
\[
\operatorname*{ess\,sup} f = \inf \lbrace \alpha \in \mathbb{R} : \mu( f^{-1} (\alpha, \infty) ) = 0 \rbrace.
\]

Then
\[
\lVert f \rVert_\infty = \operatorname*{ess\,sup} \lvert f \rvert.
\]

Also,
\[
f \in L^\infty(E) \;\Leftrightarrow\; \lVert f \rVert_\infty < \infty.
\]

---

## Theorem
$L^p(E)$ is a **complete normed space** for $1 \le p \le \infty$.  


* $X$ is **complete**
\[
\Leftrightarrow \; \sum_{n=1}^{\infty} \lVert x_n \rVert < \infty \longrightarrow
\exists \; x \in X \text{ s.t. } \lim_{N \rightarrow \infty} \lVert x - \sum_{n=1}^{N} x_n \rVert
\]
  

### Case 1: $p = \infty$

Let $\lbrace f_n \rbrace$ be a Cauchy sequence in $L^\infty(E)$.  

Define  
\[
A_{k} = \lbrace x \in E : \lvert f_k(x) \rvert > \lVert f_k \rVert_\infty \rbrace.
\]
\[
B_{m,n} = \lbrace x \in E : \lvert f_m(x) - f_n(x) \rvert > \lVert f_m - f_n \rVert_\infty \rbrace.
\]

Let $F$ be union of $A_k$ and $B_{m,n}$. Then $\mu(F) = 0$.  

For $x \in E \setminus F$, the sequence $\lbrace f_n(x) \rbrace$ is Cauchy in $\mathbb{R}$, hence convergent to some $f(x)$.

(i.e. $\lvert f_m(x) - f_n(x) \rvert < \lVert f_m - f_n \rVert \rightarrow 0$ as $m,n \rightarrow 0$)

Define $f(x) = \lim_{n \to \infty} f_n(x)$ on $E \setminus F$.  

Then
\[
\lVert f_n - f \rVert_\infty \to 0,
\]
and thus $L^\infty(E)$ is complete.


### Case 2: $1 \le p < \infty$

Let $\lbrace f_n \rbrace$ be a Cauchy sequence in $L^p(E)$.  

Take a subsequence $\lbrace f_{n_i} \rbrace$ such that  
\[
\lVert f_{n_{i+1}} - f_{n_i} \rVert_p \le 2^{-i}.
\]

Define
\[
g_k = \sum_{i=1}^k \lvert f_{n_{i+1}} - f_{n_i} \rvert, \quad
g = \sum_{i=1}^\infty \lvert f_{n_{i+1}} - f_{n_i} \rvert.
\]

Then by **Fatou’s lemma** and since $\lVert g_k \rVert_p < 1, \; \forall k = 1,2,\ldots$,
\[
\int_E g^p \le \sum_{k=1}^\infty \int_E g_k^p \le 1,
\]

so $g \in L^p(E)$.

Define
\[
f = f_{n_1} + (f_{n_2} - f_{n_1}) + (f_{n_3} - f_{n_2}) + \dots,
\]

then $f = \sum (f_{n_{k+1}} - f_{n_k})$ converges absolutely a.e. 

Thus $L^p(E)$ is complete. ✅

---
---

# (05c) Luzin’s Theorem <!-- % 루진 정리 -->

## Lemma 5-1
Let $U$ be open and $K \subset U$ be compact set.  

Then there exists a continuous function $f$ s.t.
\[
f(x) = 1, x \in K \; / \; f(x) = 0, x \in U^c
\]

### pf)

Assume $K\subset\mathbb{R}$ and use compactness: choose finitely many closed intervals
\[
K \subset \bigcup_{j=1}^{N} I_j \subset U
\]
with disjoint interiors such that $\operatorname{dist}(I_j, U^{c})>0$ for all $j$. 

For each $j$, pick continuous $\varphi_j:\mathbb{R}\to[0,1]$ with
\[
\varphi_j\equiv 1 \text{ on } I_j, \qquad \operatorname{supp}\varphi_j \subset J_j\subset U,
\]
where $J_j$ are slightly larger open intervals still inside $U$.  

(Construct $\varphi_j$ piecewise linearly on $J_j$ so that it tapers to $0$ at $\partial J_j$.)

Let
\[
s(x):=\sum_{j=1}^{N}\varphi_j(x),\qquad
f(x):=\min\lbrace1,\, s(x) \rbrace.
\]
Then $f$ is continuous, $f\equiv 1$ on $K$ (since each $x\in K$ lies in some $I_j$), and $f\equiv 0$ on $U^{c}$ because $\operatorname{supp} f \subset \bigcup_j J_j \subset U$. $\square$

---

## Theorem 5-1 (Luzin)
Let $f : [a,b] \to \mathbb{C}$ be measurable. Then

1. $\forall \varepsilon > 0, \; \exists \; g: [a,b] \to \mathbb{C}$ continuous function s.t. $\mu(\lbrace x : f(x) \ne g(x) \rbrace) < \varepsilon.$

2. If $f \in L^{\infty} [a,b]$, then $\exists \; g \in C[a,b]$ s.t. $\lVert g \rVert_{sup} \le \lVert f \rVert_{\infty}$ and $\mu(\lbrace x : f(x) \ne g(x) \rbrace) < \varepsilon$.

### pf)

### Case 1: $0 \le f < 1$

Construct step functions
\[
S_n(x) = \sum_{k=1}^{2^n} \frac{k-1}{2^n} \chi_{A_k}(x),
\]
where $A_k = \lbrace x : \frac{k-1}{2^n} \le f(x) < \frac{k}{2^n} \rbrace$.

Then define
\[
t_n = S_n - S_{n-1} = \frac{1}{2^n} \chi_{T_n}, \quad T_n = \lbrace x : \lvert t_n(x) \rvert > 0 \rbrace.
\]

Take open $U_n$ and compact $K_n$ with $K_n \subseteq T_n \subseteq U_n$ and $\mu(U_n \setminus K_n) < \varepsilon / 2^n$.

By the **Lemma 5-1**, built continuous $h_n$ so that
\[
h_n=\chi_{T_n}\quad\text{on}\quad \big(U_n\setminus K_n\big)^c.
\]

Define set $G:= [a,b]\setminus \bigcup_{n=1}^{\infty}(U_n\setminus K_n)$.

Then for every $x\in G$ and every $n$,
\[
h_n(x)=\chi_{T_n}(x).
\]

Hence, on $G$,
\[
g(x)=\sum_{n=1}^{\infty}2^{-n}h_n(x)
=\sum_{n=1}^{\infty}2^{-n}\chi_{T_n}(x)
=\sum_{n=1}^{\infty}\big(S_n(x)-S_{n-1}(x)\big)
=\lim_{N\to\infty} S_N(x)=f(x).
\]

Therefore $\{x:f(x)\ne g(x)\}\subseteq G^c=\bigcup_{n\ge1}(U_n\setminus K_n)$ and

\[
\mu\big(\{x:f(x)\ne g(x)\}\big)
\le \mu\left(\bigcup_{n=1}^{\infty}(U_n\setminus K_n)\right)
\le \sum_{n=1}^{\infty}\mu(U_n\setminus K_n)
< \sum_{n=1}^{\infty}\frac{\varepsilon}{2^n}=\varepsilon.
\]

### Case 2: $f$ is a bounded and complex function

Write
\[
f = (f_1 - f_2) + i (f_3 - f_4),
\]
where $f_1, f_2, f_3, f_4$ satisfy **Case 1**.  

### Case 3: $f$ is a not bounded 

Let $A_n = \lbrace x \in [a,b] : \lvert f(x) \rvert > n \rbrace$. Then $\mu(A_n) \downarrow 0$ as $n \to \infty$.

For any $\varepsilon > 0$, choose $N$ such that  
\[
\mu(A_N) < \frac{\varepsilon}{2}.
\]

Define 
\[
h(x) = (1 - \chi_{A_N}(x)) \cdot f(x)
\]

Since $h$ is bounded and measurable, by **Luzin’s theorem for bounded functions**,  
there exists a continuous function $g$ on $[a,b]$ such that
\[
\mu(\{x : h(x) \ne g(x)\}) < \frac{\varepsilon}{2}.
\]

Because $f = h$ outside $A_N$, we have
\[
\lbrace x : f(x) \ne g(x)\rbrace
\subseteq
A_N \cup \lbrace x : h(x) \ne g(x)\rbrace.
\]

Hence
\[
\mu(\{x : f(x) \ne g(x)\})
\le
\mu(A_N) + \mu(\{x : h(x) \ne g(x)\})
< \frac{\varepsilon}{2} + \frac{\varepsilon}{2}
= \varepsilon.
\]


### Case 4: $f \in L^\infty([a,b])$

Take continuous $\varphi: \mathcal{C} \to \mathcal{C}$ s.t.

1. $z \to z, \lvert z \rvert \le \lVert f \rVert_{\infty}$

2. $z \to \frac{z}{\lvert z \rvert} \cdot \lVert f \rVert_{\infty}, \lvert z \rvert > \lVert f \rVert_{\infty}$


Given $\varepsilon>0$, by the bounded (Luzin) case for complex functions, choose a continuous $g:[a,b]\to\mathbb{C}$ such that
\[
\mu\big(\{x : f(x)\ne g(x)\}\big)<\varepsilon .
\]

Set
\[
\tilde g := \varphi\circ g .
\]
Then $\tilde g$ is continuous and $\lVert \tilde g\rVert_\infty \le M=\lVert f\rVert_\infty$.

Moreover, on the set where $g=f$ we have $|f(x)|\le M$, hence
\[
\tilde g(x)=\varphi(g(x))=\varphi(f(x))=f(x).
\]

Therefore
\[
\lbrace x: f(x)\ne \tilde g(x) \rbrace \subseteq \lbrace x: f(x)\ne g(x) \rbrace,
\]
and consequently
\[
\mu\big(\lbrace x: f(x)\ne \tilde g(x)\rbrace \big)
\le
\mu\big(\lbrace x: f(x)\ne g(x)\rbrace \big)
<\varepsilon.
\]


---
---

# (05d) Lebesgue Space and Continuous Functions <!-- % 르벡공간과 연속함수 -->

## Theorem 5-2
For $1 \le p < \infty$, the set $C[a,b]$ of continuous functions is **dense** in $L^p([a,b])$:
$C[a,b] \subset L^p([a,b]).$
<!-- % 연속함수는 Lp공간에서 조밀 -->

### pf)

Let $f \in L^p([a,b])$ and $\varepsilon > 0$.

1. **Approximation by step functions:**  
   There exists a step function $S_n$ such that  
   \[
   \lVert f - S_n \rVert_p < \varepsilon.
   \]

2. **Approximation by simple functions:**  
   Since $\lVert S_n - f \rVert_p \to 0$,  
   we can take a **simple function** $S$ satisfying  
   \[
   \lVert S - f \rVert_p < \varepsilon.
   \]

3. **Approximation by continuous functions (Luzin):**  
   By Luzin’s theorem, there exists a continuous function $g \in C[a,b]$ such that  
   \[
   \lVert g \rVert_{\sup} \le \lVert S \rVert_\infty, \quad
   \mu(\lbrace x : S(x) \ne g(x) \rbrace) < \varepsilon.
   \]
   Hence $\lVert S - g \rVert_p < \varepsilon$,  
   and therefore $\lVert f - g \rVert_p < 2\varepsilon$.


---

## Theorem 5-3
$C_c(\mathbb{R})$ is dense in $L^p(\mathbb{R})$ for $1 \le p < \infty$.  
Here $C_c(\mathbb{R})$ denotes the space of continuous functions with compact support.
<!-- % 유한 지지 연속함수의 조밀성 -->

### pf)

Let $f \in L^p(\mathbb{R})$.  
Then
\[
\int_{-\infty}^\infty \lvert f \rvert^p < \infty.
\]
Hence there exists $N > 0$ such that
\[
\int_{\lvert x \rvert > N} \lvert f(x) \rvert^p < \varepsilon^p.
\]

Let $g \in C[-N, N]$ such that $ \lVert g - f \rVert_p < \varepsilon^p$.

Take $\alpha_1, \alpha_2 > 0$ and define a continuous cutoff function
$h(x) = 1,  x \in [-N+\alpha_1, N-\alpha_2]$ and 
$0, x \notin [-N, N]$

Then $h g \in C_c(\mathbb{R})$ and
\[
\lVert f - h g \rVert_p \le \lVert f - g \rVert_p + \lVert g - h g \rVert_p < 2\varepsilon.
\]

---

## Corollary
$[C_c(\mathbb{R}), \lVert \rVert_\sup]$ is dense in $C_0(\mathbb{R})$,  
where
\[
C_0(\mathbb{R}) = \lbrace f \in C(\mathbb{R}) : \lim_{\lvert x \rvert \to \infty} f(x) = 0 \rbrace.
\]

---

## Theorem 5-4
For $f \in L^p(\mathbb{R})$, define 
\[
f_y(x) = f(x - y).
\]
Then the map $y \mapsto f_y$ is **uniformly continuous** in $L^p(\mathbb{R})$:
\[
\lim_{y \to 0} \lVert f_y - f \rVert_p = 0.
\]

### pf)

Let $g \in C_c(\mathbb{R})$. Then \[ \lVert f_x - f_y \rVert_p \le \lVert f_x - g_x \rVert_p + \lVert g_x - g_y \rVert_p + \lVert f_y - g_y \rVert_p, \]

Fix $\varepsilon>0$. Choose $g\in C_c(\mathbb{R})$ with $\|f-g\|_{p}<\frac{\varepsilon}{3}$ (using the density of $C_c$ in $L^p$).  

For any $x,y\in\mathbb{R}$ the translation is an isometry in $L^p$:
\[
\lvert f_x-g_x\rvert_{p} = \lvert f-g \rvert_{p} < \frac{\varepsilon}{3}.
\]

Hence, for all $y$,
$
\lvert  f_y-f\rvert_{p} \le \lvert f_y-g_y\rvert_{p} + \lvert g_y-g\rvert_{p} + \lvert g-f\rvert_{p}
< \frac{2\varepsilon}{3}+\lvert g_y-g\rvert_{p}.
$

It remains to show $\lvert g_y-g\rvert_{p}\to 0$ as $y\to0$ for $g\in C_c(\mathbb{R})$.  

Let $\operatorname{supp} g\subset K$ with $0<\lvert K \rvert <\infty$. 

Since $g$ is uniformly continuous on $K$,  define the modulus of continuity
$
\omega(\delta):=\sup_{\lvert h\rvert \le\delta}\ \sup_{x\in\mathbb{R}}\lvert g(x-h)-g(x) \rvert \xrightarrow[\delta\downarrow 0]{} 0.
$

For $\lvert y\rvert\le \delta$ we have $\lvert g(x-y)-g(x)\rvert \le \omega(\delta)$, and the support of
$g(x-y)-g(x)$ is contained in $K\cup(K+y)$, whose measure is at most $2 \lvert K\rvert$. 

Therefore,
\[
\lvert g_y-g\rvert_{p}^{p}=\int_{\mathbb{R}} \lvert g(x-y)-g(x)\rvert^{p}dx
\le \omega(\delta)^{p}\, \lvert K\cup(K+y)\rvert \le \omega(\delta)^{p}\,2\lvert K\rvert.
\]

Taking $p$-th roots gives
$
\lvert g_y-g\rvert_{p}\le \omega(\delta)\,(2 \lvert K\rvert)^{1/p}\xrightarrow[\delta\downarrow 0]{}0.
$

Hence there exists $\delta>0$ such that $\lvert y\rvert <\delta\Rightarrow \lvert g_y-g\rvert_{p}<\varepsilon/3$.

Plugging this into (1) yields $\lvert f_y-f\rvert_{p}<\varepsilon$ for all $ \lvert y\rvert<\delta$.  
Since $\varepsilon>0$ was arbitrary, $\lvert f_y-f\rvert_{p}\to 0$ as $y\to 0$. $\square$


---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

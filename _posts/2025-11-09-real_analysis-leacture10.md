---
layout: post
title: "Real Analysis Lecture 10: Fourier Integral"
date: 2025-11-09
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.


# (10a) Fourier Series and Fourier Integral <!-- % 푸리에 급수와 푸리에 적분 -->

## Definition: Fourier Transform
For $f \in L^1(\mathbb{R})$, define
\[
\widehat{f}(\alpha)
= \int_{\mathbb{R}} f(x)\, e^{-i \alpha x}\, dx, \; \alpha \in \mathbb{R}
\]

Then:

1. $\widehat{f} \in C_0(\mathbb{R}) \;(L^1(\mathbb{R}) \to C_0(\mathbb{R}))$

2. $f \mapsto \widehat{f}$ is linear and bounded.

3. Linear Trigonometric: $\widehat{(f \ast g)}(\alpha) = \widehat{f}(\alpha) \cdot \widehat{g}(\alpha).$

4. $\lVert \widehat{f} \rVert_{\sup} \le \lVert f\rVert_1$

## Theorem 10-1.

If 
1. $h_n \ge 0$, 
2. $\int_{\mathbb{R}} h_n=1$
3. $\lim_{\lambda\to\infty} \int_{\mathbb{R} \setminus \lbrack -\delta, \delta \rbrack} h_{\lambda} = 0, \; \forall \lambda, \delta > 0$,

Then,

- $f \in L^1(\mathbb{R}) \Rightarrow \lVert f - f\ast h_{\lambda}\rVert_1 \to 0$
  
- If $f$ is bounded and uniformly continuous, $\Rightarrow \lVert f - f\ast h_{\lambda}\rVert_{\infty} \to 0.$

- $f \ast u_{\alpha} = \widehat{f}(\alpha) \cdot u_{\alpha}$



---
---

# (10b) Approximate Identity <!-- % 근사 항등원 -->

## Basic Formulas for Fourier Trnasform

- $\widehat{f'}(\alpha) = i\alpha\, \widehat{f}(\alpha)$
  
- $(\widehat{f})_{\alpha} = \widehat{g}(\alpha)$, where $g(x) = -ixf(x)$

- $\widehat{f \cdot u_\alpha} = (\widehat{f})_{\alpha}$, 
  
  where $(\widehat{f})_{\alpha}$: $\alpha$ translation of $\widehat{f}$

- $(\widehat{f_\alpha})(\alpha) = \widehat{f}(\alpha) \cdot u_\alpha (-x)$


---

## Example 10-1.
For $a>0$, 

1. $f(x)=e^{-\lvert x\rvert /a} \;\Rightarrow\; \widehat{f}(\alpha) = \int_{-\infty}^\infty e^{-\lvert x\rvert /a} \cdot e^{-i\alpha x} dx = \frac{2a}{1 + a^2\alpha^2}.$

2. $f(x)=\chi_{\lbrack -a, a \rbrack} \;\Rightarrow\; \widehat{f}(\alpha) = \int_{-a}^a  e^{-i\alpha x} dx = \frac{2\sin{ax}}{\alpha}.$

---

## Constructing Kernels (Approximate Identity)

1. Let $h\ge 0$, $\int_{\mathbb{R}} h=1$. Define
\[
h_{\lambda}(x)=\lambda h(\lambda x), \; x \in \mathbb{R}, \; \lambda>0.
\]

2. Let $p \in L^1(\mathbb{R}), \;0 \le p \le 1, \;p(0) = \lim_{\alpha \to 0} p(\alpha) = 1$. Define
\[
h(x) = \frac{1}{2\pi} \int_{\mathbb{R}} p(\alpha) \cdot u_\alpha (x) d\alpha 
\]
\[\Rightarrow h_{\lambda}(x)=\lambda h(\lambda x)\]

Example:
\[
H(x)=\frac{1}{2\pi} \int_{\mathbb{R}} e^{-\lvert\alpha\rvert} \cdot e^{i\alpha x} \, dx
= \frac{1}{\pi} \cdot \frac{1}{1 + x^2}
\]
\[
\Rightarrow H_{\lambda}(x)
= \frac{1}{2\pi} \cdot \frac{2\lambda}{1+\lambda^2 x^2}.
\]

---
---


# (10c) Inversion Formula <!-- % 역변환 공식 -->

## Theorem 10-2.
If  $\lim_{\alpha \to \pm \infty} \hat f(\alpha) = 0$, then
\[
\widehat{f} \in C_0(\mathbb{R}).
\]

### pf)
By definition,
\[
\hat f(\alpha)
= - \int_{\mathbb{R}} f(x)\, e^{-i\alpha (x + \frac{\pi}{\alpha})}\, dx
= \int_{\mathbb{R}} f(x-\tfrac{\pi}{\alpha})\, e^{-i\alpha x}\, dx.
\]

Thus,
\[
2\,\hat f(\alpha)
= \int_{\mathbb{R}} \lbrace f(x) - f_{\frac{\pi}{\alpha}}(x) \rbrace e^{-i\alpha x}\, dx.
\]
\[
2\, \lvert \hat f(\alpha)\rvert
\le \lVert f - f_{\frac{\pi}{\alpha}} \rVert_1 \to 0.
\]

---

Using the identity $(f \ast g)' = f \ast g'$, we see the relation  
\[
L^1(\mathbb{R}) \ast C^{\infty}_C(\mathbb{R}) \subset C^{\infty}_C(\mathbb{R}).
\]

Thus **$C^{\infty}_0(\mathbb{R})$ is dense in $L^1(\mathbb{R})$**.

---

## Theorem 10-3.

If $\hat f \in L^1(\mathbb{R})$, then 
\[
f(x) = \frac{1}{2\pi} \int_{\mathbb{R}} \hat f(\alpha)\, e^{i\alpha x}\, d\alpha \; \text{a.e.}
\]

### pf)
> $(h_\lambda \ast f)(x) = \int_{\mathbb{R}} f(x-y)\, h_\lambda(y)\, dy$,
>
> $= \int_{\mathbb{R}} \left\lbrack f(x-y) \cdot \frac{\lambda}{2\pi} \int p(\alpha) e^{-i\alpha \lambda y} d\alpha \right\rbrack \, dy$
>
> $= \frac{1}{2\pi} \int_{\mathbb{R}} \left\lbrack f(x-y) \int p(\frac{\alpha}{\lambda}) e^{-i\alpha y} d\alpha \right\rbrack \, dy$
>
> $= \frac{1}{2\pi} \int_{\mathbb{R}} p(\frac{\alpha}{\lambda}) \int  f(x-y)  e^{-i\alpha y} dy \,  d\alpha $
>
> $= \frac{1}{2\pi} \int_{\mathbb{R}} p(\frac{\alpha}{\lambda}) \int  f(y)  e^{i\alpha (x-y)} dy \,  d\alpha $
>
> $= \frac{1}{2\pi} \int_{\mathbb{R}} p(\frac{\alpha}{\lambda}) \hat f(\alpha)  e^{i\alpha x} \,  d\alpha $
>
> $\to \frac{1}{2\pi} \int_{\mathbb{R}}  \hat f(\alpha)  e^{i\alpha x} \,  d\alpha $ when $\hat f \in L^1(\mathbb{R})$
>

Since $\lVert h_\lambda \ast f - f \rVert_1 \to 0$,  
we obtain  
\[
h_{\lambda_n} \ast f(x) \to f(x)
\quad \text{a.e.}
\]

---

## Theorem 10-4.
$f, \; \hat f$ is one-to-one (i.e., uniquely determined).

---
---

# (10d) Examples of Fourier Transforms <!-- % 푸리에 변환 예시 -->

## Example 10-2.
Let $p(\alpha) = \max\lbrace 1 - \frac{\lvert \alpha\rvert}{\lambda}, 0 \rbrace,$ then

\[
k_\lambda (x)
= \frac{1}{2\pi \lambda} \cdot \frac{\sin^2(\frac{\lambda x}{2})}{(\frac{x}{2})^2}
\]

---

## Example 10-3.
Let $p(\alpha) = e^{- \frac{\alpha^{2}}{2} }$, then
\[
G(x)
= \frac{1}{\sqrt{2\pi}}\, e^{- \frac{x^2}{2}},
\]
\[
G_{\lambda}(x)
= \frac{\lambda}{\sqrt{2\pi}}\, e^{- \frac{(\lambda x)^2}{2}},
\]



---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

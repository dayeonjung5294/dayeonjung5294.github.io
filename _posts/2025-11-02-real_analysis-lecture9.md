---
layout: post
title: "Real Analysis Lecture 9: Fourier Series"
date: 2025-11-02
categories: [Real_analysis]
use_math: True
---

> *Disclaimer:* This post is a personal study note based on the Real Analysis course I attended.  
> The explanations and formulations are written in my own words for educational purposes only,  
> and do not reproduce or distribute any copyrighted material from the original lectures.


# (09a) Fourier Series of Periodic Functions <!-- % 주기함수의 푸리에 급수 -->

## Introduction
Fourier series express a periodic function as a sum of complex exponentials.  
For a $2\pi$-periodic function $f$, (i.e. $f(t + 2\pi) = f(t)$) the basic idea is:

\[
f(t) \sim \sum_{n\in\mathbb{Z}} \widehat{f}(n) e^{int}.
\]

Here  
- $e^{int}$ are the *Fourier basis functions*,  
- $\widehat{f}(n)$ are the *Fourier coefficients*,  
- and the symbol $\sim$ represents convergence in an appropriate sense (e.g., $L^2$, pointwise a.e., etc.).

---

Let  
\[
\mathbb{T} = \mathbb{R}/2\pi\mathbb{Z} = ( -\pi, \pi \rbrack.
\]


- If $f, g \in L^1(\mathbb{T} )$, then $f \ast g \in L^1(\mathbb{T} )$ and 
  $\lVert f \ast g \rVert_1 \le \lVert f \rVert_1 \lVert g \rVert_1$

- If $f \in L^1(\mathbb{T} )$, then $x \mapsto \tau_x f$ is **uniformly continuous** as a map $\mathbb{T}  \to L^1(\mathbb{T} )$,
  
  where $\tau_x f(t) = f(t+x)$

- $C(\mathbb{T} )$ is dense in $L^1(\mathbb{T} )$

---

The Fourier coefficients of $f\in L^1(\mathbb{T} )$ are defined as  
\[
\widehat{f}(n)
=
\int_{\mathbb{T} } f(t)\, e^{-int}\, dt.
\]

Define
\[
u_n(t) = e^{int}, \qquad n\in\mathbb{Z}.
\]

They satisfy the orthogonality relation
\[
\langle u_n, u_m \rangle
= \,\delta_{nm}.
\]

Thus, $\{u_n\}$ forms an orthogonal system in $L^2(\mathbb{T} )$.  
<!-- % e^{int}는 직교기저 역할 -->

---

Let $f : \mathbb{T}  \to \mathbb{C}$. (Define $\int_\mathbb{T}  f = \frac{1}{2\mathbb{T} } \int_{-\mathbb{T} }^\mathbb{T}  f(t) dt$ )

- $\widehat{f \ast u_n}(m) = \widehat{f}(m) \cdot \widehat{u_n}(m) = \widehat{f}(n) \cdot \delta_{nm} $
  
  $\Rightarrow \widehat{f \ast u_n} = \widehat{f}(n) \cdot e_n = \widehat{f}(n) \cdot \widehat{u_n}$
  
  $\Rightarrow f \ast u_n = \widehat{f}(n)\, u_n.$


---
---

# (09b) Fejér Kernel <!-- % 페제르핵 -->

## Theorem 9-1.

Let $h_n \in L^1(\mathbb{T})$ satisfy:
\[
h_n \ge 0,\qquad 
\int_{\mathbb{T}} h_n = 1,\qquad
\forall \delta \in (0,\pi),\;
\lim_{n\to\infty} \int_{\mathbb{T} \setminus [-\delta,\delta]} h_n = 0.
\]

Then for any $ f \in L^1(\mathbb{T})$,
\[
\lVert f - f\ast h_n \rVert_1 \longrightarrow 0.
\]


### pf)

For each $t \in \mathbb{T}$,

\[
f(t) - (f\ast h_n)(t)
= \int_{\mathbb{T}} h_n(s)\, ( f(t)-f(t-s) ) \, ds.
\]

Taking $L^1$-norm:

\[
\lVert f - f\ast h_n \rVert_1
\le \int_{\mathbb{T}} \int_{\mathbb{T}} h_n(s)\, \lvert f(t) - f_s(t) \rvert \, dt ds,
= \int_{\mathbb{T}} h_n(s)\, \lVert f - f_s \rVert_1\, ds,
\]
where $f_s(t)=f(t-s)$.

For any $\varepsilon>0$, $\exists\, \delta>0$ s.t.
\[
|s|<\delta \Rightarrow \lVert f - f_s \rVert_1 < \varepsilon.
\]

Split the integral:

1. On $\lvert s\rvert <\delta$: $\int_{[-\delta, \delta]} h_n(s)\, \lVert f-f_s\rVert_1 \,ds <\varepsilon$.
2. On $|s|\ge\delta$:  
   \[
   \int_{\mathbb{T} \setminus [-\delta, \delta]} h_n(s)\, \lVert f-f_s\rVert_1 \,ds
     \le 2\lVert f\rVert_1 \int_{\mathbb{T} \setminus [-\delta, \delta]} h_n(s)
     \longrightarrow 0.
   \]

Hence
\[
\lVert f - f\ast h_n \rVert_1 \to 0.
\]

---

## Theorem 9-2.

If $f \in C(\mathbb{T})$, then  
\[
\lVert f - f\ast h_n\rVert_{\sup} \to 0.
\]

### Proof

Because $f$ is uniformly continuous on compact $\mathbb{T}$,  
for any $\varepsilon>0$ there exists $\delta>0$ such that
\[
|s|<\delta \Rightarrow |f(t)-f(t-s)|<\varepsilon.
\]

Then

\[
|f(t) - (f\ast h_n)(t)|
\le \int_{\mathbb{T}} h_n(s)\, |f(t)-f(t-s)|\, ds.
\]

Split into $\lvert s\rvert<\delta$ and $\lvert s\rvert\ge\delta$ regions, obtain

\[
\lVert f - f\ast h_n\rVert_{\sup} \to 0.
\]

---

## Property 9-1.
Trigonometric polynomials $T(\mathbb{T})$ are dense in $L^1(\mathbb{T})$.

## Property 9-2.  
If $\widehat{f}(n)=0$ for all $n\in\mathbb{Z}$, then $f=0$ a.e.

### Proof  
Fejér means satisfy  
\[
\sigma_n(f) = f \ast h_n = \sum_{k=-\infty}^{\infty} \widehat{f}(k)\widehat{h_n}(k)u_k.
\]
All coefficients vanish ⇒ every Fejér mean is identically 0 ⇒  
\[
f = \lim_{n\to\infty} f\ast h_n = 0 \quad\text{a.e.}
\]

## Property 9-3.  
If $\widehat{f} \in \ell^1(\mathbb{Z})$, then

\[
f(t) = \sum_{n=-\infty}^{\infty} \widehat{f}(n) e^{int}
\]
uniformly.

### Proof  
Absolute convergence of  
\[
\sum |\widehat{f}(n)| < \infty
\]
implies uniform convergence of the Fourier series, and the limit must equal $f$.

## Property 9-4.  
If $f \in L^1(\mathbb{T})$, then Fejér means converge uniformly  
iff $f\in C_0(\mathbb{Z})$.




---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

---
layout: post
title: "Real Analysis Lecture 0 — What is an Integral?"
date: 2025-10-05
categories: [Real_analysis]
---

# 📘 Lecture 0: Introduction and Motivation for Measure

## [00a] What is an Integral?

### 1. Quadrature <!-- % 구적법 -->
The process of approximating area under a curve by partitioning an interval and summing up rectangular areas. (foundation of the Riemann integral)

\[
\lim_{n \to \infty} \sum_{k=1}^n f(\frac{k}{n}) \cdot \frac{1}{n}
\]

---

### 2. Riemann Integral <!-- % 리만 적분 -->
\[
\lim_{n \to \infty} \sum_{k=1}^n f(s_k) (x_k - x_{k-1}) \rightarrow A
\]
where \( x_{k-1} \le s_k \le x_k \).

A function is Riemann integrable if and only if the set of all its discontinuities has measure zero 




#### Goal
For a set \( E \subset \mathbb{R} \), we aim to define a function  
\[
\mu : 2^{\mathbb{R}} \to [0, \infty]
\]
that assigns a meaningful **measure** (length, area, volume) to \(E\).

#### Length of Intervals
- For an open interval \((a,b)\),
  \[
  l((a,b)) = b - a
  \]
- For disjoint intervals \((a,b)\) and \((c,d)\),
  \[
  l((a,b) \cup (c,d)) = (b - a) + (d - c)
  \]
- In general,
  \[
  l\left(\bigcup_{n=1}^\infty (a_n,b_n)\right) = \sum_{n=1}^\infty (b_n - a_n)
  \]

#### Open Set Representation
Let \( U \subset \mathbb{R} \) be open.  
For each \( x \in U \):

\[
a_x = \inf \{ a \mid (a,x) \subset U \}, \quad
b_x = \sup \{ b \mid (x,b) \subset U \}
\]

Then each \(x\) belongs to the interval \((a_x,b_x)\), and
\[
U = \bigcup_{x \in U} (a_x,b_x)
\]
Thus, every open set can be expressed as a countable union of disjoint intervals. 

#### Measure Definition
Define the **measure** as
\[
\mu(E) := \inf \{ \mu(U) \mid U \text{ open},\, E \subset U \}
\]

---

### Definition — Riemann–Stieltjes Integral *(for reference)* <!-- % 리만-스틸체스 적분 -->
Let \( f: [a,b] \to \mathbb{R} \) be bounded <span style="color:red">\( (\alpha: [a,b] \to \mathbb{R} \) be a monotone increasing function.)</span>

Let \( P = \{x_0, x_1, \dots, x_n\} \in \mathcal{P}[a, b] \).

#### Upper and Lower Sums
\[
U(P,f,{\color{red}{\alpha}}) = \sum_{i=1}^{n} M_i ({\color{red}{\alpha}}(x_i) - {\color{red}{\alpha}}(x_{i-1})), \quad 
M_i = \sup_{x \in [x_{i-1}, x_i]} f(x)
\]
\[
L(P,f,{\color{red}{\alpha}}) = \sum_{i=1}^{n} m_i ({\color{red}{\alpha}}(x_i) - {\color{red}{\alpha}}(x_{i-1})), \quad 
m_i = \inf_{x \in [x_{i-1}, x_i]} f(x)
\]

#### Integrability Condition
Let 
\[
\overline{\int_a^b} f {\color{red}{d\alpha}} = \inf \{ U_a^b(f, p, {\color{red}{\alpha}}): p \in \mathcal{P}[a,b]  \}
\]
\[
\underline{\int_a^b} f {\color{red}{d\alpha}} = \sup \{ U_a^b(f, p, {\color{red}{\alpha}}): p \in \mathcal{P}[a,b]  \}
\]

We say \( f \) is **Riemann–Stieltjes integrable** <span style="color:red">(with respect to \( \alpha \))</span> ($f \in \mathcal{R}(\alpha)$) if
\[
\overline{\int_a^b} f {\color{red}{d\alpha}}  = \underline{\int_a^b} f {\color{red}{d\alpha}} = \int_a^b f {\color{red}{d\alpha}} 
\]
\[
\Leftrightarrow  \forall \varepsilon > 0, \ \exists P \ \textit{s.t} \; \; U(f,P, {\color{red}{\alpha}}) - L(f,P, {\color{red}{\alpha}}) < \varepsilon
\]
\[
\Leftrightarrow  \forall \varepsilon > 0, \ \exists P_0 \ \textit{s.t} \; \; P_o \subseteq P \Rightarrow U(f,P, {\color{red}{\alpha}}) - L(f,P, {\color{red}{\alpha}}) < \varepsilon
\]

---

📚 *Reference:* [Real Analysis Lecture by Prof. Seung-Hyeok Kye (SNU)](https://www.math.snu.ac.kr/~kye/lecture_V/V_real/index.html)

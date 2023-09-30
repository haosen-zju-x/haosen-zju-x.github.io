---
title: Problems in Linear Algebra
description: null
date: 2023-09-30T22:04:40.775Z
draft: false
slugs: linear-algebra-problem-solving
tags:
  - Undergraduate
  - Linear Algebra
  - Problem Solving
categories:
  - Algebra
markup: pandoc
---

What's next?

<p align="center" style="font-size:40px;">
**--- No.3 ---**
</p>

Shihe asked me the following problem on October 23, 2022. After a while, we exchanged our proofs, which I felt faithfully reflected the differences in the way we do math.

**Problem [Existence of a *suitable* orthogonal projection]**

Let $L\subset \mathbb{R}^{n+l}$ ($n,l\ge 1$) be an $n$-dimensional subspace and $\{v_1,\cdots,v_{n+l}\}$ a basis of $\mathbb{R}^{n+l}$. Show that there exist $1\le j_1<\cdots<j_n\le n+l$ such that the restriction $P_{j_1,\cdots,j_n}|_L:L\to \mathbb{R}^{n+l}$ is injective (and hence induces an isomphism), where $P_{j_1,\cdots,j_n}$ denotes the orthogonal projection of $\mathbb{R}^{n+l}$ onto $\text{span}\{v_{j_1},\cdots,v_{j_n}\}$.

**Proof I [Haosen]**

The orthogonal complement of the kernel of $P_{j_1,\cdots,j_n}|_L$ is
$$\begin{align*}
	\ker(P_{j_1,\cdots,j_n}|_L)^{\perp}
	&=\left(\ker(P_{j_1,\cdots,j_n})\cap L\right)^{\perp}\\
	&=\left(\text{span}(\{v_{j_1},\cdots,v_{j_n}\})^{\perp}\cap L\right)^{\perp}\\
	&=\text{span}(\{v_{j_1},\cdots,v_{j_n}\})+L^{\perp}.
\end{align*}$$
Therefore $P_{j_1,\cdots,j_n}|_L$ is injective iff $\text{span}(\{v_{j_1},\cdots,v_{j_n}\})+L^{\perp}=\mathbb{R}^{n+l}$.

Let $\{w_1,\cdots,w_l\}$ be a basis of the $l$-dimensional subspace $L^{\perp}$. There exists $A\in M_{(n+l)\times l}(\mathbb{R})$ of rank $l$ such that
$$
(w_1\ \cdots\ w_l)=(v_1\ \cdots\ v_{n+l})A.
$$
Now we note that there exists a sequence of elementary column operations that transforms $A$ into a matrix with exactly $n$ zero rows, in other words, there exists $Q\in GL_{l}(\mathbb{R})$ such that $AQ$ has exactly $n$ zero rows, with the other $l$ nonzero rows being linearly independent. We claim that the labels of the zero rows, denoted by $1\le j_1<\cdots<j_n\le n+l$, will fulfill the proof. For clarity, denote by $1\le i_1<\cdots<i_l\le n+l$ the labels of the nonzero rows.

In fact, $L^{\perp}=\text{span}(\{w_1,\cdots,w_l\})=$ the column space of the matrix $(w_1\ \cdots\ w_l)=$ the column space of the matrix $(w_1\ \cdots\ w_l)Q=$ the column space of the matrix $(v_1\ \cdots\ v_{n+l})AQ=\text{span}(\{v_{i_1},\cdots,v_{i_l}\})$. Therefore, $\text{span}(\{v_{j_1},\cdots,v_{j_n}\})+L^{\perp}=\text{span}(\{v_1,\cdots,v_{n+l}\})=\mathbb{R}^{n+l}$. $\blacksquare$

**Proof II [Shihe]**

Shehe's proof is more geometrically intuitive. For each $1\le k\le n+l$, take a nonzero vector $w_k\in \mathbb{R}^{n+l}$ such that $\text{span}(\{w_k\})=\text{span}(\{v_1,\cdots,v_{n+l}\}\setminus\{v_k\})^{\perp}$. We claim that $w_1,\cdots,w_{n+l}$ are linearly independent.

In fact, if $\sum_{k=1}^{n+l}\lambda_k w_k=0$ ($\lambda_1,\cdots,\lambda_{n+l}\in \mathbb{R}$), then by applying $\langle \cdot,v_k\rangle$ to both sides we get $\lambda_k\langle w_k,v_k\rangle=0$ ($k=1,\cdots,n+l$). Clearly $\langle w_k,v_k\rangle\neq 0$, because otherwise $w_k$ is orthogonal to every vector in the basis $\{v_1,\cdots,v_{n+l}\}$ and hence must be zero, contradiction. Thus $\lambda_k=0\ (k=1,\cdots,n+l)$, showing that $w_1,\cdots,w_{n+l}$ are linearly independent.

Since $\dim L=n<n+l$, there exists some $w_{k_1}$ that is not in $L$. The orthogonal projection of $\mathbb{R}^{n+l}$ along $\text{span}(\{w_{k_1}\})$, denoted by $P_{w_{k_1}}:\mathbb{R}^{n+l}\to \mathbb{R}^{n+l}$, induces an isomorphism when restricted to $L$, as $\ker(P_{w_{k_1}}|_L)=\text{span}(\{w_{k_1}\})\cap L=0$. Moreover,
$$
\text{Im}(P_{w_{k_1}})=\ker(P_{w_{k_1}})^{\perp}=\text{span}(\{w_{k_1}\})^{\perp}=\text{span}(\{v_1,\cdots,v_{n+l}\}\setminus\{v_{k_1}\}).
$$

If $l=1$, we're done. If $l\ge 2$, then $\dim P_{w_{k_1}}(L)=n<n+l-1$ and so there exists $k_2\neq k_1$ such that $w_{k_2}\notin P_{w_{k_1}}(L)$. The orthogonal projection of $\text{Im}(P_{k_1})$ along $\text{span}(\{w_{k_2}\})$, denoted by $P_{w_2}:\text{Im}(P_{w_1})\to \text{Im}(P_{w_1})$, induces an isomorphism when restricted to $P_{w_{k_1}}(L)$, as $\ker(P_{w_{k_2}}|_{P_{w_{k_1}}(L)})=\text{span}(\{w_{k_2}\})\cap P_{w_1}(L)=0$. Moreover,
$$
\text{Im}(P_{w_{k_2}})=\ker(P_{w_{k_2}})^{\perp}=\text{span}(\{w_{k_2}\})^{\perp}=\text{span}(\{v_1,\cdots,v_{n+l}\}\setminus\{v_{k_1},v_{k_2}\}).
$$
Continue this process inductively until we get $P_{w_l}$. Then
$$
P:\mathbb{R}^{n+l}\to \mathbb{R}^{n+l}\quad P(v):=P_{w_l}\circ\cdots\circ P_{w_2}\circ P_{w_1}(v)
$$
is a well-defined orthogonal projection of $\mathbb{R}^{n+l}$ on $\text{span}(\{v_1,\cdots,v_{n+l}\}\setminus\{v_{k_1},\cdots,v_{k_l}\})$, fulfilling the proof. $\blacksquare$





<p align="center" style="font-size:40px;">
**--- No.2 ---**
</p>

In early February 2023, I asked myself the following seemingly naive question.

**Problem [The Gramian determines the *shape*]**

Let $\{v_1,\cdots,v_s\}$ and $\{w_1,\cdots,w_s\}$ be two subsets of $\mathbb{R}^n$. Show that there exists $A\in O(n)$ such that $Av_i=w_i\ (1\le i\le s)$ iff $\langle v_{i}, v_{j}\rangle=\langle w_{i}, w_{j}\rangle\ (1\le i,j\le s)$, i.e., the two Gramians are equal.

(Similarly, if $\{v_1,\cdots,v_s\}$ and $\{w_1,\cdots,w_s\}$ are two subsets of $\mathbb{C}^n$, then there exists $A\in U(n)$ such that $Av_i=w_i\ (1\le i\le s)$ iff $\langle v_{i}, v_{j}\rangle=\langle w_{i}, w_{j}\rangle\ (1\le i,j\le s)$, i.e., the two Gramians are equal.)

**Proof [Haosen]** We summarize the idea of proving $(\Leftarrow)$ as follows. Given the data $\langle v_i,v_j \rangle\ (1\le i,j\le s)$, we may focus on a maximal linearly independent subset of $\{v_1,\cdots,v_s\}$ to study the shape formed by these $s$ vectors in $\mathbb{R}^n$. Suppose that $\{v_{k_1},\cdots,v_{k_r}\}$ is a maximal linearly independent subset of $\{v_1,\cdots,v_s\}$, then $\{w_{k_1},\cdots,w_{k_r}\}$ is automatically a maximal linearly independent subset of $\{w_1,\cdots,w_s\}$. Perform Gram-Schmidt on them simultaneously and extend the resulted orthonormal subsets to two orthonormal bases for $\mathbb{R}^n$. The associated change of coordinates matrix then fulfills the proof. (The Gram-Schmidt process can be embodied by QR decomposition.)

$(\Rightarrow)$: Obvious.
$$
\begin{align*}
G(w_1,\cdots,w_s)&=(w_{1}\ \cdots\ w_{s})^{T}(w_{1}\ \cdots\ w_{s})\\
&=(v_{1}\ \cdots\ v_{s})^{T}A^TA(v_{1}\ \cdots\ v_{s})\\
&=(v_{1}\ \cdots\ v_{s})^{T}(v_{1}\ \cdots\ v_{s})=G(v_1,\cdots,v_s).\end{align*}
$$
$(\Leftarrow)$: Note that
$$\begin{align*}\text{rank}(v_{1}\ \cdots\ v_{s})&=\text{rank}\, G(v_1,\cdots,v_{s})\\ &=\text{rank}\, G(w_1,\cdots,w_s)=\text{rank}(w_{1}\ \cdots\ w_{s})\end{align*}$$
Denote $r:=\text{rank}(v_{1}\ \cdots\ v_{s})$. Without loss of generality, assume that $v_1,\cdots,v_r$ are linearly independent. We claim that $w_1,\cdots,w_r$ are linearly independent as well. Indeed,
$$
\begin{align*}
\text{Null}\,(w_1\ \cdots\ w_r)&=\text{Null}\,(w_1\ \cdots\ w_r)^T(w_1\ \cdots\ w_r)\\
&=\text{Null}\,(v_1\ \cdots\ v_r)^T(v_1\ \cdots\ v_r)=\text{Null}\,(v_1\ \cdots\ v_r)=0.
\end{align*}
$$
Therefore, there exist $B,C\in M_{r\times (s-r)}(\mathbb{R})$ such that
$$
\begin{align*}
(v_1\ \cdots\ v_s)&=(v_1\ \cdots\ v_r)(I_r\ |\ B),\\
(w_1\ \cdots\ w_s)&=(w_1\ \cdots\ w_r)(I_r\ |\ C).
\end{align*}
$$
Denote $G:=G(v_1,\cdots,v_r)=G(w_1,\cdots,w_r)$. Since $\text{rank}(G)=\text{rank}(v_1\ \cdots\ v_r)=r$, the matrix $G$ is invertible. Thus we have
$$
\begin{pmatrix}
I_r\\\hline B^T
\end{pmatrix}\,G\,(I_r\ |\ B)=\begin{pmatrix}
I_r\\\hline C^T
\end{pmatrix}\,G\,(I_r\ |\ C)\implies GB=GC\implies B=C.
$$
Now, it suffices to find some $A\in O(n)$ such that
$$
A(v_1\ \cdots\ v_r)=(w_1\ \cdots\ w_r)
$$
By QR decomposition, we have
$$
(v_1\ \cdots\ v_r)=Q_1R_1,\quad (w_1\ \cdots\ w_r)=Q_2R_2
$$
where $R_i\in M_{r\times r}(\mathbb{R})$ is an upper triangular matrix with positive diagonal entries and $Q_i\in M_{n\times r}(\mathbb{R})$ satisfies $Q_i^TQ_i=I_r$ (semi-orthogonal). Thus we have
$$
(Q_1R_1)^TQ_1R_1=(Q_2R_2)^TQ_2R_2\implies R_1^TR_1=R_2^TR_2.
$$
By the uniqueness of Cholesky decomposition for positive-definite matrices, we have $R_1=R_2$. Indeed, $R_1R_2^{-1}=(R_1^{T})^{-1}R_2^T$ is upper triangular and lower triangular, and hence a diagonal matrix, denoted by $D$. Thus we have
$$
R_1=DR_2,\ R_2^T=R_1^TD\implies D=I_r\implies R_1=R_2.
$$

Therefore, it suffices to find some $A\in O(n)$ such that
$$
AQ_1=Q_2.
$$
Since the columns of $Q_i$ forms an orthonormal subset of $\mathbb{R}^n$ and thus extends to an orthonormal basis for $\mathbb{R}^n$, there exists $\widetilde{Q}_i\in O(n)$ such that $\widetilde{Q}_i=(Q_i\ |\ X_i)$ for some $X_i\in M_{n\times (n-r)}(\mathbb{R})$. Define $A:=\widetilde{Q}_2\widetilde{Q}_1^{-1}$. Then $A\in O(n)$ and $AQ_1=Q_2$, as desired. $\blacksquare$





<p align="center" style="font-size:40px;">
**--- No.1 ---**
</p>

The next was one of the problems in my entrance examination of École Polytechnique, in November 2021. It estimates the size of a set of unit vectors that are "almost orthonormal".

**Problem [*Almost* orthonormal]**

Show that if $v_1,\cdots,v_m$ are $m$ unit vectors in $\mathbb{C}^n$ such that $|\langle v_i,v_j \rangle|\le \frac{1}{2\sqrt{n}}$ for any $i\neq j$, then $m<2n$.

**Proof [Haosen, under the guidance of the examiner]**

Let $G:=G(v_1,\cdots,v_m)$ be the Gramian, i.e., $G(i,j)=\langle v_i,v_j \rangle$ for $1\le i,j\le m$. Define $H:=G-I_m$. Since $H$ is Hermitian, we have
$$
\begin{align*}
\text{tr}(H^2)&=\text{tr}(H^*H)\\
&=\sum_{i,j=1}^{m}|H(i,j)|^2\\
&=\sum_{1\le i\neq j\le m}|\langle v_i,v_j\rangle|^2\\
&\le (m^2-m)\cdot (\tfrac{1}{2\sqrt{n}})^2=\frac{m^2-m}{4n}.
\end{align*}
$$
On the other hand, since $G$ is positive semi-definite, $G$ has $r:=\text{rank}(G)=\text{rank}(v_1\ \cdots\ v_m)\le n$ positive eigenvalues, and the other $m-r$ eigenvalues of $G$ are all zero. (In fact, we only use the latter.) Consequently, the eigenvalues of $H$ are $\underbrace{\lambda_1,\cdots,\lambda_r}_{\in (-1,+\infty)},\underbrace{-1,\cdots,-1}_{m-r}$, and the eigenvalues of $H^2$ are $\underbrace{\lambda_1^2,\cdots,\lambda_r^2}_{\in [0,+\infty)},\underbrace{1,\cdots,1}_{m-r}$. Therefore,
$$
\text{tr}(H^2)=\sum_{i=1}^{r}\lambda_i^2+(m-r)\ge m-n.
$$
Combining the two estimates, we conclude that
$$
m-n\le \frac{m^2-m}{4n},
$$
from which $m<2n$ follows. $\blacksquare$
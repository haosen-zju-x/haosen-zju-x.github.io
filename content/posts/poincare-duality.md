---
title: Poincaré Duality
description: Explain the ideas behind the construction of the chain homotopy in the proof of the Poincaré lemma for compactly supported cohomology (cf. Bott-Tu, *Differential Forms in Algebraic Topology*).
date: 2023-09-30T20:16:07.758Z
draft: false
slugs: poincare-duality
tags:
  - Algebraic Topology
  - Differentiable Manifolds
categories:
  - Topology
markup: pandoc
---

<!-- <link rel="stylesheet" type="text/css" href="https://tikzjax.com/v1/fonts.css">
<script src="https://tikzjax.com/v1/tikzjax.js"></script>
<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (1in);
  \end{tikzpicture}
</script> -->

# The Poincaré Lemma for Compactly Supported Cohomology

Let $M$ be a smooth manifold. Then the product manifold $M\times \mathbb{R}^1$ is a smooth manifold as well, and the projection $\pi:M\times \mathbb{R}^1\to M$ is a smooth map. The pullback $\pi^*:\Omega^*(M)\to \Omega^*(M\times \mathbb{R}^1)$ [[^脚注]] does not map $\Omega_c^*(M)$ into $\Omega_c^*(M\times \mathbb{R}^1)$, so instead we consider the pushforward known as integration along the fiber
$$
\begin{equation*}
	\pi_*:\Omega_c^*(M\times \mathbb{R}^1)\to \Omega_c^{*-1}(M)\quad \begin{cases}
		f(x,t)\pi^*\phi\mapsto 0\\
		f(x,t)\mathrm{d}{t}\wedge\pi^*\phi\mapsto \left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi
	\end{cases}
\end{equation*}
$$
where $\phi\in \Omega^*(M)$ and  $f\in C_c^{\infty}(M\times \mathbb{R};\mathbb{R})$. (These two types of elements in $\Omega_c^*(M\times \mathbb{R}^1)$ will soon be revisited.) It's quick to check that $\pi_*$ is a chain map. We will show that the induced map $\pi_*:H_c^*(M\times \mathbb{R}^1)\to H_c^{*-1}(M)$ is an isomorphism.

Take $e=e(t)\mathrm{d}{t}\in \Omega_c^1(\mathbb{R}^1)$ such that $\displaystyle\int_{\mathbb{R}^1} e=1$. Define
$$
\begin{equation*}
	e_*:\Omega_c^*(M)\to \Omega_c^{*+1}(M\times \mathbb{R}^1)\quad \psi\mapsto e(t)\mathrm{d}{t}\wedge\pi^*\psi
\end{equation*}
$$
where the map $t\mapsto e(t)$ has been identified with the composition $(x,t)\mapsto t\mapsto e(t)$. It's quick to check that $e_*$ is a chain map, and $\pi_*\circ e_*=\text{id}$ on $\Omega_c^*(M)$. We will show that there is a chain homotopy $K$ connecting $e_*\circ \pi_*$ and $\text{id}$ on $\Omega_c^*(M\times \mathbb{R}^1)$, so that the induced map $e_*:H_c^{*}(M)\to H_c^{*+1}(M\times \mathbb{R}^1)$ is the inverse of $\pi_*:H_c^*(M\times \mathbb{R}^1)\to H_c^{*-1}(M)$.

We shall construct the desired chain homotopy $K:\Omega_c^*(M\times \mathbb{R}^1)\to \Omega_c^{*-1}(M\times \mathbb{R}^1)$ from the basic relation
$$
\begin{equation*}
	\text{id}-e_*\circ \pi_*=\mathrm{d}K+K \mathrm{d}
\end{equation*}
$$
To proceed, interpret this relation on the aforementioned two types of elements in $\Omega_c^*(M\times \mathbb{R}^1)$, and be reminded that computations will be done w.r.t. some specific local coordinates.

- For $f(x,t)\pi^*\phi$, we require
$$
	\begin{equation*}
		f(x,t)\pi^*\phi=\mathrm{d}K(f(x,t)\pi^*\phi)+K \left[\left(\displaystyle\sum_i \dfrac{\partial f}{\partial x^i}(x,t)\mathrm{d}{x^i}+\dfrac{\partial f}{\partial t}(x,t)\mathrm{d}{t}\right)\wedge \pi^*\phi+f(x,t)\pi^*\mathrm{d}{\phi}\right]
	\end{equation*}
$$
- For $f(x,t)\mathrm{d}{t}\wedge\pi^*\phi$, we require
$$
	\begin{align*}
		&f(x,t)\mathrm{d}{t}\wedge\pi^*\phi-e(t)\mathrm{d}{t}\wedge\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]\\
		&=\mathrm{d}K(f(x,t)\mathrm{d}{t}\wedge\pi^*\phi)+K \left[-\displaystyle\sum_i \dfrac{\partial f}{\partial x^i}(x,t)\mathrm{d}{t}\wedge\mathrm{d}{x^i}\wedge\pi^*\phi-f(x,t)\mathrm{d}{t}\wedge\pi^*\mathrm{d}{\phi}\right]
	\end{align*}
$$

We observe that when $\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t=0$, or equivalently, $f\in \dfrac{\partial }{\partial t}(C_c^{\infty}(M\times \mathbb{R}^1))$, the two requirements become very close. An immediate guess follows:
$$
\begin{equation*}
	K_1(f(x,t)\pi^*\phi)=0,\quad K_1(f(x,t)\mathrm{d}{t}\wedge\pi^*\phi)=\left(\displaystyle\int_{-\infty}^{t} f(x,t) \,\mathrm{d}t\right)\pi^*\phi
\end{equation*}
$$
whenever $\phi\in \Omega^*(M)$ and $f\in C_c^*(M\times \mathbb{R}^1)$. While $K_1$ solves the first requirement, it does not reconcile with the second:
$$
\begin{align*}
	&\mathrm{d}K_1(f(x,t)\mathrm{d}{t}\wedge\pi^*\phi)+K_1 \left[-\displaystyle\sum_i \dfrac{\partial f}{\partial x^i}(x,t)\mathrm{d}{t}\wedge\mathrm{d}{x^i}\wedge\pi^*\phi-f(x,t)\mathrm{d}{t}\wedge\pi^*\mathrm{d}{\phi}\right]\\
	=&\mathrm{d}\left[\left(\displaystyle\int_{-\infty}^{t} f(x,t) \,\mathrm{d}t\right)\pi^*\phi\right]-\displaystyle\sum_i \left(\displaystyle\int_{-\infty}^{t} \dfrac{\partial f}{\partial x^i}(x,t) \,\mathrm{d}t\right)\mathrm{d}{x^i}\wedge \pi^*\phi-\left(\displaystyle\int_{-\infty}^{t} f(x,t) \,\mathrm{d}t\right)\pi^*\mathrm{d}{\phi}\\
	=&f(x,t)\mathrm{d}{t}\wedge \pi^*\phi
\end{align*}
$$
However, the computation also indicates that we are not far away from success, with only one term involving $e=e(t)\mathrm{d}{t}$ missing.

As a remedy, consider $K_2=K-K_1$. It suffices to construct $K_2$ in the same fashion:

- For $f(x,t)\pi^*\phi$, we require
$$
	\begin{equation*}
		0=\mathrm{d}K_2(f(x,t)\pi^*\phi)+K_2 \left[\left(\displaystyle\sum_i \dfrac{\partial f}{\partial x^i}(x,t)\mathrm{d}{x^i}+\dfrac{\partial f}{\partial t}(x,t)\mathrm{d}{t}\right)\wedge \pi^*\phi+f(x,t)\pi^*\mathrm{d}{\phi}\right]
	\end{equation*}
$$
- For $f(x,t)\mathrm{d}{t}\wedge\pi^*\phi$, we require
$$
	\begin{align*}
		&-e(t)\mathrm{d}{t}\wedge\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]\\
		&=\mathrm{d}K_2(f(x,t)\mathrm{d}{t}\wedge\pi^*\phi)+K_2 \left[-\displaystyle\sum_i \dfrac{\partial f}{\partial x^i}(x,t)\mathrm{d}{t}\wedge\mathrm{d}{x^i}\wedge\pi^*\phi-f(x,t)\mathrm{d}{t}\wedge\pi^*\mathrm{d}{\phi}\right]
	\end{align*}
$$

It is again natural to set $K_2(f(x,t)\pi^*\phi)=0$, and so the first requirement simplifies to
$$
\begin{equation*}
	K_2 \left(\dfrac{\partial f}{\partial t}(x,t)\mathrm{d}{t}\wedge \pi^*\phi\right)=0
\end{equation*}
$$
Now we focus on the second requirement. Note that
$$
\begin{align*}
	&\hphantom{=}e(t)\mathrm{d}{t}\wedge\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]\\
	&=\mathrm{d}\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\wedge\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]+\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\mathrm{d}\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]\\
	&\hphantom{=\mathrm{d}\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\wedge\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]}-\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\mathrm{d}\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]\\
	&=\mathrm{d}\left\{\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]\right\}\\
	&\hphantom{=}-\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\pi^*\left[\displaystyle\sum_i \left(\displaystyle\int_{-\infty}^{\infty} \dfrac{\partial f}{\partial x^i}(x,t) \,\mathrm{d}t\right)\mathrm{d}{x^i}\wedge \phi+\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\mathrm{d}{\phi}\right]
\end{align*}
$$
An immediate guess follows:
$$
\begin{equation*}
	K_2(f(x,t)\mathrm{d}{t}\wedge \pi^*\phi)=-\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]
\end{equation*}
$$
which indeed solves the second requirement, and together with $K_2(f(x,t)\pi^*\phi)=0$, solves the first, since
$$
\begin{equation*}
	\displaystyle\int_{-\infty}^{\infty} \dfrac{\partial f}{\partial t}(x,t) \,\mathrm{d}t=0
\end{equation*}
$$

Conclusion: The map $K:\Omega_c^{*}(M\times \mathbb{R}^1)\to \Omega_c^{*-1}(M\times \mathbb{R}^1)$ defined by
$$
\begin{equation*}
	\begin{cases}
		f(x,t)\pi^*\phi\mapsto 0\\
		f(x,t)\mathrm{d}{t}\wedge\pi^*\phi\mapsto \left(\displaystyle\int_{-\infty}^{t} f(x,t) \,\mathrm{d}t\right)\pi^*\phi-\left(\displaystyle\int_{-\infty}^{t} e(t) \,\mathrm{d}t\right)\pi^*\left[\left(\displaystyle\int_{-\infty}^{\infty} f(x,t) \,\mathrm{d}t\right)\phi\right]
	\end{cases}
\end{equation*}
$$
is a chain homotopy connecting $e_*\circ \pi_*$ and $\text{id}$ on $\Omega_c^*(M\times \mathbb{R}^1)$, and consequently the maps
$$
\begin{equation*}
		H_c^{*+1}(M\times \mathbb{R})\begin{matrix}\xrightarrow{\pi_*}\\ \xleftarrow[e_*]{}\end{matrix}H_c^*(M)
\end{equation*}
$$
are isomorphisms.

As a corollary, for each positive integer $n$, there holds
$$
\begin{equation*}
	H_c^*(\mathbb{R}^n)=\begin{cases}
		\mathbb{R}, &\text{in dimension $n$}\\
		0, &\text{elsewhere}
	\end{cases}
\end{equation*}
$$
where the isomorphism $H_c^*(\mathbb{R}^n)\xrightarrow{\cong}\mathbb{R}$ is given by iterated $\pi_*$, i.e., by integration over $\mathbb{R}^n$, thanks to Fubini's theorem. Besides, by iterating $e_*$, we see that a generator of $H_c^n(\mathbb{R}^n)$ is represented by a bump $n$-form $\alpha=\alpha(x)\mathrm{d}{x^1}\wedge\cdots\wedge \mathrm{d}{x^n}$ with $\displaystyle\int_{\mathbb{R}^n} \alpha=1$, whose support can be made as small as possible.

[^脚注]:[To be explicit, if $\phi\in \Omega^r(M)$ is represented as $\sum_{i_1<\cdots<i_r}\phi_{i_1\cdots i_r}(x)\mathrm{d}{x^{i_1}}\wedge\cdots\wedge \mathrm{d}{x^{i_r}}$ w.r.t. some chosen local coordinates on $M$, then $\pi^*\phi\in \Omega^r(M\times \mathbb{R})$ is simply represented as $\sum_{i_1<\cdots<i_r}\phi_{i_1\cdots i_r}\circ \pi(x,t)\mathrm{d}{x^{i_1}}\wedge\cdots\wedge \mathrm{d}{x^{i_r}}$ w.r.t. the associated local coordinates on $M\times \mathbb{R}^1$.]
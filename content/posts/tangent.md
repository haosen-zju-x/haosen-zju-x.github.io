---
title: Tangent Story
description: null
date: 2023-09-24T20:33:22+02:00
draft: false
slugs: tangent
tags:
  - Differentiable Manifolds
categories:
  - Geometry
markup: pandoc
---

Where the whole story begins.

# Part I : Tangent Spaces & Cotangent Spaces

Let $M$ be a smooth $m$-manifold and $p\in M$. We will define the tangent space and the cotangent space of $M$ at $p$.

## Tangent Space $T_pM$ --- The Geometric Approach

Choose a local chart $(U,\varphi)$ centered at $p$.

Set $C_p:=\{\alpha\in C^{\infty}(I;M) \,|\, \text{$I$ is an open interval containing $0$}, \alpha(0)=p\}$. Define $T_pM:=C_p/\sim$, where $\sim$ is an equivalence relation on $C_p$ defined by $\alpha\sim \beta:\iff (\varphi\circ \alpha)'(0)=(\varphi\circ \beta)'(0)$. If $(V,\psi)$ is another local chart centered at $p$, then we have $(\psi\circ \alpha)'(0)=(\psi\circ \varphi^{-1})'(0) (\varphi\circ \alpha)'(0)$. Therefore the definition of the equivalence relation $\sim$ does not depend on the choice of the local chart, neither does the definition of $T_pM$. The 1-1 correspondence $T_pM\ni [\alpha]\mapsto (\varphi\circ \alpha)'(0)\in \mathbb{R}^m$ induces an $m$-dimensional real vector space structure on $T_pM$. The elements of $T_pM$ (i.e. the equivalence classes of *curves* passing through $p$) are called *tangent vectors*, and $T_pM$ is called the *tangent space of $M$ at $p$*. Denote by $\{\left.\tfrac{\partial }{\partial x^1}\right|_p, \cdots, \left.\tfrac{\partial }{\partial x^m}\right|_p\}$ the base of $T_pM$ corresponding to $\{e_1,\cdots,e_m\}$ in the chosen local chart.

**Remark [Tangent vectors as directional derivatives]**
The following observation motivates the definition of cotangent vectors: we can view tangent vectors as operators taking directional derivatives of smooth functions. For every $\gamma\in C_p$, whenever $f$ is a real-valued $C^{\infty}$ function on an open neighborhood of $p$, define
\begin{equation*}
	[\gamma]f:=D_{\gamma}(f)=\left.\dfrac{\mathrm{d}}{\mathrm{d}t}\right|_{t=0}(f\circ \gamma)(t).
\end{equation*} 
To justify this definition we note that
\begin{equation*}
	D_{\gamma}(f)=\nabla(f\circ \varphi^{-1})(0)\cdot (\varphi\circ \gamma)'(0),
\end{equation*}
which shows that $D_\gamma$ (taking derivatives along $\gamma$) is completely determined by the equivalence class of $\gamma$, i.e., the tangent vector $[\gamma]$. This identity also shows that
\begin{equation*}
	\left.\dfrac{\partial }{\partial x^i}\right|_p f=\partial_i (f\circ \varphi^{-1})(0)
\end{equation*}
and moreover: $([\alpha]+[\beta])f=[\alpha]f+[\beta]f, (\lambda[\alpha])f=\lambda([\alpha]f)$. Soon we will see the precise duality behind these ideas.

We also mention that $[\gamma](f+g)=[\gamma]f+[\gamma]g, [\gamma](\lambda f)=\lambda([\gamma]f)$, and $[\gamma](fg)=([\gamma]f)g(p)+f(p)([\gamma]g)$. This leads to the treatment of tangent spaces as so called *derivations*, which we will skip.

Of course we can just define the cotangent space $T_p^*M$ to be the dual of the tangent space $T_pM$. But it will be beneficial to explore the hidden duality seen above. In the following, we first define cotangent spaces using a standard algebraic approach and then specify the natural duality between $T_pM$ and $T_p^*M$.

## Cotangent Space $T_p^*M$ --- The Algebraic Approach

Set $F_p:=\{(f,U) \,|\, \text{$U$ is an open neighborhood of $p$}, f\in C^{\infty}(U;\mathbb{R})\}/\sim$, where the equivalence relation is as follows: $(f,U)\sim (g,V)$ iff there exists an open neighborhood $W\subset U\cap V$ such that $f|_W=g|_W$. The elements of $F_p$ are called *germs (of the sheaf of smooth functions on $M$)*. In the space of germs at $p$, define $[f,U]+[g,V]:=[f+g,U\cap V]$ and $[f,U]\cdot [g,V]:=[fg,U\cap V]$. Then $(F_p,+,\cdot)$ is a local ring whose unique maximal ideal is $\mathfrak{m}_p:=\{[f]\in F_p \,|\, f(p) = 0\}$ and whose residue field is $\mathbb{R}$. Define the *cotangent space of $M$ at $p$* to be $T_p^*M:=\mathfrak{m}_p/\mathfrak{m}_p^2$.

Let's show that $T_p^*M$ is naturally a real vector space of dimension $m$. Let $x^1,\cdots,x^m$ be a local coordinate system centered at $p$. One can *easily* show that
\begin{equation*}
	\mathfrak{m}_p=\{[f]\in F_p \,|\, \exists [f_i]\in F_p \text{ s.t. } f= \textstyle\sum x^if_i\}=\langle [x^1],\cdots,[x^m] \rangle.
\end{equation*}
Consider the map
\begin{equation*}
	\theta:\mathfrak{m}_p\to \mathbb{R}^n\quad [\textstyle\sum x^if_i]\mapsto (f_1(p),\cdots,f_m(p)).
\end{equation*}
To verify that $\theta$ is well-defined, suppose that $[\sum x^if_i]=[\sum x^ig_i]$. In a suitable open neighborhood of $p$, we have $f_i=g_i$ on the subset $(\cap_{j\neq i} \{x_j=0\})\cap \{x_i\neq 0\}$. By continuity, we get $f_i(p)=g_i(p)$, although $[f_i]$ may not equal to $[g_i]$. Therefore $\theta$ is a well-defined map, and moreover is a surjective homomorphism of $\mathbb{R}$-modules. Now we conclude from $\ker(\theta)=\mathfrak{m}_p^2$ that $T_p^*M=\mathfrak{m}_p/\mathfrak{m}_p^2\cong \mathbb{R}^m$ (as $\mathbb{R}$-modules) and that $T_p^*M=\text{span}\{\mathrm{d}x^1,\cdots,\mathrm{d}x^m\}$, where $\mathrm{d}x^i:=[[x^i]]=[x^i]+\mathfrak{m}_p^2$. The elements of $T_p^*M$ are called *cotangent vectors*.

**Remark [Duality]**
Suppose that the local coordinate system is associated with the local chart used before, i.e., $\varphi=(x^1,\cdots,x^m)$, or equivalently $x^i\circ \varphi^{-1}(x_1,\cdots,x_m)=x_i$. For any $[f]\in \mathfrak{m}_p$, write $f=\sum x^if_i$, then by linearity and Leibniz's rule we have $\left.\tfrac{\partial }{\partial x^j}\right|_p f
=\sum_i [(\left.\tfrac{\partial }{\partial x^j}\right|_px^i)f_i(p)+x^i(p)(\left.\tfrac{\partial }{\partial x^j}\right|_p f_i)]
=\sum_i \partial_j(x^i\circ \varphi^{-1})(0)f_i(p)
=f_j(p)$. More generally,
\begin{equation*}
	[\gamma]f=(\varphi\circ \gamma)'(0)\cdot\theta([f]),\quad \forall [\gamma]\in T_pM.
\end{equation*}
Therefore we have a canonical pairing between $T_pM$ and $T_p^*M$:
\begin{equation*}
	[\gamma][[f]]:=[\gamma]f,\quad\forall ([\gamma],[[f]])\in T_pM\times T_p^*M.
\end{equation*}
Since $\left.\tfrac{\partial }{\partial x^i}\right|_p \mathrm{d}x^j = \left.\tfrac{\partial }{\partial x^i}\right|_p x^j=\partial_i(x^j\circ \varphi^{-1})(0)=\delta_i^j$, the canonical pairing is perfect, showing that the tangent space $T_pM$ and the cotangent space $T_p^*M$ are canonically dual to each other.

## Examples

Coming soon...

# Part II : Tangent Bundles & Cotangent Bundles

Coming soon...

# Part III : Tangent Maps & Cotangent Maps

Coming soon...

# Part IV : Vector Fields & Lie Brackets

Coming soon...

# Part V : Riemannian Metrics

Coming soon...

# Part VI : Levi-Civita Connections

Coming soon...

# Part VII : Exponential Maps

Coming soon...
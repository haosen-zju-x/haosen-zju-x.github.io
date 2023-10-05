---
title: Tests et Régions de Confiance
description: null
date: 2023-10-01T19:24:26.988Z
draft: false
slugs: tests-et-regions-de-confiance
tags:
  - Inférence Statistique
categories:
  - Statistique
markup: pandoc
---

<style>
  p.mybox 
  {
    border-style:dashed;
    border-width:1.5px;
    border-color:blue;
    background-color:#e6e6fa;
    padding-left:10px;
    padding-right:5px;
  }
</style>

<!-- Pour la première fois de ma vie, je pense que les statistiques peuvent être intéressantes et élégantes.

Un grand merci à Prof. Gersende Fort pour ses petites classes très bien faites :)

# Théorie

## Cramér-Rao

Coming soon...

## Neyman-Pearson

Coming soon... -->

# Exercices

## Test de comparaison de deux variances & Test de comparaison de deux moyennes

Considérons le modèle statistique
$$
\left(\mathbb{R}^{n+p},\mathcal{B}(\mathbb{R}^{n+p}),\left\{\mathbb{P}_{\theta}=p_{\theta}\cdot\mathrm{d}\text{Leb}^{\otimes (n+p)}=(\mathcal{N}(\mu_0,\sigma_0^2))^{\otimes n}\otimes (\mathcal{N}(\mu_1,\sigma_1^2))^{\otimes p} \,\Big|\, \theta = (\mu_0,\mu_1,\sigma_0^2,\sigma_1^2)\in \mathbb{R}^2\times (\mathbb{R}_+^*)^2\right\}\right).
$$

<p class="mybox">
  1\. Déterminer l'estimateur du maximum de vraisemblance du paramètre $\theta=(\mu_0,\mu_1,\sigma_0^2,\sigma_1^2)$.
</p>

On remarque que $L(\theta;X_1,\cdots,X_n,Y_1,\cdots,Y_p)=L(\theta_0;X_1,\cdots,X_n)\cdot L(\theta_1;Y_1,\cdots,Y_p)$, où $\theta_0=(\mu_0,\sigma_0^2)$ et $\theta_1=(\mu_1,\sigma_1^2)$. Comme l'estimateur du maximum de vraisemblance du paramètre $\theta_0$ est $\left(\bar{X}_n,V_n\right)$, où
$$
\bar{X}_n:=\frac{1}{n}\sum_{i=1}^{n}X_i,\quad V_n:=\frac{1}{n}\sum_{i=1}^{n}(X_i-\bar{X}_n)^2,
$$
et que l'estimateur du maximum de vraisemblance du paramètre $\theta_1$ est $(\bar{Y}_p,W_p)$, où
$$
\bar{Y}_p:=\frac{1}{p}\sum_{j=1}^{n}Y_j,\quad W_p:=\frac{1}{p}\sum_{j=1}^{p}(Y_j-\bar{Y}_p)^2,
$$
on en conclut que l'estimateur du maximum de vraisemblance du paramètre $\theta$ est
$$
\hat{\theta}_{n,p}^{\text{MV}}=(\bar{X}_n,\bar{Y}_p,V_n,W_p).
$$

<p class="mybox">
  2\. Déterminer un test de niveau $\alpha$ de l'hypothèse
  $$
  H_0 : \sigma_0^2=\sigma_1^2,\quad\text{contre}\quad H_1 : \sigma_0^2>\sigma_1^2.
  $$
</p>

Rappelons que sous $\mathbb{P}_{\theta}$, $nV_n/\sigma_0^2=\frac{1}{\sigma_0^2}\sum_{i=1}^{n}(X_i-\bar{X}_n)^2\sim \chi^2(n-1)$ et $pW_p/\sigma_1^2=\frac{1}{\sigma_1^2}\sum_{j=1}^{p}(Y_j-\bar{Y}_p)^2\sim \chi^2(p-1)$. Alors, pour tout $\theta\in \Theta\triangleq\mathbb{R}^2\times (\mathbb{R}_+^*)^2$, on a sous $\mathbb{P}_{\theta}$
$$
\frac{nV_n/\sigma_0^2}{pW_p/\sigma_1^2}\sim F(n-1,p-1),
$$
ce qui ne dépend pas du paramètre $\theta$. Par conséquent, sous $H_0$ (qui suppose que $\sigma_0^2=\sigma_1^2$) on a
$$
\mathbb{P}_{\theta}\left(\frac{nV_n}{pW_p}\le q_{1-\alpha}^{F(n-1,p-1)}\right)=1-\alpha.
$$
Ainsi, $\phi(Z):=\mathbb{1}\left\{\dfrac{nV_n}{pW_p}\ge q_{1-\alpha}^{F(n-1,p-1)}\right\}$ est un test de taille (et donc de niveau) $\alpha$.

<p class="mybox">
  3\. Calculer la $p$-valeur du test.
</p>

Dans notre cas, la statistique de test est $T(Z):=\frac{nV_n}{pW_p}$ et la valeur critique du test est $c_{\alpha}:=q_{1-\alpha}^{F(n-1,p-1)}$, qui est décroissante par rapport à $\alpha\in [0,1]$. Ainsi, la $p$-valeur du test est
$$
\begin{align*}
  \hat{\alpha}(Z)
  &=\inf\{\alpha\in ]0,1[ \,:\, T(Z)\ge c_{\alpha}\}\\
  &=1-\Phi\left(\frac{nV_n}{pW_p}\right),
\end{align*}
$$
où $\Phi$ désigne la fonction de répartition de la loi de Fisher de $(n-1,p-1)$ degrés de liberté.

Nous considérons dans la suite le modèle statistique
$$
\left(\mathbb{R}^{n+p},\mathcal{B}(\mathbb{R}^{n+p}),\left\{\mathbb{P}_{\theta}=p_{\theta}\cdot\mathrm{d}\text{Leb}^{\otimes (n+p)}=(\mathcal{N}(\mu_0,\sigma^2))^{\otimes n}\otimes (\mathcal{N}(\mu_1,\sigma^2))^{\otimes p} \,\Big|\, \theta = (\mu_0,\mu_1,\sigma^2)\in \mathbb{R}^2\times \mathbb{R}_+^*\right\}\right).
$$

<p class="mybox">
  4\. Construire un intervalle de confiance de $\mu_0-\mu_1$ de niveau de confiance $1-\alpha$.
</p>

Sous $\mathbb{P}_{\theta}$, les deux variables aléatoires réelles $\bar{X}_n\sim \mathcal{N}(\mu_0,\sigma^2/n)$ et $\bar{Y}_p\sim \mathcal{N}(\mu_1,\sigma^2/p)$ sont indépendentes, et donc
$$
\frac{(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)}{\sqrt{\sigma^2/n+\sigma^2/p}}\sim \mathcal{N}(0,1).
$$
D'autre part, on sait que sous $\mathbb{P}_{\theta}$,
$$
\frac{1}{\sigma^2}(nV_n+pW_p)\sim \chi^2(n+p-2).
$$
On rappelle aussi que $\bar{X}_n,V_n$ sont indépendantes sous $\mathbb{P}_{\theta}$, et que $\bar{Y}_p,W_p$ le sont aussi. En plus, comme 
$X_1,\cdots,X_n$ et $Y_1,\cdots,Y_p$ sont indépendantes entre elles sous $\mathbb{P}_{\theta}$, on voit que $\bar{X}_n,W_p$ sont indépendantes sous $\mathbb{P}_{\theta}$, et que $\bar{Y}_p,V_n$ le sont aussi. Donc, les deux variables aléatoires réelles nouvellement construites, $\frac{(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)}{\sqrt{\sigma^2/n+\sigma^2/p}}$ et $\frac{1}{\sigma^2}(nV_n+pW_p)$, sont indépendantes sous $\mathbb{P}_{\theta}$. Cela permet de conclure que sous $\mathbb{P}_{\theta}$,
$$
\frac{[(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)]^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\sim F(1,n+p-2).
$$
Alors, pour tout $\theta\in \Theta$,
$$
\mathbb{P}_{\theta}\left(\frac{[(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)]^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\le q_{1-\alpha}^{F(1,n+p-2)}\right)=1-\alpha.
$$
On en tire donc une intervalle de confiance de niveau de confiance $1-\alpha$ pour $\mu_0-\mu_1$ :
$$
\textstyle
\left[(\bar{X}_n-\bar{Y}_p)\pm \sqrt{nV_n+pW_p}\sqrt{(\frac{1}{n}+\frac{1}{p})q_{1-\alpha}^{F(1,n+p-2)}}\right]
$$

<p class="mybox">
  5\. En déduire un test de niveau $\alpha$ de l'hypothèse
  $$
  H_0 : \mu_0=\mu_1,\quad\text{contre}\quad H_1 : \mu_0\neq \mu_1.
  $$
</p>

D'après la question précédente, le test défini par
$$
\phi(Z):=\mathbb{1}\left\{\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\ge q_{1-\alpha}^{F(1,n+p-2)}\right\}
$$
est un test de taille (et donc de niveau) $\alpha$.

<p class="mybox">
  6\. Calculer la $p$-valeur du test.
</p>

Dans notre cas, la statistique de test est $T(Z):=\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}$, et la valeur critique du test est $c_{\alpha}:=q_{1-\alpha}^{F(1,n+p-2)}$, qui est décroissante par rapport à $\alpha\in [0,1]$.
Ainsi, la $p$-valeur du test est
$$
\begin{align*}
  \hat{\alpha}(Z)
  &=\inf\{\alpha\in ]0,1[ \,:\, T(Z)\ge c_{\alpha}\}\\
  &=1-\Psi\left(\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\right),
\end{align*}
$$
où $\Psi$ désigne la fonction de répartition de la loi de Fisher de $(1,n+p-2)$ degrés de liberté.

<p class="mybox"> 
  7\. Construire un test de niveau $\alpha$ de l'hypothèse
  $$
  H_0 : \mu_0\le \mu_1,\quad\text{contre}\quad H_1 : \mu_0>\mu_1.
  $$
</p>

On considère l'estimateur de la différence $\mu_0-\mu_1$ donné par $T(Z):=\frac{\bar{X}_n-\bar{Y}_p}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}$.
On observe que sous $H_0$,
$$
\begin{align*}
\mathbb{P}_{\theta}\left(T(Z)\ge \sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right)
&\le \mathbb{P}_{\theta}\left(T(Z)-\frac{\mu_0-\mu_1}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}\ge \sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right)\\
&\le \mathbb{P}_{\theta}\left(\frac{[(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)]^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\ge q_{1-\alpha}^{F(1,n+p-2)}\right)\\
&= \alpha.
\end{align*}
$$
Ainsi, le test
$$
\phi(Z):=\mathbb{1}\left\{\frac{\bar{X}_n-\bar{Y}_p}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}\ge \sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right\}
$$
est un test de niveau $\alpha$ de l'hypothèse $H_0:\mu_0\le \mu_1$ contre $H_1:\mu_0>\mu_1$.

<p class="mybox">
   8\. Calculer la $p$-valeur du test.
</p>

Dans notre cas, la statistique de test est $T(Z):=\frac{\bar{X}_n-\bar{Y}_p}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}$ et la valeur critique du test est $c_{\alpha}:=\sqrt{q_{1-\alpha}^{F(1,n+p-2)}}$, qui est décroissante par rapport à $\alpha\in [0,1]$. Ainsi, la $p$-valeur du test est
$$
\begin{align*}
  \hat{\alpha}(Z)
  &=\inf\{\alpha\in ]0,1[ \,:\, T(Z)\ge c_{\alpha}\}\\
  &=
  \begin{cases}
    1-\Psi\left(\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\right), & \text{si $\bar{X}_n>\bar{Y}_p$;}\\
    +\infty, & \text{sinon,}
  \end{cases}
\end{align*}
$$
où $\Psi$ désigne la fonction de répartition de la loi de Fisher de $(1,n+p-2)$ degrés de liberté.

<!-- ## Exercice 2 : Le test du rapport de vraisemblance généralisé

Coming soon...

## Exercice 3 : Un cas où il n'existe pas de test uniformément plus puissant & Test uniformément plus puissant *parmi les tests sans biais*

Coming soon... -->
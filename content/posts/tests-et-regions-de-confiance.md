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
  p.context
  {
    border-left-width:3px;
    border-left-style:solid;
    border-right-style:none;
    border-top-style:none;
    border-bottom-style:none;
    border-radius:3px;
    border-color:#00FF00;
    padding-left:7px;
    padding-right:3px;
  }
</style>

<style>
  p.exo
  {
    border-left-width:3px;
    border-left-style:solid;
    border-right-style:none;
    border-top-style:none;
    border-bottom-style:none;
    border-radius:3px;
    border-color:#228B22;
    padding-left:7px;
    padding-right:3px;
  }
</style>

<style>
  details
  {
    border: 1px solid #aaa;
    border-radius: 3px;
    padding: 0.5em 0.5em 0;
  }
  summary
  {
    font-weight: bold;
    margin: -0.5em -0.5em 0;
    padding: 0.5em;
  }
  details[open]
  {
    padding: 0.5em;
  }
  details[open] summary
  {
    border-bottom: 1px solid #aaa;
    margin-bottom: 0.5em;
  }
</style>

# Exercices

## Test de comparaison de deux variances & Test de comparaison de deux moyennes (03/10/2023)

<p class="context">
  Considérons le modèle statistique
  $$
  \left(\mathbb{R}^{n+p},\mathcal{B}(\mathbb{R}^{n+p}),\left\{\mathbb{P}_{\theta}=p_{\theta}\cdot\mathrm{d}\text{Leb}^{\otimes (n+p)}=(\mathcal{N}(\mu_0,\sigma_0^2))^{\otimes n}\otimes (\mathcal{N}(\mu_1,\sigma_1^2))^{\otimes p} \,\Big|\, \theta = (\mu_0,\mu_1,\sigma_0^2,\sigma_1^2)\in \Theta=\mathbb{R}^2\times (\mathbb{R}_+^*)^2\right\}\right).
  $$
  Nous noterons $X_1,\cdots,X_n$ les observations du *groupe "0"*, est $Y_1,\cdots,Y_p$ les observations du *groupe "1"*.
</p>

<p class="exo">
  1\. Déterminer l'estimateur du maximum de vraisemblance du paramètre $\theta=(\mu_0,\mu_1,\sigma_0^2,\sigma_1^2)$.
</p>

<details open>
  <summary>Solution</summary>
  <p>
    Remarquons le fait que
    $$
    L(\theta;X_1,\cdots,X_n,Y_1,\cdots,Y_p)=L(\theta_0;X_1,\cdots,X_n)\cdot L(\theta_1;Y_1,\cdots,Y_p),
    $$
    où $\theta_0:=(\mu_0,\sigma_0^2)$ et $\theta_1:=(\mu_1,\sigma_1^2)$. Comme l'EMV du paramètre $\theta_0$ est $\left(\bar{X}_n,V_n\right)$, où
    $$
    \bar{X}_n:=\frac{1}{n}\sum_{i=1}^{n}X_i,\quad V_n:=\frac{1}{n}\sum_{i=1}^{n}(X_i-\bar{X}_n)^2,
    $$
    et que l'EMV du paramètre $\theta_1$ est $(\bar{Y}_p,W_p)$, où
    $$
    \bar{Y}_p:=\frac{1}{p}\sum_{j=1}^{n}Y_j,\quad W_p:=\frac{1}{p}\sum_{j=1}^{p}(Y_j-\bar{Y}_p)^2,
    $$
    on en déduit que l'EMV du paramètre $\theta$ est $(\bar{X}_n,\bar{Y}_p,V_n,W_p)$.
  </p>
</details>

<p class="exo">
  2\. Déterminer un test de niveau $\alpha$ de l'hypothèse
  $$
  H_0 : \sigma_0^2=\sigma_1^2,\quad\text{contre}\quad H_1 : \sigma_0^2>\sigma_1^2.
  $$
</p>

<details open>
  <summary>Solution</summary>
  <p>
    Pour tout $\theta\in \Theta$, sous $\mathbb{P}_{\theta}$, $nV_n/\sigma_0^2\sim \chi^2(n-1)$ et $pW_p/\sigma_1^2\sim \chi^2(p-1)$, d'où
    $$
    \frac{nV_n/\sigma_0^2}{pW_p/\sigma_1^2}\sim F(n-1,p-1),
    $$
    ce qui ne dépend pas du paramètre $\theta$. Par conséquent, sous $H_0$,
    $$
    \mathbb{P}_{\theta}\left(\frac{nV_n}{pW_p}\le q_{1-\alpha}^{F(n-1,p-1)}\right)=1-\alpha.
    $$
    Ainsi, $\phi(Z):=\mathbb{1}\left\{\dfrac{nV_n}{pW_p}\ge q_{1-\alpha}^{F(n-1,p-1)}\right\}$ est un test de taille (et donc de niveau) $\alpha$.
  </p>
</details>

<p class="exo">
  3\. Calculer la $p$-valeur du test. 
</p>

<details open>
  <summary>Solution</summary>
  <p>
    Dans notre cas, la statistique de test est $T(Z):=\frac{nV_n}{pW_p}$ et la valeur critique du test est $c_{\alpha}:=q_{1-\alpha}^{F(n-1,p-1)}$, qui est décroissante par rapport à $\alpha\in [0,1]$. Ainsi, la $p$-valeur du test est
    $$
    \hat{\alpha}(Z)=\inf\{\alpha\in [0,1] \,:\, T(Z)\ge c_{\alpha}\}=1-\Psi\left(\frac{nV_n}{pW_p}\right),
    $$
    où $\Psi$ désigne la fonction de répartition de la loi de Fisher de $(n-1,p-1)$ degrés de liberté.
  </p>
</details>

<p class="context">
  Nous considérons dans la suite le modèle statistique
  $$
  \left(\mathbb{R}^{n+p},\mathcal{B}(\mathbb{R}^{n+p}),\left\{\mathbb{P}_{\theta}=p_{\theta}\cdot\mathrm{d}\text{Leb}^{\otimes (n+p)}=(\mathcal{N}(\mu_0,\sigma^2))^{\otimes n}\otimes (\mathcal{N}(\mu_1,\sigma^2))^{\otimes p} \,\Big|\, \theta = (\mu_0,\mu_1,\sigma^2)\in \mathbb{R}^2\times \mathbb{R}_+^*\right\}\right).
  $$
</p>

<p class="exo">
  4\. Construire un intervalle de confiance de $\mu_0-\mu_1$ de niveau de confiance $1-\alpha$.
</p>

<details open>
  <summary>Solution</summary>
  <p>
    Soit $\theta\in \Theta$ et travaillons sous $\mathbb{P}_{\theta}$. D'une part, $\bar{X}_n\sim \mathcal{N}(\mu_0,\sigma^2/n)$, $\bar{Y}_p\sim \mathcal{N}(\mu_1,\sigma^2/p)$, et elles sont indépendentes, d'où
    $$
    \frac{(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)}{\sigma \sqrt{1/n+1/p}}\sim \mathcal{N}(0,1).
    $$
    D'autre part, en appliquant le théorème de Gosset, on voit que
    $$
    \frac{1}{\sigma^2}(nV_n+pW_p)\sim \chi^2(n+p-2),
    $$
    et que $\bar{X}_n$ et $V_n$, ainsi que $\bar{Y}_p$ et $W_p$, sont indépendantes. De plus, $\bar{X}_n$ et $W_p$, ainsi que $\bar{Y}_p$ et $V_n$, sont évidemment indépendantes. On conclut que $\frac{(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)}{\sigma \sqrt{1/n+1/p}}$ et $\frac{1}{\sigma^2}(nV_n+pW_p)$ sont indépendantes et donc que
    $$
    \frac{[(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)]^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\sim F(1,n+p-2).
    $$
    Alors, pour tout $\theta\in \Theta$,
    $$
    \mathbb{P}_{\theta}\left(\frac{[(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)]^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\le q_{1-\alpha}^{F(1,n+p-2)}\right)=1-\alpha.
    $$
    On en tire donc une intervalle de confiance de niveau de confiance $1-\alpha$ $(0<\alpha<1)$ pour $\mu_0-\mu_1$ :
    $$
    \textstyle
    \left[(\bar{X}_n-\bar{Y}_p)\pm \sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right].
    $$
  </p>
</details>

<p class="exo">
  5\. En déduire un test de niveau $\alpha$ de l'hypothèse
  $$
  H_0 : \mu_0=\mu_1,\quad\text{contre}\quad H_1 : \mu_0\neq \mu_1.
  $$
</p>

<details open>
  <summary>Solution</summary>
  <p>
    D'après la question précédente, le test
    $$
    \phi(Z):=\mathbb{1}\left\{\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\ge q_{1-\alpha}^{F(1,n+p-2)}\right\}
    $$
    est un test de taille (et donc de niveau) $\alpha$ de l'hypothèse $H_0:\mu_0=\mu_1$ contre $H_1:\mu_0\neq \mu_1$.
  </p>
</details>

<p class="exo">
  6\. Calculer la $p$-valeur du test.
</p>

<details open>
  <summary>Solution</summary>
  <p>
    Dans notre cas, la statistique de test est $T(Z):=\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}$, et la valeur critique du test est $c_{\alpha}:=q_{1-\alpha}^{F(1,n+p-2)}$, qui est décroissante par rapport à $\alpha\in [0,1]$.
    Ainsi, la $p$-valeur du test est
    $$
    \hat{\alpha}(Z)=\inf\{\alpha\in [0,1] \,:\, T(Z)\ge c_{\alpha}\}=1-\Psi\left(\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\right),
    $$
    où $\Psi$ désigne la fonction de répartition de la loi de Fisher de $(1,n+p-2)$ degrés de liberté.
  </p>
</details>

<p class="exo"> 
  7\. Construire un test de niveau $\alpha$ de l'hypothèse
  $$
  H_0 : \mu_0\le \mu_1,\quad\text{contre}\quad H_1 : \mu_0>\mu_1.
  $$
</p>

<details open>
  <summary>Solution</summary>
  <p>
    On considère l'estimateur de la différence $\mu_0-\mu_1$ donné par $T(Z):=\frac{\bar{X}_n-\bar{Y}_p}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}$.
    On observe que sous $H_0$,
    $$
    \begin{align*}
    \mathbb{P}_{\theta}\left(T(Z)\ge \sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right)
    &\le \mathbb{P}_{\theta}\left(T(Z)-\frac{\mu_0-\mu_1}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}\ge \sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right)\\
    &\le \mathbb{P}_{\theta}\left(\frac{[(\bar{X}_n-\bar{Y}_p)-(\mu_0-\mu_1)]^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\ge q_{1-\alpha}^{F(1,n+p-2)}\right)= \alpha.
    \end{align*}
    $$
    Ainsi, le test \[^[On pourrait ignorer le cas où $\alpha=1$.]\]
    $$
    \phi(Z):=\mathbb{1}\left\{\frac{\bar{X}_n-\bar{Y}_p}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}\ge \sqrt{q_{1-\alpha}^{F(1,n+p-2)}}\right\}
    $$
    est un test de niveau $\alpha$ de l'hypothèse $H_0:\mu_0\le \mu_1$ contre $H_1:\mu_0>\mu_1$.
  </p>
</details>

<p class="exo">
   8\. Calculer la $p$-valeur du test.
</p>

<details open>
  <summary>Solution</summary>
  <p>
    Dans notre cas, la statistique de test est $T(Z):=\frac{\bar{X}_n-\bar{Y}_p}{\sqrt{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}}$ et la valeur critique du test est $c_{\alpha}:=\sqrt{q_{1-\alpha}^{F(1,n+p-2)}}$ \[^[On pourrait convenir que $c_1=-\infty$.]\], qui est décroissante par rapport à $\alpha\in [0,1]$. Ainsi, la $p$-valeur du test est
    $$
    \begin{align*}
      \hat{\alpha}(Z)
      &=\inf\{\alpha\in [0,1] \,:\, T(Z)\ge c_{\alpha}\}\\
      &=
      \begin{cases}
        1-\Psi\left(\frac{(\bar{X}_n-\bar{Y}_p)^2}{(\frac{1}{n}+\frac{1}{p})(nV_n+pW_p)}\right), & \text{si $\bar{X}_n>\bar{Y}_p$;}\\
        1, & \text{sinon,}
      \end{cases}
    \end{align*}
    $$
    où $\Psi$ désigne la fonction de répartition de la loi de Fisher de $(1,n+p-2)$ degrés de liberté.
  </p>
</details>

<!-- ## Exercice 2 : Le test du rapport de vraisemblance généralisé

Coming soon...

## Exercice 3 : Un cas où il n'existe pas de test uniformément plus puissant & Test uniformément plus puissant *parmi les tests sans biais*

Coming soon... -->
---
title: Hoeffding 不等式
date: 2023-08-30T01:43:25.643Z
draft: true
description: null
slug: hoeffding
categories:
  - 概率统计
tags:
  - 统计学习
markup: pandoc
---

Soient $X_1,\cdots,X_n$ des variables aléatoire réelle indépendantes telles que, pour tout $i\in \{1,\cdots,n\}$, $\mathbb{E}[X_i]=0$ et $a_i\le X_i\le b_i$. Alors pour tout $t>0$, on a
$\mathbb{P}(\bar{X}_n\ge t)\le e^{-2n^2t^2/\sum_{i=1}^{n}(b_i-a_i)^2},\mathbb{P}(\bar{X}_n\le -t)\le e^{-2n^2t^2/\sum_{i=1}^{n}(b_i-a_i)^2}.$

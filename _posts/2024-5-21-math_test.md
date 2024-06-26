---
layout: post
title: "latex 公式测试"
date:   2024-5-21
tags: [latex, mathjax]
comments: true
author: luowei
toc: true
---

测试latex公式的显示效果。
<!-- more -->

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# 1.拉格朗日插值多项式

拉格朗日插值多项式是一种用于通过已知数据点来构造多项式的插值方法。具体来说，对于给定的 $n+1$ 个数据点 $(x_0, y_0), (x_1, y_1), \ldots, (x_n, y_n)$，我们可以构造一个 $n$ 次多项式 $P(x)$，使得这个多项式在这些点上的函数值与给定的函数值相同，即 $P(x_k) = y_k$。

## 插值基函数

插值基函数 $L_i(x)$ 是这样构造的：

$$
L_k(x) = \prod\limits_{j=0 \atop j \neq k}^n \frac{x - x_j}{x_k - x_j} \quad  (k = 0, 1, \ldots, n)
$$

这里， $\prod$ 表示连乘。插值基函数 $L_k(x)$ 满足在 $x_k$ 处等于 1，而在其他 $x_j$ 处等于 0（$j \neq k$）。因此， $L_k(x)$ 确保了每个插值点的独立性。

## 拉格朗日插值多项式

拉格朗日插值多项式 $P(x)$ 是这些插值基函数 $L_k(x)$ 的线性组合：

$$
P(x) = \sum_{k=0}^{n} y_k L_k(x)=\sum_{k=0}^{n} \left[ y_k \prod\limits_{j=0 \atop j \neq k}^n \frac{x - x_j}{x_k - x_j} \right]
$$

这意味着 $P(x)$ 可以通过已知数据点的函数值 $y_k$ 和插值基函数 $L_k(x)$ 的组合来表示。具体来说，每个 $y_k$ 与对应的 $L_k(x)$ 相乘，并将所有这些乘积相加，即可得到插值多项式。

这样构造的 $P(x)$ 满足在每个已知数据点 $x_k$ 处的函数值正好等于 $y_k$，即 $P(x_k) = y_k$。

## 截断误差/插值余项

设$f(x)$在$[a,b]$有n+1阶导数，$ x0, x1,\ldots, x_n $为$[a, b]$上$n+1$个互异的节点, $p(x)$为满足$p(x_i) = f(x_i) (i=1,2,\ldots, n)$的$n$次多项式,那么对于任何$x\in [a,b]$有插值余项:

$$
R(x)=f(x)-p(x)=\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)\cdots(x-x_n)
$$

$$
若
\max \limits_{a\leq x \leq b}\left|f^{(n+1)}(x)\right| = M_{n+1}
则 
\left| R_n(x) \right| \leq \frac{M_{n+1}}{(n+1)!}|(x-x_0)\cdots(x-x_n)|
$$

对于线性插值多项式$p(x)$,其插值余项为：

$$
R_n(x) = \frac{1}{2}f''(\xi)(x-x_0)(x-x_1) \quad \xi \in [a,b] \tag{1}
$$

$$
R_n(x) \leq \frac{1}{8}(b-a)^2M_2 \tag{2}
$$




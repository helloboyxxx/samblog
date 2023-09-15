---
title: "413_Pigeonhole_Principle"
date: 2023-09-15T17:28:11-05:00
draft: false
math: true
tags: ["Combinatorics"]
---


If $n+1$ objects are distributed into $n$ boxes, then at least one box contains two or more of the objects. 

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

For each $i\in \set{1, ..., n}$, let $a_i = $  number of objects in box $i$. Then, $a_1 + ... + a_n = n+1$ Let $a_j = \text{max } a_i$. Then, 
`
\begin{align*}
n+1 &\leq n\cdot a_j \\
\frac{n+1}{n} &\leq a_j \\
1 < \frac{n+1}{n} &\leq a_j\\
1 &< a_j
\end{align*}
`
Note that this conclusion doesn't hole if you have $n$ objects or less.



<span style="color:#04c2b2">$\boldsymbol{\sf Exercise}$</span> There are 5 points in a square of side length 2. Prove that at least two of them are with the distance at most $\sqrt{2}$.

Equally divide this square into four smaller squares with side length 1. By the pigeonhole principle, $\exists$ one $1 \times 1$ square with $ \geq$ 2 points. 



### <span style="color:#3c66b5">$\boldsymbol{\textsf{Theorem}}$</span>

A grid of 27 points (forming a $3 \times 9$ square) in the plane is given.Each point is coloured red or blue. Prove taht there exists a monochromatic rectangle, that is, a rectangle with all four vertices of the same color. 

<center>
<img src="https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/points.png" alt="points" style="zoom:50%;"/>
</center>

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Consider the the pattern of coloring of a single column. Each colum has 3 points. 
Then, there are $2^3  = 8$ ways of coloring this column. As there are 9 columns in this square, by pigeonhole principle, there are at least two columns in the same pattern. Again, by the pigeonhole principle, each column must have at least two red or two blue. 



### More abstract formulations of the pigeonhole principle



Let $X$ and $Y$ be finite sets and let $f: X \to Y$ be a function from $X$ to $Y$. 

<span style="color:#599eff">$\boldsymbol{\sf Proposition}$</span> If $X$ has more elements than $Y$, then $f$ is not injective. 

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Let $X = \set{x_1, ..., x_n}$, $Y = \set{y_1, ..., y_m}$

Define $A_i = \set{x_j : f(x_j) = y_i}, \forall i \in \set{1, ..., m}$.

Then we have: $n = |X| = |A_1| + ... + |A_m|$

Suppose for contradiction that $f$ is injective

$\implies |A_i| \leq 1 \implies |X| = |A_1| + ... + |A_m| \leq m \implies n \leq m$. Contradiction

<span style="color:#599eff">$\boldsymbol{\sf Proposition}$</span> If $X$ and $Y$ have the same number of elements and $f$ is surjective, then $f$ is injective. 

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span> $n = |X| = |A_1| + ... + |A_m| \geq m$ by the definition of surjective. And since $m=n$, $|A_1| + ... + |A_m| = m \implies |A_i| = 1$

<span style="color:#599eff">$\boldsymbol{\sf Proposition}$</span> If $X$ and $Y$ have the same number of elements and $f$ is injective, then $f$ is surjective. 



### <span style="color:#3c66b5">$\boldsymbol{\textsf{Theorem}}$</span>

Let $m$ be any positive integer and let $a_1, ..., a_m$ be a sequence be any sequance of $m$ integers. Then, there exsist consecutive $a$'s in the sequence whose sum is divisible by $m$. 

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Pigeons:

`
\begin{matrix}
a_1\\
a_1 + a_2\\
\vdots\\
a_1 + a_2 + ... + a_m
\end{matrix}
`

Pigeonholes:

$$
A_r = \set{n \in \mathbb{Z} : n = qm + r, q \in \mathbb{Z}}, \text{where } r \in \set{1, ..., m}
$$



Notice that we select $r$ from $1$ to $m$. This is because: 

Whenever we have some $k \in \set{1, .., m}$ such that $a_1 + ... + a_k = qm = qm + 0$, we have done finding our goal sequence.

Otherwise, putting $m$ pigeons into $m-1$ pigeonholes gives us a fact that $\exists i, j \in \set{1, ..., m}, i \neq j$ such that $(a_1 + ... + a_i) \equiv (a_1 + ... a_j) \text{ mod }m $. WLOG, suppose $i < j$, we have $m \mid (a_{i+1} + ... + a_j)$, giving us what we want.



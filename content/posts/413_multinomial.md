---
title: "413_Multinomial Coefficient"
date: 2023-10-30T10:30:51-05:00
draft: false
math: true
tags: ["Combinatorics"]
---

<span style="color:#28a745">Definition</span> A multinomial coefficient is:

$$
\binom{n}{n_1 n_2 \cdots n_t}
=\frac{n !}{n_{1} ! n_{2} ! \cdots n_{t} !}
$$

Here, $n_1, n_2, \ldots, n_t$ are nonnegative integers with
$$
n_1+n_2+\cdots+n_t=n
$$


### <span style="color:#3c66b5">Pascal's theorem for multinomial coefficients</span>

Pascal's theorem for
Let $n, k \in \mathbb{N}$ and $(n)_{i=1}^k$ be natural numbers so that
$$
n_1+\cdots+n_k=n
$$
Then,

$$
\binom{n}{n_1, n_2, \ldots, n_k} = 
\binom{n-1}{n_1-1, n_2, \ldots, n_k} + \ldots + 
\binom{n-1}{n_1, n_2, \ldots, n_k-1}
$$



<span style="color:#eb861c">Proof</span>

Combinatorial argument: 
$$
\text { Let } S=\{\underbrace{1, \ldots, 1}_{n_1}, \underbrace{2, \ldots, 2}_{n_2}, \ldots, \underbrace{k, \ldots, k}_{n_k}\}
$$
Count $N = $# of permutations of $S$.

For each $i \in [k]$, define $N_i = $ # of permutations of $S$ where the first element is equal to $i$. 

Then, $N = N_1 + N_2 + \ldots + N_k$. Where:
$$
N_i = \frac{(n-1)!}{n_1!n_2! \cdots n_{i-1}!(n_i-1)!n_{i+1}\cdots n_k!}
$$
Which is equal to the right side. Left side is trivial. Done.



### <span style="color:#3c66b5">The multinomial theorem</span>

Let $n$ be a positive integer. For all $x_1,\ldots,x_t$, we have

$$
(x_1+\cdots+x_t)^n = \sum \binom{n}{n_1,\, n_2, \ldots, \, n_k} x_1^{n_1}x_2^{n_2}\cdots x_t^{n_t}
$$

where the summation extends over all nonnegative integral solutions $n_1,\ldots,n_t$ of $n_1 + \cdots + n_t = n$.

<span style="color:#eb861c">Proof</span>

Define $S = \{n\cdot x_1, n\cdot x_2 \cdots n\cdot x_k\}$ ($n$ copies of $x_i$)

Define $\mathcal{P} = $ the collection of all $n$-permutaions of the multiset $S$. 
$$
(x_1 + \ldots + x_k)^n = \sum_{a_1a_2\ldots a_n \in \mathcal{P}} a_1 \cdot a_2 \cdots a_n
$$
Imagine that you just expand this huge multiplication on the left side, then choose one $x_i$ from each parenthesis.

> Question: What is the number of $n$-permutation of $S$ with $n_1$ $x_1$'s, $n_2$ $x_2$'s, ... $n_k$ $x_k$'s, where $n_1 + n_2 + \ldots + n_k = n$.

Answer: $\binom{n}{n_1, n_2, \ldots, n_k}$

Then we have: 
$$
(x_1 + \ldots + x_k)^n = \sum_{a_1a_2\ldots a_n \in \mathcal{P}} a_1 \cdot a_2 \cdots a_n = \text{right side of the theorem}
$$






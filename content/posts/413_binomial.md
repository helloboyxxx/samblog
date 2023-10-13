---
title: "413_binomial"
date: 2023-09-12T17:35:33-05:00
draft: false
math: true
tags: ["Combinatorics"]
---

# Binomial Coefficient and Binomial Identity

### <span style="color:#3c66b5">Pascal's Triangle</span>

`
\begin{matrix}
{0 \choose 0}\\
{1 \choose 0} & {1 \choose 1}\\
{2 \choose 0} & {2 \choose 1} & {2 \choose 2}\\
{3 \choose 0} & {3 \choose 1} & {3 \choose 2} & {3 \choose 3}\\
{4 \choose 0} & {4 \choose 1} & {4 \choose 2} & {4 \choose 3} & {4 \choose 4}\\
.\\
.\\
.
\end{matrix}
`

### <span style="color:#3c66b5">Pascal's Formula</span>

For all integers $n$ and $k$ with $1 \leq k \leq n - 1$, we have: 
$$
{n \choose k} = {{n-1} \choose k} + {{n-1} \choose {k-1}}
$$

<span style="color:#eb861c">Proof</span>

Let $S = \set{1, 2, ..., n}$ be a set of size n.

We'll count in two ways of the size of the following set:

$\mathcal{C} = \set{A : A \subseteq S, |A| = k}$

(1) $|\mathcal{C}| = {n \choose k}$

(2) Define: 
`
\begin{align*}
\mathcal{C_1} = \set{A : A \subseteq S, |A| = k, 1 \in A}\\
\mathcal{C_2} = \set{A : A \subseteq S, |A| = k, 1 \not\in A}
\end{align*}
`
Note that: $\mathcal{C_1}$ and $\mathcal{C_2}$ are disjoint, $\mathcal{C} = \mathcal{C_1} \cup \mathcal{C_2}$

Since $|\mathcal{C_1}| = {{n-1} \choose {k-1}}$, $|\mathcal{C_2}| = {{n-1} \choose {k}}$, we get the identity.



### <span style="color:#3c66b5">Theorem</span>

For $n \geq 0$, we have: 
$$
{n \choose 0} + {n \choose 1} + {n \choose 2} + ...+{n \choose n} = 2^n
$$
This is a row in the Pascal's triangle. 

<span style="color:#eb861c">Proof</span>

Let $\mathcal{C}$ = $n$-digit binary numbers. Two way to count this: 

(1) $|\mathcal{C}| = 2^n$

(2) Define: $\mathcal{C_i} = n$-digit binary numbers with exactly $i$ 1's.

Then simply $|\mathcal{C}| = \sum_{i=0}^{n}\mathcal{C_i}$   , as they are all disjoint. 



### <span style="color:#3c66b5">Theorem</span>

$$
{n \choose 0} + {n \choose 2} + ... = {n \choose 1} + {n \choose 3} + ...
$$

<span style="color:#eb861c">Proof</span>

Let $S = \set{1, ...,n}$

Define: 

$\mathcal{C_1} = $ subsets of $S$ with odd size

$\mathcal{C_2} = $ subsets of $S$ with even size

> Question: How to select an even subset?

First, select any subset $A \subseteq \set{1, ..., n - 1}$:

- If $|A|$ is even, then $A \in \mathcal{C_2}$, and $A \cup \set{set} \in \mathcal{C_1}$
- If $|A|$ is odd, then $A \in \mathcal{C_1}$, and $A \cup \set{n} \in \mathcal{C_2}$

As this constructs a bijection, $|\mathcal{C_1}| = |\mathcal{C_2}| = 2^{n-1}$



### <span style="color:#3c66b5">The Binomial Theorem</span>

Let $n$ be a positive integer. Then, for all $x$ and $y$ we have: 
$$
(x+y)^n = \sum_{k=0}^{n} {n \choose k} x^{n-k}y^k
$$
<span style="color:#eb861c">Proof</span>

As we have $n$ $(x+y)$ multiplication, we choose either an $x$ or a $y$ from each pair to multiply. This makes sure that we must have all terms in the form: $x^iy^{n-i}$. The remaining task is simply count the number of $x^iy^{n-i}$. Given this $i$, we have $n \choose i$ ways to choose the combination, thus we have the resulting formula.

<span style="color:#3c66b5">Corollary</span>

Let $n$ be a positive integer. Then, for all $x$ we have

$$
(1+x)^n = \sum \limits_{k=0}^{n} \binom{n}{k} x^k
$$

### <span style="color:#3c66b5">Theorem</span>

For $1 \leq k \leq n$, we have: 
$$
{n \choose k} = \frac{n}{k} {{n - 1} \choose {k-1}}
$$
<span style="color:#eb861c">Proof</span>

Goal: $k{n \choose k} = n{{n - 1} \choose {k-1}}$ 

Among $n$ people, we want to select $k$ people and we want to elect one of these $k$ people as the boss. 

(1) First select $k$ people, then select the boss: ${n \choose k} \cdot k$

(2) First select the boss, then choose subset of $n$ that contains this boss: $n \cdot {{n-1} \choose {k-1}}$



### <span style="color:#3c66b5">Theorem</span>

For $n\geq 1$ we have: 
$$
1{n \choose 1} + 2{n \choose 2} + ... + n{n \choose n} = n2^{n-1}
$$



<span style="color:#eb861c">Proof</span>

$n$ people, select a group of people with one boss. How many choices do we have?

(1)

- Select the size of the group: $i \in \set{1, ..., n}$
- Select a group with $i$ people: $n \choose i$
- Inside the group, assign someone to be the boss: $i$

This gives us the left side of the identity.

(2)

- Choose the boss: $n$
- Chose the rest of the group: A subset of remainning people: $2^{n-1}$

### <span style="color:#3c66b5">Theorem</span>

For $n \geq 0$ we have:
$$
\sum_{k=0}^{n}{n \choose k}^2 = {{2n}\choose n}
$$
Right side: The number of choices for selecting a group of $n$ people out of $2n$ people.

Labeling the people: $\set{1, ..., 2n}$. Splitting this $2n$ people into two $n$ people group. Given a specific $k$, we can select $k$ people from the first group, and then $n-k$ people from the second group. In that situation, we have ${n \choose k} \cdot {n \choose {n-k}}$. The final thing to do is simply take the sum of all the $k$'s. This gives us the left side of this identity.

### <span style="color:#3c66b5">The hockey-stick identity</span>

For $0 \leq k \leq n$ we have: 
$$
\sum_{m=k}^{n}{m \choose k} = {{n+1} \choose {k+1}}
$$
Intuition: Choose a column, and draw a box. Summing the values in the box gives the value at position $(n+1, k+1)$.

<span style="color:#eb861c">Proof</span>

$n+1$ people, select $k+1$: ${{n+1} \choose {k+1}}$

Order people by height, from smallest to tallest: $1, 2, ..., n+1$

- Select the tallest person in the group of size $m+1$, and then choose the rest $k$ people: ${{m} \choose {k}}$
- $m$ varies from $k$ to $n$
- Summing all the $m$ cases gives us the left side of this identity.












### Reference:

https://lmattos.web.illinois.edu/math-413-lecture-log/, MATH 413, Leticia Dias Mattos


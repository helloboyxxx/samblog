---
title: "413_binomial"
date: 2023-09-12T17:35:33-05:00
draft: false
math: true
tags: ["Math 413"]
---


# Binomial Coefficient and Binomial Identity

### Pascal's Triangle

$$
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
$$

### **Pascal's Formula**

For all integers $n$ and $k$ with $1 \leq k \leq n - 1$, we have: 
$$
{n \choose k} = {{n-1} \choose k} + {{n-1} \choose {k-1}}
$$

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Let $S = \{1, 2, ..., n\}$ be a set of size n.

We'll count in two ways of the size of the following set:

$\mathcal{C} = \{A : A \subseteq S, |A| = k\}$

(1) $|\mathcal{C}| = {n \choose k}$

(2) Define: 
$$
\mathcal{C_1} = \{A : A \subseteq S, |A| = k, 1 \in A\}\\
\mathcal{C_2} = \{A : A \subseteq S, |A| = k, 1 \not\in A\}
$$
Note that: $\mathcal{C_1}$ and $\mathcal{C_2}$ are disjoint, $\mathcal{C} = \mathcal{C_1} \cup \mathcal{C_2}$

Since $|\mathcal{C_1}| = {{n-1} \choose {k-1}}$, $|\mathcal{C_2}| = {{n-1} \choose {k}}$, we get the identity.



### <span style="color:#3c66b5">$\boldsymbol{\textsf{Theorem}}$</span>

For $n \geq 0$, we have: 
$$
{n \choose 0} + {n \choose 1} + {n \choose 2} + ...+{n \choose n} = 2^n
$$
This is a row in the Pascal's triangle. 

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Let $\mathcal{C}$ = $n$-digit binary numbers. Two way to count this: 

(1) $|\mathcal{C}| = 2^n$

(2) Define: $\mathcal{C_i} = n$-digit binary numbers with exactly $i$ 1's.

Then simply $|\mathcal{C}| = \sum_{i=0}^{n}\mathcal{C_i}$   , as they are all disjoint. 



### <span style="color:#3c66b5">$\boldsymbol{\textsf{Theorem}}$</span>

$$
{n \choose 0} + {n \choose 2} + ... = {n \choose 1} + {n \choose 3} + ...
$$

<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Let $S = \{1, ...,n\}$

Define: 

$\mathcal{C_1} = $ subsets of $S$ with odd size

$\mathcal{C_2} = $ subsets of $S$ with even size

Question: How to select an even subset?

First, select any subset $A \subseteq \{1, ..., n - 1\}$:

- If $|A|$ is even, then $A \in \mathcal{C_2}$, and $A \cup \{n\} \in \mathcal{C_1}$
- If $|A|$ is odd, then $A \in \mathcal{C_1}$, and $A \cup \{n\} \in \mathcal{C_2}$

As this constructs a bijection, $|\mathcal{C_1}| = |\mathcal{C_2}| = 2^{n-1}$



### <span style="color:#3c66b5">$\boldsymbol{\textsf{The Binomial Theorem}}$</span>

Let $n$ be a positive integer. Then, for all $x$ and $y$ we have: 
$$
(x+y)^n = \sum_{k=0}^{n} {n \choose k} x^{n-k}y^k
$$
<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

As we have $n$ $(x+y)$ multiplication, we choose either an $x$ or a $y$ from each pair to multiply. This makes sure that we must have all terms in the form: $x^iy^{n-i}$. The remaining task is simply count the number of $x^iy^{n-i}$. Given this $i$, we have $n \choose i$ ways to choose the combination, thus we have the resulting formula.

### <span style="color:#3c66b5">$\boldsymbol{\textsf{Corollary}}$</span>

Let $n$ be a positive integer. Then, for all $x$ we have

$$
(1+x)^n = \sum \limits_{k=0}^{n} \binom{n}{k} x^k
$$

### <span style="color:#3c66b5">$\boldsymbol{\textsf{Theorem}}$</span>

For $1 \leq k \leq n$, we have: 
$$
{n \choose k} = \frac{n}{k} {{n - 1} \choose {k-1}}
$$
<span style="color:#eb861c">$\boldsymbol{\sf Proof}$</span>

Goal: $k{n \choose k} = n{{n - 1} \choose {k-1}}$ 

Among $n$ people, we want to select $k$ people and we want to elect one of these $k$ people as the boss. 

(1) First select $k$ people, then select the boss: ${n \choose k} \cdot k$

(2) First select the boss, then choose subset of $n$ that contains this boss: $n \cdot {{n-1} \choose {k-1}}$

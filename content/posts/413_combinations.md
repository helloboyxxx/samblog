---
title: "413_combinations"
date: 2023-09-08T13:23:54-05:00
draft: false
math: true
tags: ["Combinatorics"]
---

A combination of a set $S$ is a term usually used to denote an unordered selection of the element of $S$. It is simply a selection of a subset of $S$.

- $r$-combination = $r$-subset. 
- $n\choose r$ is the number of $r$-subset in the set of size $n$. 

### Theorem

For $0 \leq r \leq n$, we have: 
$$
P(n, r) = r! {n \choose r} \text{ and } 
{n \choose r} = \frac{n!}{r!(n-r)!}
$$
**Pf:** 

Let $S$ be a set of size $n$. $S = \{s_1, ..., s_n\}$

First, let us choose a string of size $r$ formed by elements of $S$ ($r$-permutation):
$$
\mathcal{P}(n, r) = \{(s_{i1}, ..., s_{ir}): s_{ij} \in S, \text{all distinct}\}
$$
And define: 
$$
\mathcal{C}(n, r) = \text{set of subsets of }S \text{ with size }r
$$
Define the function: 
$$
f:\mathcal{P}(n, r) \to \mathcal{C}(n, r)\\
f(s_{i1}, ..., s_{ir}) = \{s_{i1}, ..., s_{ir}\}
$$
Consider: How many times a set is being counted? 

Ans: $r!$

Then we have: 
$$
|\mathcal{P}(n, r)| = r!|\mathcal{C}(n, r)|
$$


### Corollary

$$
{n \choose r} = {n \choose {n-r}}
$$



Problem: 

>  There is a $4 \times 6$ grid. Starting from bottom left and ending at top right. You can only choose up or right move. How many different paths can you take?

There is a bijection between these paths and the set of strings of size 10 of the form: $(a_1, a_2,..., a_{10})$, where each $a_i$ is $U$ or $R$.  ($URUURR...$). But since the number of $U$'s = 4, the number of distributing 4 $U$'s in a string of size 10 is $10 \choose 4$.



### Theorem

Let $S$ be a multiset with objects of $k$ different types, where each object has an infinite repetition number. Then, the number of $r$-permutations of $S$ is $k^r$.

**Pf:**

There are $r$ position to be filled in. Each position has $k$ choices since we have infinite number of each type in this multiset S. This gives us $k^r$

Another examle: $S = \{a, a, b\}$. If we want 3-permutation of S. In this case, $(a, a, a)$ is not a 3-permutation of S. 



### Theorem

Let the size of $S$ be $n = n_1 + ... + n_k$. Then the number of permutations of $S$ is equal to: 
$$
\frac{n!}{(n_1)!(n_2)!... (n_k)! }
$$
**Pf:**

Let $a_1^1, ..., a_{n_1}^1$ be a labelling of the elements of type 1.

Let $a_1^2, ..., a_{n_2}^2$ be a labelling of the elements of type 2.

Let $a_1^3, ..., a_{n_3}^3$ be a labelling of the elements of type 3.

...

Let $a_1^k, ..., a_{n_k}^k$ be a labelling of the elements of type 3.

Consider the set $S' = \{a_1^1, ..., a_{n_1}^1, ..., a_1^k, ..., a_{n_k}^k\}$

The permutations of $S' = n!$. Then we can create a function: 
$$
f:\{\text{permutations of }S'\} \to \{\text{permutation of }S\}\\
f(\text{string} = \text{string where the labels are removed})
$$
Removing the label makes all those elements in the same type indistinguishable. (You cannot tell the different between $a_1^1$ and $a_2^1$ if the lable is removed.)

Consider: For a given permutation $A$ of $S$, what's the number of the set $\{S: f(S) = A\}$? 

Ans: $(n_1)!(n_2)! ... (n_k)!$





##### Problem: 

How many ways do we have of partitioning the set $\{1, 2, ..., 10\}$ into 3 sets: out of size 2, out of size 3, and another of size 5?

**Solution 1:**
$$
{10 \choose 2} {8 \choose 3} {5 \choose 5} = 
{10 \choose 5} {5 \choose 3} {2 \choose 2}
$$
**Solution 2:**

Define the set: $\mathcal{P}(10) =$ set of all permutations of $\{1, ..., 10\}$. Then, $|\mathcal{P} = 10!|$

Define: $f: \mathcal{P} \to \{\text{Box configurations}\}$ by:
$$
f(a_1, ..., a_{10}) 
= \left( \{a_1, a_2\}, \{a_3, a_4, a_5\}, \{...\} \right)
$$
Question: Given a box configuration $\mathcal{B}$, what is the number $\{S:f(S) = \mathcal{B}\}$, where $S$ are strings. 
$$
|\mathcal{P}(10)| = |\text{Box configuration}| \cdot 2! \cdot 3! \cdot 5!
$$
This gives us: 
$$
|\text{Box configuration}| = \frac{|\mathcal{P}(10)|}{2! \cdot 3! \cdot 5!}
$$

### Theorem 2.4.3: 

Let $n$ be a positive integer and let $n_1, n_2, ... ,n_k$ be positive integers with $n = n_l + n_2 + ... + n_k$· The number of ways to partition a set of $n$ objects into k labeled boxes in which Box 1 contains $n_1$ objects, Box 2 contains $n_2$ objects, ... , Box $k$ contains $n_k$ objects equals:
$$
\frac{n!}{n_1! \cdot n_2! \cdot \cdot \cdot n_k!}
$$


### Theorem 2.5.1

Let $S$ be a multiset with objects of $k$ types, each with an infinite repetition number. Then, the number of $r$-**combinations** of $S$ equals to: 
$$
{{r + k - 1} \choose r}
$$
**Pf:**

Now: we need to select a submultiset. Each submultiset is associated to a solution of:
$$
X_1 + ... + X_k = r\\
X_1, ..., X_k \in \mathbb{N} \cup \{0\}
$$
Let $\mathcal{S}$ be the set of solutions.  

Define: $f: \mathcal{S} \to \{0, 1 \text{ bit strings with } k - 1 \text{ ones and }r \text{ zeros}\}$ by : 

$f(x_1, ..., x_k) = (00 ...0(X_1\text{ zeros})) 1 (00 ...0(X_2\text{ zeros})) 1 ... (00 ...0(X_k\text{ zeros}))$

Given $s \in f(\mathcal{S})$, the number of 1's in $s = k  - 1$, and the number of 0's in $s = r$.

Easy to check that this function $f$ is a bijection.

$\mathcal{R} =$ set of 0-1 strings with $k-1$ 1's and $r$ 0's. It suffices to show: $|\mathcal{R}| = |\mathcal{S}|$. $\blacksquare$



**Problem:**

A bakery boasts eight varieties of doughnuts. If a box of doughnuts contains one dozen, how many different options are there for a box of doughnuts?

We need to calculate the number of solutions for: $X_1 + ... + X_8 = 12$, which is: ${8 + 12 - 1} \choose 12$.



**Problem:**

What is the number of integral solutions of the equation $X_1 + X_2 + X_3 + X_4 = 20$, in which $X_1 \geq 3, X_2 \geq 1, X_3 \geq 0, X_4 \geq 5$?

Define:

$X_1 = Y_1 + 3$

$X_2 = Y_2 + 1$

$X_3 = Y_3$

$X_4 = Y_4 + 5$

This gives us: 
$Y_1 + Y_2 + Y_3 + Y_4 = 20 - (3 + 1 + 0 + 5) = 11$

The number of solutions with $Y_i \in \mathbb{N} \cup \{0\} = {14 \choose 3}$




Next class: 

### Pascal's Formula

For all integers $n$ and $k$ with $1 \leq k \leq n - 1$, we have: 
$$
{n \choose k} = {{n-1} \choose k} + {{n-1} \choose {k-1}}
$$



### Reference:

https://lmattos.web.illinois.edu/math-413-lecture-log/, MATH 413, Leticia Dias Mattos


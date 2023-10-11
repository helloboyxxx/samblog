---
title: "413_permutation"
date: 2023-09-18T13:45:07-05:00
draft: false
math: true
tags: ["Combinatorics"]
---
# Permutation of Sets

<span style="color:#28a745">Definition</span> permutation
A permutation of a set $S$ can be thought of as a listing of the elements $S$ in some order.

$P(n, r)$ denotes the number of $r$-permutations of an $n$-element set.



<span style="color:#28a745">Definition</span> $r$-permutation

An $r$-permutation of a set $S$ is a string $a_1, a_2, ... a_r$ where $a_i \in S, \forall i \in [r]$ and $a_i \neq a_j$ for $i \neq j$.

Note: $[r] = {1, 2, ..., r}$



### <span style="color:#3c66b5">Theorem</span>

For $n$ and $r$ positive integers with $r \leq n$, 
$$
P(n, r) = n \cdot (n - 1) \cdot \cdot \cdot(n - r + 1)
$$
<span style="color:#eb861c">Proof</span> by multiplication principle.

WIth the notation of factorial, we can write: 
$$
P(n, r) = \frac{n!}{(n - r)!}
$$

<span style="color:#04c2b2">Exercise</span>
How many ways are there to label the squares for the $4 \times 4$ chessboard with the numbers $1,2, ..., 15$, in such a way that exactly one square does not receive any label? 

**solution**: Consider labeling the empty square with 16...

<span style="color:#04c2b2">Exercise</span>
What is the number of ways to order the 26 letters so that no two vowels a, e, i, o, u occurs consecutively?

Left as an exercise. 



<span style="color:#04c2b2">Exercise</span>
How many seven-digit numbers are there such that the digits are distinct integers taken from $\{1, 2, ..., 9\}$ and such that the digits 5 and 6 do not appear consecutively in either order?

**solution:** 
$m$ = The number of all possible combination = $\frac{9!}{2!}$.

$k$ = The number of strings of size 6 with distinct elements in $\{1, 2, 3, 4, 7, 8, 9, x\}$ and containning $x$, where $x = 56$.
$= 6 \cdot 7 \cdot 6 \cdot 5 \cdot 4 \cdot 3$

The first 6 is for the position to place $x$.

Ans = $m - 2k$

---

## Circular permutation

### <span style="color:#3c66b5">Theorem</span>

The number of circular $r$-permutation of a set of $n$ elements is given by: 


$$
\frac{P(n, r)}{r} = \frac{n!}{r \cdot (n-r)!}
$$
<span style="color:#eb861c">Proof</span> 
Similar to the line permutation. We divide the number by $r$ because the same circle is counted $r$ times for all circles. 


### Reference:

https://lmattos.web.illinois.edu/math-413-lecture-log/, MATH 413, Leticia Dias Mattos



# IF YOU KNOW LESS FORMULAS, YOU WOULD HAVE MORE SPACES IN YOUR BRAIN. 😝


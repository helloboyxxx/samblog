---
title: "413_Pigeonhole Principle"
date: 2023-09-15T17:28:11-05:00
draft: false
math: true
tags: ["Combinatorics"]
---
# Pigeonhole Principle

If $n+1$ objects are distributed into $n$ boxes, then at least one box contains two or more of the objects. 

<span style="color:#eb861c">Proof</span>

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



<span style="color:#04c2b2">Exercise</span> There are 5 points in a square of side length 2. Prove that at least two of them are with the distance at most $\sqrt{2}$.

Equally divide this square into four smaller squares with side length 1. By the pigeonhole principle, $\exists$ one $1 \times 1$ square with $ \geq$ 2 points. 



### <span style="color:#3c66b5">Theorem</span>

A grid of 27 points (forming a $3 \times 9$ square) in the plane is given.Each point is coloured red or blue. Prove taht there exists a monochromatic rectangle, that is, a rectangle with all four vertices of the same color. 

<img src="https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/points.png" alt="points" style="zoom:50%;" />

<span style="color:#eb861c">Proof</span>

Consider the the pattern of coloring of a single column. Each colum has 3 points. 
Then, there are $2^3  = 8$ ways of coloring this column. As there are 9 columns in this square, by pigeonhole principle, there are at least two columns in the same pattern. Again, by the pigeonhole principle, each column must have at least two red or two blue. 

---

### More abstract formulations of the pigeonhole principle



Let $X$ and $Y$ be finite sets and let $f: X \to Y$ be a function from $X$ to $Y$. 

<span style="color:#599eff">Proposition</span> If $X$ has more elements than $Y$, then $f$ is not injective. 

<span style="color:#eb861c">Proof</span>

Let $X = \set{x_1, ..., x_n}$, $Y = \set{y_1, ..., y_m}$

Define $A_i = \set{x_j : f(x_j) = y_i}, \forall i \in \set{1, ..., m}$.

Then we have: $n = |X| = |A_1| + ... + |A_m|$

Suppose for contradiction that $f$ is injective

$\implies |A_i| \leq 1 \implies |X| = |A_1| + ... + |A_m| \leq m \implies n \leq m$. Contradiction

<span style="color:#599eff">Proposition</span> If $X$ and $Y$ have the same number of elements and $f$ is surjective, then $f$ is injective. 

<span style="color:#eb861c">Proof</span> $n = |X| = |A_1| + ... + |A_m| \geq m$ by the definition of surjective. And since $m=n$, $|A_1| + ... + |A_m| = m \implies |A_i| = 1$

<span style="color:#599eff">Proposition</span> If $X$ and $Y$ have the same number of elements and $f$ is injective, then $f$ is surjective. 



### <span style="color:#3c66b5">Theorem</span>

Let $m$ be any positive integer and let $a_1, ..., a_m$ be a sequence be any sequance of $m$ integers. Then, there exsist consecutive $a$'s in the sequence whose sum is divisible by $m$. 

That is, there exists integers $k$ and $l$ with $0 \leq k \leq m$ for which $a_{k+1} + a_{k+1} + ... + a_l$ is divisible by $m$. 

<span style="color:#eb861c">Proof</span>

Pigeons:
`
\begin{matrix}
s_1 =& a_1\\
s_2 =& a_1 + a_2\\
\vdots\\
s_m =& a_1 + a_2 + ... + a_m
\end{matrix}
`

Pigeonholes: 
$$
A_r = \set{n \in \mathbb{Z} : n = qm + r, q \in \mathbb{Z}}, \text{where } r \in \set{1, ..., m}
$$



The rule is to put $s_i$ into $A_r$ if $s_i \equiv r \mod{m}$.

Notice that we select $r$ from $1$ to $m$. This is because: 

Whenever we have some $k \in \set{1, .., m}$ such that $a_1 + ... + a_k = qm = qm + 0$, we have done finding our goal sequence.

Otherwise, putting $m$ pigeons into $m-1$ pigeonholes gives us a fact that $\exists i, j \in \set{1, ..., m}, i \neq j$ such that $(a_1 + ... + a_i) \equiv (a_1 + ... a_j) \text{ mod }m $. WLOG, suppose $i < j$, we have $m \mid (a_{i+1} + ... + a_j)$, giving us what we want.



<span style="color:#04c2b2">Exercise</span>

A chess master who has 11 weeks to prepare for a turnament decies to play at least one game everday. But to avoid tiring himself, he decides not to play more than 12 games during any calendar week. Show that there exists a succession of days during which the chess master will have played exactly 21 games. 

**Solution: **

$77 \leq \text{number of games} \leq 132$

Define the sequence: 
`
\begin{align*}
a_1 &= \text{\# games played at day 1}\\
a_2 &= \text{\# games played at day 1 and day 2}\\
\vdots\\
a_{77} &= \text{\# games played from day 1 to day 77}
\end{align*}
`
Define another sequence: 

`
\begin{align*}
&a_1 + 21\\
&a_2 + 21\\
&\vdots\\
&a_{77}+21
\end{align*}
`


Put these two sequences together, we have a sequance of size $77 \cdot 2 = 154$

The goal is to show that two of them are equal. Note that there are 132 games at maximum, then the maximum number in this $132 + 21 = 153$.

By the pigeonhole pirinciple, two of them are equal. And since these two equal number may not come from the same sequence, $\exists a_i = a_j + 21$, which gives us the consecutive days $i$ to $j$. 



### <span style="color:#3c66b5">Chinese Remainder Theorem</span>

Let $m$ and $n$ be relatively prime positive integers, and let $a$ and $b$ be integers where $0 \leq a \leq m - 1$ and $0 \leq b \leq n - 1$.

Then, there is a positive integer $x$ such that $x = pm + a = qn + b$ for some integer $p,q$.

<span style="color:#eb861c">Proof</span>

Consider the sequence that has $n$ numbers in this sequence. 
$$
a, m + a, 2m+a, ..., (n-1)m + a
$$

**Claim:** No two numbers in this sequence have same remainder division by $n$. 

Suppose, by contradiction, that $\exists i< j, p, q, \in \mathbb{Z}, \text{and } r \in \set{0, ..., n-1}$ such that: 

$im + a = pn + r$ and $jm + a = qn + r$. This gives us:
$$
(j - i)m = n(q-p)\\
\implies n \mid (j - i)m\\
\implies n \mid (j-i)
$$
As $i, j \leq n - 1 \implies 0 \leq j-i \leq n-1 \implies j-i = 0$, giving us a contradiction

Then the claim is true. 

Therefore, all the remainders show up $\implies$ there exists $i$ such that $im + a = pn + b, p \in \mathbb{Z}$. $\blacksquare$



### <span style="color:#3c66b5">Strong Form of Pigeonhole Principle</span>

Let $q_1, q_2, ..., q_n$ be positive integers.
If $q_1 + ... + q_n - n + 1$ objects are distributed into $n$ boxes, then either the first box contains at least $q_1$ objects, or the second box contains at least $q_2$ objects,... or the $n$ th box contains at least $q_n$ objects.

<span style="color:#eb861c">Proof</span>

Suppose for contradiction that: 

- Box 1 recieves $\leq q_1 - 1$
- Box 2 recieves $\leq q_2 - 1$
- ...
- Box $n$ recieves $\leq q_n - 1$ 

Which sums to $(q_1 + .. + q_n) - n$

As we have the number of objects = $q_1 + ... + q_n - n + 1$

Then the contradiction happens. $\blacksquare$



<span style="color:#3c66b5">Corollary</span>

If $n(r-1)+1$ objects are distributed into $n$ boxes, then at least one of the boxes contains $r$ or more of the objects.

<span style="color:#eb861c">Proof</span>

Take $q_1 = q_2 = ... = q_n = r$

$n(r - 1) + 1 = nr - n + 1 = (q_1 + ... + q_n) - n + 1$

By theorem, there must be one box $\geq r$. $\blacksquare$



### <span style="color:#3c66b5">Another way to formulate the pigeonhole principle</span>

Let $m_1, m_2, ..., m_n$ be non-negative integers. if 
$$
\frac{m_1 + ... + m_n}{n} > r - 1
$$
then at least one of the integers is greater or equal to $r$. 

<span style="color:#eb861c">Proof</span>

By contradiction, suppose that $m_i < r, \forall i$. We can take the maximum value: $mi = r-1, \forall i$, which gives us: 
`
\begin{align*}
\sum_{i=1}^{n} m_i = n(r-1)\\
\frac{\sum_{i=1}^{n} m_i}{n} = (r-1)
\end{align*}
`
Clearly, there is a contradiction. $\blacksquare$



<span style="color:#04c2b2">Exercise</span>


* Two disks, one smaller than the other, are each divided into 200 congruent sectors.

* In the larger disk, 100 of the sectors are chosen arbitrarily and painted red; the other 100 sectors are painted blue. 

* In the smaller disk, each sector is painted either red or blue with no stipulation on the number of red and blue sectors. 

* The small disk is then placed on the larger disk so that their centers coincide. 

* Show that it is possible to align the two disks so that the number of sectors of the small disk whose color matches the corresponding sector of the large disk is at least 100.

> Text copied from professor Leticia Dias Mattos's Slide: https://lmattos.web.illinois.edu/math-413-lecture-log/

<span style="color:#eb861c">Proof</span>

**Define:** a configuration $c$ is just a way of placing the small disk on the large disk with aligned colors.

We can label (or mark the position of) the disk from 1 to 200

Double counting the following set:
$$
S = \set{(c, i): c \text{ is a configuration and the sector } i \text{ have matching colors}}
$$
(1)

For each $i$, let $t_i = $ number of configurations so that the sector $i$ has matching colors

Then $|S| = \sum_{i=1}^{200} t_i = 200 \cdot 100$ 

(2)

For each configuration $c$, let $a_c$ be the number of sectors that has same color in the same label(position)

`
\begin{align*}
|S| &= \sum_{\text{c config}}^{} a_c\\
\frac{|S|}{200} &= \frac{\sum_{\text{c config}}^{} a_c}{200} = 100 > 100-1
\end{align*}
`
By pigeonhole principle, done. $\blacksquare$


### Reference:

https://lmattos.web.illinois.edu/math-413-lecture-log/, MATH 413, Leticia Dias Mattos


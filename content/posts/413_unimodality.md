---
title: "413_Unimodality of binomial coef & Sperner's theorem"
date: 2023-10-10T22:55:46-05:00
draft: false
math: true
tags: ["Combinatorics"]
---

# Unimodality of Binomial Coefficients and Sperner's Theorem 

If we examine the binomial coefficients in a row of Pascal's triangle, we notice that the numbers increase for a while and then decrease. A sequence of numbers with this property is called **unimodal**. 

### <span style="color:#3c66b5">Theorem</span>

Let $n$ be a positive integer. The sequence of binomial coefficients
$$
{{n} \choose {0}}, {{n} \choose {1}}, \ldots, {{n} \choose {n}}
$$
is a unimodal sequence. Mor precisely, 
$$
{{n} \choose {0}} < {{n} \choose {1}} < \ldots < {{n} \choose {\lfloor n/2\rfloor}}
$$
and 
$$
{{n} \choose {\lceil n/2 \rceil}} > \ldots {{n} \choose {n-1}} > {{n} \choose {n}}
$$


<span style="color:#eb861c">Proof</span>

$k \in \{0, \ldots, n\}$

Compare ${{n} \choose {k}}$ to ${{n} \choose {k-1}}$ by using division: 
$$
\frac{{{n} \choose {k}}}{{{n} \choose {k-1}}} = \frac{n-k+1}{k} < 1 \iff n-k+1 < k \iff \frac{n+1}{2} < k
$$
When $n$ is odd: $\frac{n+1}{2}$ gives us $\lceil \frac{n}{2} \rceil$

$\implies$ ${{n} \choose {k}} < {{n} \choose {k-1}} \iff k > {\lceil n / 2\rceil}$

and also ${{n} \choose {k}} > {{n} \choose {k-1}} \iff k < {\lceil n / 2\rceil}$

Note that: ${{n} \choose {k}} = {{} \choose {}}$

==TBC==



We want to use this theorem to prove Sperner's theorem. But we need some definition first.



<span style="color:#28a745">Definition</span> (Chain)

We say that a collection $\mathcal{C}$ of subsets of $S$ is a chain provided that for that each pair of subsets in $C$, one is contained in the other:

$$
A_1, A_2 \in \mathcal{C}, A_1 \neq A_2, \text{ implies that } A_1 \subset A_2 \text{ or } A_2 \subset A_1.
$$



<span style="color:#28a745">Definition</span> (antichain)

An antichain of a set $S$ is a collection $\mathcal{A}$ of subsets of $S$ with the property that no subset in $\mathcal{A}$ is contained in another.

Let $\mathcal{F}$ be a collection of sets. It is an antichain if $A, B \in \mathcal{F}, A\neq B$ then $A \nsubseteq B$ and $B \nsubseteq A$.



Example: $\{\{1,2\}, \{2,3\}, \{3,4\}\}$

> Question: Let $S$ be a set of $n$ elements. What is the maximum size of a antichain on $S$?



### <span style="color:#3c66b5">Sperner's theorem</span>

Let $S$ be a set of $n$ elements. The maximum size of an antichain on $S$ is $\binom{n}{\lfloor n/2\rfloor}$



<span style="color:#eb861c">Proof</span>

$[n] = \{1, 2, \ldots, n\}$

Fix $\mathcal{F}$ antichain in $[n]$

$\mathcal{C} = \{A \subset S : |A| = {\lfloor n/2\rfloor}\}$

$\mathcal{P} = \{(\mathcal{C}, A): A \in \mathcal{F} \cap \mathcal{C} \text{ and  } \mathcal{C} \text{ is the maximal chain in }S\}$. 🧐 This is CRITICAL

We want to proof this theorem by double conting this $\mathcal{P}$.  Our goal is to bound $|\mathcal{F}|$ using $\mathcal{P}$. 



**The upper bound**

> Question 1: What is the number of maximum chain in $[n]$? Ans: n!
>
> Question 2: Given a maximal chain $\mathcal{C}$, $|\mathcal{F} \cap \mathcal{C}| \leq ?$ Ans: 1

By Q1 and Q2, we can give an upper bound $|\mathcal{P}| \leq n!$.

> Question 3: Fix a set $A \in \mathcal{F}$. What is the number of maximal chain $\mathcal{C}$ have $A \in \mathcal{C}$?
>
> Answer: $|A|!$ to permutate the first half. $(n-|A|)!$ to permutate the second half. So we have $|A|! \cdot (n-|A|)!$ such maximal chains. 

By Q1, Q2, Q3, we have
`
\begin{align*}
\sum_{A \in \mathcal{F}}|A|! \cdot (n-|A|)! = |\mathcal{P}| \leq n!\\
\implies
\sum_{A \in \mathcal{F}}\frac{1}{\binom{n}{|A|}} \leq 1 && \text{divide both side by }n!
\end{align*}
`
As we have the unimodel theorem above, 
`
\begin{align*}
\binom{n}{\lfloor n/2 \rfloor} &\geq \binom{n}{|A|}, \forall A\\
\frac{1}{\binom{n}{\lfloor n/2 \rfloor}} &\leq \frac{1}{\binom{n}{|A|}}
\end{align*}
`
Then we continue: 
`
\begin{align*}
\frac{|\mathcal{F}|}{\binom{n}{\lfloor n/2 \rfloor}} &\leq \sum_{A \in \mathcal{F}}\frac{1}{\binom{n}{|A|}} \leq 1\\
|\mathcal{F}| &\leq \binom{n}{\lfloor n/2 \rfloor}
\end{align*}
`
$\blacksquare$





Here is an interesting application.

### <span style="color:#3c66b5">Littlewood--Offord theorem</span>

Let $v_1, \ldots, v_n$ be positive integers. Let $x_1, \ldots, x_n$ be random variables so that $\mathbb{P}\left(x_i=1\right)=\mathbb{P}\left(x_i=-1\right)=1 / 2$. Then,
$$
\max _r \mathbb{P}\left(x_1 v_1+\cdots+x_n v_n=r\right)=O\left(\frac{1}{\sqrt{n}}\right) \text {. }
$$
Think of this as an one dimensional random walk problem:

<img src="https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20231009135742559.png" alt="image-20231009135742559" style="zoom:50%;" />

<span style="color:#eb861c">Proof</span>

Let $r \in \mathbb{Z}$ fixed. 

Define:
$$
\mathcal{S} = \{(a_1, \ldots, a_n): a_i \in \{±1\}, \sum_{i=1}^{n}a_iv_i = r\}
$$

$$
\mathbb{P}(x_1v_1 + \ldots + x_nv_n = r) = \frac{|\mathcal{S}|}{2^n}
$$

For each solution $s = (a_1, \ldots, a_n) \in \mathcal{S}$ define: 
$$
A_s = \{i : a_i = 1\}
$$
<span style="color:#9650af">Observation</span> given this $A_s$, we can always find an $s$. 

**Claim:** the family $\mathcal{F} = \{A_s : s \in \mathcal{S}\}$ is an antichain. 

Short proof by contradiction: Suppose there exists some $s_1, s_2$ such that $A_{s_1} \subset A_{s_2}$. We have $s_1$ as one solution, and it has $|A_{s_1}|$ many $+1$ steps. Also because that $A_{s_1} \subset A_{s_2}$ , $s_2$ has all the $+1$ steps as $s_1$, but it also flips some $-1$ steps of $s_1$ to $+1$ steps. This makes the resulting point bypass the goal, $r$, which results in an contradiction as $s_2$ cannot be a solution. 

Then, by the observation, $\exists$ a bijection between $\mathcal{F}$ and $\mathcal{S}$, which means $|\mathcal{F}| = |\mathcal{S}|$. This gives us:
$$
\mathbb{P}(x_1v_1 + \ldots + x_nv_n = r) = \frac{|\mathcal{S}|}{2^n} = \frac{|\mathcal{F}|}{2^n} \leq \frac{\binom{n}{\lfloor n/2\rfloor}}{2^n}
$$
Further simplification: 
$$
\binom{n}{\lfloor n/2\rfloor} \sim \Theta\left(\frac{2^n}{\sqrt n}\right)
$$
Cancelling the $2^n$ gives us the statement of the theorem. $\blacksquare$
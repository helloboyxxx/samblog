---
title: "413_lower bounded Ramsey"
date: 2023-10-04T17:28:53-05:00
draft: false
math: true
tags: []
---

# Lower Bound of Ramsey Number


### <span style="color:#3c66b5">Theorem</span>

==Lower bound...== $R(k) \geq 2^{k/2}$

Before we start the proof, let's look at 3 ingredients we need: 

- The probabilistic method
- The union bound 
- The binomial estimate

#### <span style="color:#599eff">The probabilistic method</span>

Let $\Omega$ be the set of all possible outcomes of an experiment. Suppose that each outcome is equally likely. Let $A \subseteq \Omega$ be an event.
$$
\text{If } \operatorname{Prob}(A) < 1 \text{, then } \operatorname{Prob}(A^c) > 0
$$
**Our setting:**

Let $n \in \mathbb{N}$ to be chosen later. 

Experiment: colro each edge of $K_n$ uniformly at random with red or blue. 

Set of all possible outcome is:

$$
\Omega = \set{\text{red, blue}} ^{{n} \choose {k}}
$$

#### <span style="color:#599eff">Union Bound</span>

Let $\Omega$ be the set of all possible outcome of an experiment. Suppose that each outcome is equally likely. Let $A_1, \ldots, A_t \subseteq \Omega$ be some events. Then: 
$$
\operatorname{Prob}(A_1 \cup A_2 \cup \cdots A_t) \leq \sum_{i=1}^{t}\operatorname{Prob}(A_i)
$$
<span style="color:#eb861c">Proof</span>

Consider the sets: 
`
\begin{align*}
B_1 &= A_1\\
B_2 &= A_2 \setminus A_1\\
B_3 &= A_3 \setminus (A_1 \cup A_2)\\
&\vdots\\
B_t &= A_t \setminus (A_1 \cup \cdots \cup A_t)\\
\end{align*}
`
Notice that: 

- $B_i \cap B_j = \varnothing, \forall i \neq j$
- $B_i \subseteq A_i, \forall i$
- $A_1 \cup \cdots \cup A_t = B_1 \cup \cdots \cup B_t$

<img src="https://github.com/helloboyxxx/images-for-notes/blob/master/uPic/image-20231004160227017.png?raw=true" alt="venn" style="width:50%;" />

These implies that: 
$$
\mathbb{P}(A_1 \cup \cdots \cup A_t) = \sum_{i=1}^{t}\mathbb{P}(B_i) \leq \sum_{i=1}^{t}\mathbb{P}(A_i)
$$


**Our setting:**

Label all the copies of $K_k$inside $K_n$. There are ${{n} \choose {k}}$ of them. 

Our events will be of the follo==wing form:== 
$$
A_i = \{i^{th}\}
$$



#### <span style="color:#599eff">A binomial estimate</span>

$$
\text{If } 1 \leq k \leq n, \text{ then } {{n} \choose {k}} \leq \left(\frac{ne}{k}\right)^k
$$

<span style="color:#eb861c">Proof</span>

We simply use that $1+x \leq e^x$ for all $x \in \mathbb{R}$. 

> To see why this "fact" holds, consider the tangent line of the function $f(x) = e^x$ at $x=0$.

==To Be Continue...==








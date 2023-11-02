---
title: "413_lower bounded Ramsey"
date: 2023-10-04T17:28:53-05:00
draft: false
math: true
tags: ["Combinatorics"]
---

### <span style="color:#3c66b5">Theorem</span>

$$
\text{For every } k \in \mathbb{N}, \text{we have } R(k)\ge 2^{k/2}
$$


Before we start the proof, let's look at 3 ingredients we need: 

- The probabilistic method
- The union bound 
- The binomial estimate

#### <span style="color:#599eff">The probabilistic method</span>

Let $\Omega$ be the set of all possible outcomes of an experiment. Suppose that each outcome is equally likely. Let $A \subseteq \Omega$ be an event.
$$
\text{If } \operatorname{Prob}(A) < 1 \text{, then } \operatorname{Prob}(A^c) > 0
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

<center>
  <figure>
    <img src=" https://github.com/helloboyxxx/images-for-notes/blob/master/uPic/image-20231004160227017.png?raw=true " style="width:50%;" />
    <figcaption>  </figcaption>
  </figure>
</center>

These implies that: 
$$
\mathbb{P}(A_1 \cup \cdots \cup A_t) = \sum_{i=1}^{t}\mathbb{P}(B_i) \leq \sum_{i=1}^{t}\mathbb{P}(A_i)
$$


#### <span style="color:#599eff">The binomial estimate</span>

$$
\text{If } 1 \leq k \leq n, \text{ then } {{n} \choose {k}} \leq \left(\frac{ne}{k}\right)^k
$$

<span style="color:#eb861c">Proof</span>

We simply use that $1+x \leq e^x$ for all $x \in \mathbb{R}$. 

> To see why this "fact" holds, consider the tangent line of the function $f(x) = e^x$ at $x=0$.

Use the binomial theorem
`
\begin{align*}
\left( 1 + \frac{k}{n} \right)^k &= \sum_{i=0}^{n}\left(\frac{k}{n}\right)^i{{n} \choose {i}} &&\text{by Binomial Theorem}\\
&\geq \left( \frac{k}{n} \right)^k \cdot \binom{n}{k} && \text{when $i$ starts from $k$}\\
\end{align*}
`

Since we have the fact: $1+x \leq e^x$, when $x = \frac{k}{n}$, we have:

`
\begin{align*}
\left( e^{k/n} \right)^n = e^k \geq \left( 1 + \frac{k}{n} \right)^k
&\geq \left( \frac{k}{n} \right)^k \cdot \binom{n}{k} \\
\iff 
\left( \frac{en}{k} \right)^k &\geq \binom{n}{k}
\end{align*}
`





### NOW, lets start our proof of the "lower bound" theorem in the beginning

<span style="color:#eb861c">Proof</span> of $R(k)\geq 2^{k/2}$

#### Intuition

We want to show that whenever $n$ is smaller than some number, it is **possible** to have some coloring of $K_n$ such that $\nexists $monochromatic $K_k$.

#### Approaching the proof

Let $n \in \mathbb{N}$ to be chosen later. 

Experiment: color each edge of $K_n$ uniformly at random with red or blue. 

Set of all possible outcome is:
$$
\Omega = \set{\text{red, blue}}^{{n} \choose {2}}
$$

Then, choose a $k$. Label all the copies of $K_k$ inside $K_n$. There are ${{n} \choose {k}}$ of them. 

Our events will be of the following form: 
$$
A_i = \set{i^{th} \text{ clique is monochromatic}}
$$


Consider the probability of each of these $A_i$. They should have the same probability. So $\forall i \in \set{1, \ldots, \binom{n}{k} }, A_i = A_1$. For  each edge in the $K_k$ graph, it can be colored either red or blue. By applying the multiplication principle, this is:
$$
\mathbb{P}(A_i) = 2 \cdot \left( \frac{1}{2} \right)^{|E(K_k)|} = 2 \cdot \left( \frac{1}{2} \right)^{\binom{k}{2}}
$$

We want to know what is the probability of the event $A$, that for all coloring of $K_n$, there exists a monochromatic $K_k$:

`
\begin{align*}
\mathbb{P}\left(A\right) &= \mathbb{P}\left(\bigcup_{i=1}^{\binom{n}{k}}A_i\right) = \mathbb{P}\left(\bigcup_{i=1}^{\binom{n}{k}}A_1\right)\\
&= \binom{n}{k}\mathbb{P}\left( A_1 \right) = \binom{n}{k} \cdot 2 \cdot \left( \frac{1}{2} \right)^{\binom{k}{2}}\\
&\leq \left( \frac{ne}{k} \right)^k \cdot 2 \cdot \left( \frac{1}{2} \right)^{\binom{k}{2}} && \text{binomial estimate}\\
&= \left( \frac{ne}{k} \right)^k \cdot 2 \cdot \left( \frac{1}{2} \right)^{k(k-1)/2}\\
&= \left( \frac{ne\cdot 2^{1/k}}{k\cdot 2^{(k-1)/2}} \right)^k
\end{align*}
`

HERE COMES THE MAGIC!!!

Pick $n = 2^{k/2}$ for this expression, then cancel some terms.
`
\begin{align*}
P(A) &\leq \left( \frac{2^{k/2} \cdot e\cdot 2^{1/k}}{k\cdot 2^{(k-1)/2}} \right)^k\\
&= \left( \frac{2^{1/2} \cdot e \cdot 2^{1/k}}{k} \right)^k
\end{align*}
`
Then, we argue that this is smaller than 1 for all $k \geq 5$. To see why, just check the correctness of the inequality:
$$
\sqrt{2} \cdot e \cdot 2^{1/k} < k
$$
When $k = 5$, left side is about 4.416. When $k$ gets larger, it left side gets closer to $\sqrt{2} e$, which must be smaller than $k$. For $k < 5$ cases, we can just check them by hand. 

When we have the result that $P(A) < 1$, by the probabilistic method, we know the probability of the existance of a coloring such that no monochromatic $K_k$ appears in $K_n$.



> Personally, I have one confusion: when $n = 2^{k/2}$, we have the above result. But we are trying to prove $R(k)\geq 2^{k/2}$... so...🤔?


### Reference:

https://lmattos.web.illinois.edu/math-413-lecture-log/, MATH 413, Leticia Dias Mattos








---
title: "Fermat's Little Theorem"
date: 2024-10-29T17:02:49-05:00
draft: false
math: true
tags: ["cryptography"]
---

# RSA in pure number theory

### Binomial Theorem

Given $a, b \in \mathbb{R}, n \in \mathbb{N}$, then 
$$
(a + b)^n = \sum_{k = 0}^{n} \binom{n}{k}a^k b^{n-k}
$$
<span style="color:#599eff">Proposition</span> Let $p$ be prime. $\forall a, b \in \mathbb{Z}$, we have:
$$
(a+b)^p \equiv a^p + b^p \mod p
$$
<span style="color:#eb861c">Proof</span> It suffices to show that $\binom{p}{k} \equiv 0 \mod p$ if $0 < k < p$. Observe: $p \mid  p!, p \nmid k!, p \nmid (p-k)!$, hence $p \mid \binom{p}{k}$. $\blacksquare$

### Fermat's Little Theorem

Let $p$ prime, $a \in \mathbb{Z}$, 

1. $a^p \equiv a \mod p$
2. If $p \nmid a$, then $a^{p-1} \equiv 1 \mod p$

<span style="color:#eb861c">Proof(1)</span> For $a \geq 1$, use induction on $a$.

Base case $a = 1, 1^p = 1$ holds. 

For $a > 1, (a + 1)^p \equiv a^p + 1^p \equiv a + 1 \mod p$, by the previous proposition. 

For $a < 1$, symmetric. $\blacksquare$

<span style="color:#eb861c">Proof(2)</span> By definition of $\equiv$, we know $p \mid a^p - a \implies p \mid a(a^{p-1} - 1)$. $p$ is a prime, $p \nmid a \implies p \mid a^{p-1} - 1$. $\blacksquare$

### Two-prime Fermat's Little Theorem

Let $p, q$ be distinct primes. Let $m = \mathsf{lcm}(p-1, q-1)$. If $a \in\mathbb{Z}, h \in\mathbb{N} $ such that $h \equiv 1 \mod m$, then $a^h \equiv a \mod pq$.

> This is almost identical to Euler's Theorem when $N = pq$. 

<span style="color:#eb861c">Proof</span> We know $h = 1 + tm$ for some $t \in \mathbb{Z}$. 
$$
a^h - a = a^{1+tm} - a = a(a^{tm} - 1)
$$
We want to show $pq \mid (a^h - a)$, so show $pq \mid a(a^{tm} - 1)$. But also $\mathsf{gcd}(p, q) = 1$, so this is same as showing $p \mid a(a^{tm} - 1), q \mid a(a^{tm} - 1)$ separately. 

Claim: if $p \nmid a$, then $p \mid a^{tm} - 1$.

$m = \mathsf{lcm}(p-1,q-1)$, so $m = (p-1)s$, for some $s \in \mathbb{N}$. 
$$
a^{tm} = a^{ts(p-1)} = (a^{p-1})^{ts} \equiv 1^{ts}  \equiv 1 \mod p
$$
$q$ is similar. $\blacksquare$

> This proof is actually very similar to proof of Euler's theorem. It's just not using the Lagrange's theorem.








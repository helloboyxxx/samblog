---
title: "Commitment and Signatures"
date: 2024-12-13T00:03:24-06:00
draft: false
math: true
tags: ["cryptography"]
---


### <span style="color:#28a745">Definition</span> Commitment

- Parameters $\mathsf{pp} \gets \mathsf{Gen}(1^n)$. 
- $\mathsf{com} \gets \mathsf{Commit}(m, r)$
- $\set{0, 1} \gets \mathsf{Open}(\mathsf{com}, m, r)$.

**Binding:** an adversary can’t open the commitment to a different message $m'$.

**Hiding:** $\mathsf{com}$ does not reveal any information about the message $m$. 

> One naive approach is to use hash. However, hash is not hiding.

### Pedersen commitment

- $\mathsf{Gen}(1^n)$: group $\mathbb{G}$ with order $q$ and random generators $g, h$. 
- $\mathsf{Commit}(m, r)$: pick a random $r \gets \mathbb{Z}_q$, compute $\mathsf{com} = g^mh^r$. 
- $\mathsf{Open}(\mathsf{com}, m, r)$: check if $\mathsf{com} = g^mh^r$. 

This scheme is computationally binding: if we express $h = g^x$ for some $x$, then finding $m' \neq m$ such that $g^mh^r = g^{m+rx} = g^{m' + r'x} = g^{m'}h^{r'}$ is hard by discrete log assumption.

It is perfectly hiding because $h^r$ acting as a one-time pad. 



### Sigma protocol

> This is a general protocol for proof of knowledge: proving that I know something.

<center>
  <figure>
    <img src=" https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20241212163716582.png " style="width:50%;" />
        <img src=" https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20241212163729442.png " style="width:50%;" />
  </figure>
</center>

To show the security of ⬆️, we need to show:

- Special soundness: suppose verifier already has a commitment $\mathsf{com} = g^\alpha h^\beta$, then for any adversary



### Fiat-Shamir Transformation

> Making public-coin interactive protocols non-interactive

We can use this transformation to make Sigma protocol non-interactive.

<center>
  <figure>
    <img src=" https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20241212165155456.png " style="width:50%;" />
    <figcaption>  </figcaption>
  </figure>
</center>

This is using the randomness given by random oracle. 

---

### <span style="color:#28a745">Definition</span> Signatures

- sk: private key, pl: public key, m: message, $\sigma$ : signature
- $(p k, s k)=\operatorname{Gen}\left(1^n\right)$
- $\sigma=\operatorname{sign}_{s k}(m)$
- $\{0,1\} \leftarrow \operatorname{Verify}_{\mathrm{pk}}(\sigma, m)$

**Correctness**: $\text{Verify}\_{\mathbf{p k}}(\sigma, m)=1$ for $(p k, s k) \leftarrow \operatorname{Gen}\left(1^n\right)$, any message $m \in \mathcal{M}, \sigma=\operatorname{sign}_{s k}(m)$

**Security**
Experiment Sig_forge $_{A, \Pi}(n)$ :

1. $(p k, s k)$ are generated using Gen $\left(1^n\right)$
2. Adversary $A$ is given $p k$, and oracle access to $\operatorname{sign}_{s k}(\cdot)$. Let Q be the set of all queries made by $A$
3. $A$ outputs $(m, \sigma)$
4. Experiment outputs 1 if (1) verify ${ }_{\mathrm{pk}}(m, \sigma)=1$ and (2) $m \notin Q$

Definition: a signature scheme $\Pi=$ (Gen, Sign, Verify) is unforgeable/secure, if for all PPT adversaries $A$, there is a negligible function negl such that for all $n$,

$$
\operatorname{Pr}\left[\text {SigForge}_{A, \Pi}(n)=1\right] \leq \operatorname{negl}(n)
$$

> Essence: others cannot create your signature without knowing the secret key.

---

### Plain RSA Signature: 

> Almost the same as plain RSA encryption. Simply swap encryption and decryption.

- Gen: choose two large prime numbers p and q such that $p \neq q$. Set $N = pq$. Pick integer $e$ coprime with $\phi(N)=(p-1)(q-1)$, compute $d$ such that $e \cdot d \equiv 1 \bmod \phi(N)$. 
Public key $pk=(N, e)$ Private key $sk = d$
- $\operatorname{sign}_{s k}(m): \sigma=m^d \bmod N$
- $\operatorname{verify}_{p k}(\sigma, m)$ : if $\sigma^e=m \bmod N$, output 1 ; otherwise, output 0



**However**, this scheme is not secure as plain RSA is malleable / multiplicative homomorphic. (Try multiplying two messages together.)

### RSA full-domain hash

- Gen: choose two large prime numbers p and q such that $p \neq q$. Set $N = pq$. Pick integer $e$ coprime with $\phi(N)=(p-1)(q-1)$, compute $d$ such that $e \cdot d \equiv 1 \bmod \phi(N)$. **Specify a hash function** $H: \set{0, 1}^* \to \mathbb{Z}_N^*$.
  Public key $pk=(N, e)$ Private key $sk = d$
- $\operatorname{sign}_{s k}(m): \sigma=(H(m))^d \bmod N$
- $\operatorname{verify}_{p k}(\sigma, m)$ : if $\sigma^e=H(m) \bmod N$, output 1 ; otherwise, output 0

Since this kills the homomorphic property of plain RSA signature.



### RSA Assumption

1. Run $\operatorname{Gen}\left(1^n\right)$ to obtain $(N, e, d)$
2. Choose a random $y \in \mathbb{Z}_N^*$
3. $A$ is given $(N, e, y)$ and outputs $x \in \mathbb{Z}_N^*$
4. Output 1 if $x^e=y \bmod N$

$$
\operatorname{Pr}\left[\operatorname{RSA}_{\mathrm{A}}(n)=1\right] \leq \operatorname{negl}(n)
$$

### Security proof for RSA full-domain hash signature

<span style="color:#eb861c">Proof</span> We prove by using reduction from RSA assumption to RSA full-domain hash. Suppose there exists an attacker $A$ for RSA full-domain hash.



#### Observations

- Suppose $A$ will make $q$ queries to $H$, where $q$ is in polynomial. Here, $H$ is a random oracle.

- Let $M$ be the set of all queries to $H$: $M = \set{m_1, \ldots, m_q}$. 

- Let $Q$ be the set of all queries to the signing oracle. 

- If $A$ outputs successful forgery $(m^\*, \sigma^\*)$, by definition of signature forgery, $m^* \not \in Q$. For the verification to work, we need $(\sigma^\*)^e = H(m^\*)$. If $A$ does not use $H$, by definition of random oracle, the probability of getting a correct result is negligable. Hence, we know $A$ must use $H$ for its attack.

#### Build attacker $A'$ for RSA assumption

We can now build $A'$: input $N, e, y$, output $x$ such that $x^e = y \mod N$. 

- We first pick a random index $j \in \set{1, \ldots, q}$. 
- **We build our own random-oracle for the attacker**. 
  - For query $H(m_i)$ where $i \neq j$, we first pick a random $\sigma_i \in \mathbb{Z}_N^*$, then compute $\sigma_i^e \mod N$ and return to the attacker. Record the result for duplicated queries.
  - For query $H(m_j)$ where $i = j$, we simply return $y$. (We can do this because we know $y$ is also a random element in $\mathbb{Z}_N^*$, which has same distribution as the $\sigma_i^e$ for other $i$'s). Record the result for duplicated queries. If $m_j \in Q$, then abort. 
- **We build our own signature scheme for the attacker**. For a query $\mu$, 
  - If $\mu = m_j$, abort because we don't know how to compute a $\sigma_j$ such that $\sigma_j^e = y$.
  - Otherwise, return the recorded $\sigma_i$ if $\mu$ is seen before, or a new random $\sigma$, and record
- If $A$ outputs $m^* = m_j$, and the corresponding signature $\sigma_j$, we can output $\sigma_j$ directly. Otherwise, abort.

Attacker $A'$ successes with probability $1/q$ of $A$ success rate.

---

### Schnorr Identification Scheme

> An identification scheme is used for the holder of the private key to prove to you that they hold the private key.

<center>
  <figure>
    <img src=" https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20241212165431395.png " style="width:50%;" />
    <figcaption>  </figcaption>
  </figure>
</center>

- In step 5: right side $= (g^x)^r \cdot g^k = g^s = \text{left side}$ if everyone is honest.
- Observe that if the prover hides $k$, given $s$, it is still impossible for veirifier to learn $rx$. So $k$ is a kind of one-time pad, and $k$ should be hidden.

Now we can build **non-interactive** variant using Fiat-Shamir Transformation, by setting $r = H(K)$.

<center>
  <figure>
    <img src=" https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20241212172105218.png " style="width:50%;" />
    <figcaption>  </figcaption>
  </figure>
</center>

### Schnorr Signature Scheme

Now, instead of simply proving that the prover holds secret key, we can prove that it created the message. So, a naive scheme is just a variant of the  **non-interactive** Schnorr identification scheme: change  $r = H(K)$ to $r = H(K || m)$. Everything else is the same. This scheme works, but is not optimal as $K$ is large in terms of size in practice. 

We can avoid using $K$. Instead, can send $r$ directly without revealing $K$. Given one of $r$ and $K$, we can compute the other one easily. 

<center>
  <figure>
    <img src=" https://raw.githubusercontent.com/helloboyxxx/images-for-notes/master/uPic/image-20241212172944723.png " style="width:50%;" />
    <figcaption>  </figcaption>
  </figure>
</center>



### Reference

- [UIUC CS 407 Fall 2024 Lecture 21, 22](https://zhangyp.web.illinois.edu/teaching/ECECS407_Fall2024/)
- Introduction to Modern Cryptography, 3rd edition, Jonathan Katz and and Yehuda Lindell.
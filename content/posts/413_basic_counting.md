---
title: "413_basic_counting"
date: 2023-08-28T14:35:27-05:00
draft: false
math: true
---

# The four basic counting principle

Suppose that a set $S$ is partitioned into pairwise disjoint parts $S_1, S_2, ..., S_n$. 



### **Addition principle:** 

$$
|S| = |S_1| + |S_2| + ... + |S_m|
$$

Ex: 

Path counting: In a $3 \times 3$ grid, if you can move 1 step upward or 1 step to the right. How many ways do we have to move from bottom-left to top-right corner?

The idea is to break this problem into smaller problems. Addition principle guarrantees that we can add the numbers together. 

Think of the final step we need to take. It must be either an up or a right. This makes the problem to become a similar but smaller problem that has $2 \times 3$ size. Mark it $n_{2\times 3}$

Using the same idea, we have: 
$$
n_{3 \times 3} = 2 * n_{2 \times 3}
= 2 * (n_{2 \times 2} + n_{3 \times 1})\\
=
$$

### **Multiplication principle**

Let $S$ be a set of ordered pairs $(a, b)$ of objects, where the first object $a$ comes from a set of size $p$, and for each choice of object $a$ there are q choices for object $b$. Then the size of $S$ is 
$$
|S| = p \cdot q
$$

**Generalized multiplicative principle**

Let $S$ be a finite set of $p$-tuples $a = (a_1, ..., a_p)$ and let $t_1, ..., t_p$ be some positive numbers.

Suppose that for every $a = (a_1, ..., a_p) \in S$, and every $i \in \{1, ..., p\}$, we have
$$
|\{b \in S:b_j = a_j, \forall j \neq i\}| = t_i
$$
Then, 
$$
|S| = t_1 \cdot t_2 \cdot ... t_p
$$
(4) counts the number of choices if we fix all other dimension except $i$.



Ex: 

**Determine the number of positive integers that are factors of the number $2^{10}\cdot 7 \cdot 13^3$.**

This number can be written as: 
$2^{a}\cdot 7^b \cdot 13^c$.
Then just consider the number of choices for $a, b, c$:

$a \in \{0, 1, ... 10\}$
$b \in \{0, 1\}$
$c \in \{0, 1, 2, 3\}$

In total, $11 \cdot 2 \cdot 4 = 88$



### **Observation**

In the multiplication principle the $q$ choices for object $b$ may vary the choice of $a$. The only requirement is that there be the same number $q$ of choices, not necessarily the same choices. 

(When we choose one coordinate, the choices for other coordinates changes)

Ex: 

How many two-digit numbers have distinct and nonzero digits? 

9 * 8 = 72. The first digit has 9 choices, the second digit has 8 (since 0 and the 1st choice are not allowed)



### **Subtraction Principle**

Let $A$ be a set and let $U$ be a larger set containing $A$. Let 
$$
\bar{A} = U \setminus A = \{x \in U : x \notin A\}
$$


Ex: 

Computer passwords are consist of a string of six symbols taken from digit 0 to 9 and letters a to z. 

How many computer passwords have a repeat symbol?

ans: The number of total passwords - passwords that don't repeat. 

= $36^6 - 36 * 35 * 34 * 33 * 32 * 31$

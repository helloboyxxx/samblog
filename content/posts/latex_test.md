---
title: "Some latex tests"
date: 2023-08-28T22:39:19-05:00
draft: true
math: true
---

Consider a $n \times m$ chessboard...


$$
\int{f(x)dx}
$$


Since $94 = 4 + 5x$ for some $x \in \mathbb{N}$, my claim is that the first player wins when it chooses $4$ in the beginning. Then, whenever the second player choose $a, x \in\{1, 2, 3, 4\}$, the first player just add it to 5. So choose $5-a$. By doing this, the first player always reaches $10x + 9$ or $10x + 4$ for $x \in \mathbb{N}$. Since $94$ is included, the first player must win. 


$\mathfrak{ABCDEFG}$


Hi `$z = x + y$`.

`$$a^2 + b^2 = c^2$$`

`$$\begin{vmatrix}a & b\\
c & d
\end{vmatrix}=ad-bc$$`

from: https://yihui.org/en/2018/07/latex-math-markdown/

### complex math (array)
`$$
\begin{array} {lcl}
  L(p,w_i) &=& \dfrac{1}{N}\Sigma_{i=1}^N(\underbrace{f_r(x_2
  \rightarrow x_1
  \rightarrow x_0)G(x_1
  \longleftrightarrow x_2)f_r(x_3
  \rightarrow x_2
  \rightarrow x_1)}_{sample\, radiance\, evaluation\, in\, stage2}
  \\\\\\ &=&
  \prod_{i=3}^{k-1}(\underbrace{\dfrac{f_r(x_{i+1}
  \rightarrow x_i
  \rightarrow x_{i-1})G(x_i
  \longleftrightarrow x_{i-1})}{p_a(x_{i-1})}}_{stored\,in\,vertex\, during\,light\, path\, tracing\, in\, stage1})\dfrac{G(x_k
  \longleftrightarrow x_{k-1})L_e(x_k
  \rightarrow x_{k-1})}{p_a(x_{k-1})p_a(x_k)})
\end{array}
$$`


### Testing alignments

`$$
\begin{align*}
\frac{1}{\Gamma(s)}\int_{0}^{\infty}\frac{u^{s-1}}{e^{u}-1}\mathrm{d}u
\end{align*}
$$`


### Hx tests
test: 看看以下代码能不能打出来：

1. 
$$
\mathcal{F}
$$

2. 
$$
\lambda_i \xlongequal[]{\text{eq.}(1)}\int_{\{i\}}
$$

3. 
`$$
\begin{align*}
  \text{(1) } 0\oplus 0 & = 0\\
  \text{(2) } 1\oplus 0 & = 1\\
  \text{(3) } 0\oplus 1 & = 1\\
  \text{(4) } 1\oplus 1 & = 0
\end{align*}
$$`

We observe that:

4.
$$
\begin{itemize}
  \item for $y=x\oplus z$, $y$ agreees with $x$ if (1) or (3) happen; disagrees 
  if (2) or (4) happen.
  \item $y=0$ iff $x$ and $z$ agree; $y=1$ iff $x$ and $z$ disagree.
\end{itemize}
$$
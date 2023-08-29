---
title: "413_chessboard"
date: 2023-08-29T17:24:30-05:00
draft: false
math: true
---

### Gomor's Theorem:

**If you move two cells of a $8 \times 8$ chessboard of opposite colors, the remaining cells can be fully domino tiled.** 

Pf: 

Draw a closed path that passes through every square exactly once. (Draw a big C and then draw back and forth horizontally)

Choose the two cells to be removed, and the closed path we have will be sperated into two paths. 

If we lable the close path we chose in the beginning from 1 to 64 in the order we drew it, white cells have odd numbers, and black cells have even numbers (or reversed).

Easy to see that the path in between the two cells crosses even number tiles. 



### Gomor's on more general chessboard ($n \times m$ board):

**The two opposite corners must be in opposite color iff n and m has different paritity.** 

PF: Consider the "L" shape edge of the board(half the square), there are $m + n - 1$ tiles. When this number is even, they are in opposite color. 

Then check: **When m and n have different parity, then there must be an "S" shape closed path to cross all the tiles.** 



Def: b-ominos. It covers b tiles in a row...



### Thm: An $m \times n$ board has a tiling with b-ominos iff $b|m$ or $b|n$. 

$\leftarrow$ is trivial. 

$\rightarrow$: 

Color the board: 

`$$
\begin{matrix}
1 & 2 & 3 & 4 & 5 & 6 &...\\
3 & 1 & 2 & 3 & 4 & 5 &... \\
2 & 3 & 1 & 2 & 3 & 4 &... \\
.\\
.\\
.
\end{matrix}
$$`

Consider the board has dimension $m \times n$ and $m = qb + r$, $n = tb + s$

Then, on this board, each b-omino see a color exactly once. 

Assume, for contradiction, $r, s \neq 0$

As we are assuming to have a b-omino tiling, each color shows up the same number of times $\rightarrow$ then in the little $r \times s$ chessboard, each color has the same number of squares.
WLOG, assume $s \leq r$. The number of 1's in the $r \times s$ chessboard = $s$.
The total number of squares is $rs$. Consider we tiling with b-ominos, the number of sqares is also $sb$ (Each b-omino sees every color once, so number of 1's = number of tiles. So $sb$). Cancle out the b, we have the contradiction.


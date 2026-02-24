---
title: Random math
date: 2025-12-09
type: post
tags:
    - Mathematics
    - Problem solving
---
### Random 1
$$
The unit step function $\sigma$ is defined as
\[
\sigma(x)=
\begin{cases}
1, & x \ge 0,\\[4pt]
0, & x < 0.
\end{cases}
\]
Let
\[
f(x)=
\begin{cases}
2, & x \ge -1,\\[4pt]
-3, & x < -1.
\end{cases}
\]
Express $f$ as a linear transformation of the unit step function $\sigma$. 
\textbf{Solution.}

Translation of $\sigma(x)$ by $\xi$ is defined as:

\[
\sigma_\xi(x) = \sigma(x-\xi) =
\begin{cases}
1, & x \ge \xi,\\[4pt]
0, & x < \xi.
\end{cases}
\]

The value of $f(x)$ changes at $x = -1$, which means $\xi = -1$.

\[
f(x) = a \sigma(x+1) + b
\]

\[
f(x) =
\begin{cases}
2, & x \ge -1,\\[4pt]
-3, & x < -1,
\end{cases}
\quad\Longleftrightarrow\quad
\begin{cases}
a + b = 2,\\[4pt]
b = -3.
\end{cases}
\]

\[
\Longleftrightarrow
\begin{cases}
a = 5,\\[4pt]
b = -3
\end{cases}
\]

So the linear transformation of the unit step function is:

\[
f(x) = 5\sigma(x+1) - 3.
\]

$$
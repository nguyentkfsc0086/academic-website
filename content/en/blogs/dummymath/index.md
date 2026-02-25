---
title: Random math
date: 2025-12-09
type: post
tags:
    - Mathematics
    - Problem solving
---
### Random 1

The unit step function $(\sigma)$ is defined as

{{< math >}}
\[
\sigma(x)=
\begin{cases}
1, & x \ge 0,\\
0, & x < 0.
\end{cases}
\]
{{< /math >}}

Let

{{< math >}}
\[
f(x)=
\begin{cases}
2, & x \ge -1,\\
-3, & x < -1.
\end{cases}
\]
{{< /math >}}

Express $(f)$ as a linear transformation of the unit step function $(\sigma)$.


`Solution`

A translation of $(\sigma(x))$ by $(\xi)$ is

{{< math >}}
\[
\sigma(x-\xi)=
\begin{cases}
1, & x \ge \xi,\\
0, & x < \xi.
\end{cases}
\]
{{< /math >}}

The function $(f(x))$ jumps at $(x=-1)$, so take $(\xi=-1)$. Then

{{< math >}}
\[
f(x)=a\,\sigma(x+1)+b.
\]
{{< /math >}}

For $(x<-1)$, $(\sigma(x+1)=0)$, so $(f(x)=b=-3)$.

For $(x\ge -1\)$, $(\sigma(x+1)=1)$, so $(f(x)=a+b=2)$.

Thus,

{{< math >}}
\[
b=-3,\qquad a+b=2 \implies a=5.
\]
{{< /math >}}

Therefore,

{{< math >}}
\[
\boxed{f(x)=5\sigma(x+1)-3.}
\]
{{< /math >}}
### Random 2
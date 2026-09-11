---
title: Random math 2
date: 2026-09-11
type: post
tags:
    - Mathematics
    - Problem solving
---
# Constant-Coefficient Discrete Diffusion

## Infinite Lattice

Consider the discrete diffusion equation

{{< math >}}

\[
\frac{d}{dt}u_n(t)
=
u_{n+1}(t)+u_{n-1}(t)-2u_n(t),
\qquad n\in\mathbb{Z}.
\]

{{< /math >}}

with initial condition

{{< math >}}

\[
u_n(0)
=
\delta_{n0}
=
\begin{cases}
1, & n=0,\\
0, & n\neq 0.
\end{cases}
\]

{{< /math >}}

Here, {{< math >}}\(u_n(t)\){{< /math >}} represents the density or concentration at lattice site {{< math >}}\(n\){{< /math >}} at time {{< math >}}\(t\){{< /math >}}.

Define

{{< math >}}

\[
\mathbf{u}(t)
=
(\ldots,u_{-1}(t),u_0(t),u_1(t),\ldots)^T.
\]

{{< /math >}}

Then the infinite system can be written as

{{< math >}}

\[
\mathbf{u}'(t)
=
A\mathbf{u}(t),
\]

{{< /math >}}

where the discrete Laplacian operator {{< math >}}\(A\){{< /math >}} is defined componentwise by

{{< math >}}

\[
(A\mathbf{v})_n
=
v_{n+1}+v_{n-1}-2v_n.
\]

{{< /math >}}

---

### Separated Solutions

Assume a separated solution of the form

{{< math >}}

\[
\mathbf{u}(t)
=
c(t)\mathbf{v},
\]

{{< /math >}}

where {{< math >}}\(\mathbf{v}\){{< /math >}} is a spatial profile that is independent of time, while {{< math >}}\(c(t)\){{< /math >}} describes how its magnitude changes with time.

Substituting into

{{< math >}}

\[
\mathbf{u}'(t)
=
A\mathbf{u}(t)
\]

{{< /math >}}

gives

{{< math >}}

\[
c'(t)\mathbf{v}
=
c(t)A\mathbf{v}.
\]

{{< /math >}}

For the spatial profile {{< math >}}\(\mathbf{v}\){{< /math >}} to remain fixed as time changes, {{< math >}}\(A\mathbf{v}\){{< /math >}} must be proportional to {{< math >}}\(\mathbf{v}\){{< /math >}}. Therefore,

{{< math >}}

\[
A\mathbf{v}
=
\lambda\mathbf{v}.
\]

{{< /math >}}

Thus, the spatial part must satisfy an eigenvalue equation.

Componentwise,

{{< math >}}

\[
v_{n+1}+v_{n-1}-2v_n
=
\lambda v_n.
\]

{{< /math >}}

Equivalently,

{{< math >}}

\[
v_{n+1}
-
(2+\lambda)v_n
+
v_{n-1}
=
0.
\]

{{< /math >}}

---

### Spatial Modes

To solve the recurrence relation, assume

{{< math >}}

\[
v_n=r^n.
\]

{{< /math >}}

Substituting this into the recurrence gives

{{< math >}}

\[
r^{n+1}
-
(2+\lambda)r^n
+
r^{n-1}
=
0.
\]

{{< /math >}}

Dividing by {{< math >}}\(r^{n-1}\){{< /math >}}, we obtain

{{< math >}}

\[
r^2-(2+\lambda)r+1=0.
\]

{{< /math >}}

This is the characteristic equation.

If the roots are {{< math >}}\(r_1\){{< /math >}} and {{< math >}}\(r_2\){{< /math >}}, then their product is

{{< math >}}

\[
r_1r_2=1.
\]

{{< /math >}}

Therefore, the two roots may be written as

{{< math >}}

\[
r
\qquad\text{and}\qquad
r^{-1}.
\]

{{< /math >}}

For distinct roots, the general spatial solution is

{{< math >}}

\[
v_n
=
C_1r^n+C_2r^{-n}.
\]

{{< /math >}}

To obtain bounded oscillatory modes on the entire infinite lattice, we consider

{{< math >}}

\[
|r|=1.
\]

{{< /math >}}

Hence, we write

{{< math >}}

\[
r=e^{i\theta},
\qquad
\theta\in\mathbb{R}.
\]

{{< /math >}}

Then

{{< math >}}

\[
r^n=e^{in\theta},
\qquad
r^{-n}=e^{-in\theta},
\]

{{< /math >}}

and the spatial solution becomes

{{< math >}}

\[
v_n
=
C_1e^{in\theta}
+
C_2e^{-in\theta}.
\]

{{< /math >}}

Since

{{< math >}}

\[
e^{in(\theta+2\pi)}
=
e^{in\theta},
\]

{{< /math >}}

the Fourier modes are periodic in {{< math >}}\(\theta\){{< /math >}} with period {{< math >}}\(2\pi\){{< /math >}}.

Therefore, it is sufficient to consider one interval of length {{< math >}}\(2\pi\){{< /math >}}, for example

{{< math >}}

\[
-\pi\leq\theta\leq\pi.
\]

{{< /math >}}

---

### Eigenvalue as a Function of Theta

Consider one Fourier mode

{{< math >}}

\[
v_n^{(\theta)}
=
e^{in\theta}.
\]

{{< /math >}}

Applying the discrete Laplacian gives

{{< math >}}

\[
\begin{aligned}
v_{n+1}^{(\theta)}
+
v_{n-1}^{(\theta)}
-
2v_n^{(\theta)}
&=
e^{i(n+1)\theta}
+
e^{i(n-1)\theta}
-
2e^{in\theta}
\\
&=
e^{in\theta}
\left(
e^{i\theta}
+
e^{-i\theta}
-
2
\right)
\\
&=
e^{in\theta}
\left(
2\cos\theta-2
\right).
\end{aligned}
\]

{{< /math >}}

Therefore,

{{< math >}}

\[
\boxed{
\lambda(\theta)
=
2\cos\theta-2.
}
\]

{{< /math >}}

Since

{{< math >}}

\[
-1\leq\cos\theta\leq1,
\]

{{< /math >}}

we obtain

{{< math >}}

\[
-4\leq\lambda(\theta)\leq0.
\]

{{< /math >}}

Thus, {{< math >}}\(\theta\){{< /math >}} determines the spatial oscillation of the mode, while {{< math >}}\(\lambda(\theta)\){{< /math >}} determines its rate of change in time.

---

### Time Evolution

Recall that

{{< math >}}

\[
c'(t)\mathbf{v}
=
c(t)A\mathbf{v}.
\]

{{< /math >}}

Using

{{< math >}}

\[
A\mathbf{v}
=
\lambda\mathbf{v},
\]

{{< /math >}}

we obtain

{{< math >}}

\[
c'(t)\mathbf{v}
=
\lambda c(t)\mathbf{v}.
\]

{{< /math >}}

Therefore,

{{< math >}}

\[
c'(t)
=
\lambda c(t).
\]

{{< /math >}}

The solution of this scalar differential equation is

{{< math >}}

\[
c(t)
=
Ce^{\lambda t}.
\]

{{< /math >}}

Since

{{< math >}}

\[
\lambda(\theta)
=
2\cos\theta-2,
\]

{{< /math >}}

the time factor associated with the mode {{< math >}}\(\theta\){{< /math >}} is

{{< math >}}

\[
e^{(2\cos\theta-2)t}.
\]

{{< /math >}}

Hence, a single Fourier mode evolves according to

{{< math >}}

\[
u_n(t)
=
e^{(2\cos\theta-2)t}
v_n^{(\theta)}.
\]

{{< /math >}}

---

### Superposition of Modes

A single Fourier mode cannot satisfy the initial condition

{{< math >}}

\[
u_n(0)
=
\delta_{n0}.
\]

{{< /math >}}

Therefore, many Fourier modes must be combined.

For a discrete collection of parameters {{< math >}}\(\theta_i\){{< /math >}}, we may write

{{< math >}}

\[
u_n(t)
=
\sum_i
C_i
e^{(2\cos\theta_i-2)t}
v_n^{(\theta_i)}.
\]

{{< /math >}}

Here, each value {{< math >}}\(\theta_i\){{< /math >}} corresponds to a different spatial mode, and {{< math >}}\(C_i\){{< /math >}} represents the weight of that mode.

However, in the infinite-lattice problem, {{< math >}}\(\theta\){{< /math >}} varies continuously over the interval

{{< math >}}

\[
[-\pi,\pi].
\]

{{< /math >}}

Divide this interval into {{< math >}}\(N\){{< /math >}} equal pieces.

Since the total length of the interval is {{< math >}}\(2\pi\){{< /math >}}, the width of each piece is

{{< math >}}

\[
\Delta\theta
=
\frac{2\pi}{N}.
\]

{{< /math >}}

We interpret the discrete coefficient {{< math >}}\(C_i\){{< /math >}} as

{{< math >}}

\[
C_i
\approx
C(\theta_i)\Delta\theta,
\]

{{< /math >}}

where {{< math >}}\(C(\theta)\){{< /math >}} represents the coefficient density associated with the Fourier mode corresponding to {{< math >}}\(\theta\){{< /math >}}.

Thus,

{{< math >}}

\[
u_n(t)
\approx
\sum_{i=1}^{N}
C(\theta_i)
e^{(2\cos\theta_i-2)t}
v_n^{(\theta_i)}
\Delta\theta.
\]

{{< /math >}}

This expression has the form of a Riemann sum.

As

{{< math >}}

\[
N\to\infty,
\qquad
\Delta\theta\to0,
\]

{{< /math >}}

the Riemann sum becomes an integral:

{{< math >}}

\[
\boxed{
u_n(t)
=
\int_{-\pi}^{\pi}
C(\theta)
e^{(2\cos\theta-2)t}
v_n^{(\theta)}
\,d\theta.
}
\]

{{< /math >}}

Thus, the integral represents a continuous superposition of all Fourier modes.

Since

{{< math >}}

\[
v_n^{(\theta)}
=
e^{in\theta},
\]

{{< /math >}}

we obtain

{{< math >}}

\[
u_n(t)
=
\int_{-\pi}^{\pi}
C(\theta)
e^{(2\cos\theta-2)t}
e^{in\theta}
\,d\theta.
\]

{{< /math >}}

The remaining problem is to determine the coefficient function {{< math >}}\(C(\theta)\){{< /math >}} from the initial condition.

---

### Fourier Transform

For the sequence {{< math >}}\(\{u_n(t)\}_{n\in\mathbb{Z}}\){{< /math >}}, define the discrete Fourier transform by

{{< math >}}

\[
\widehat{u}(\theta,t)
=
\sum_{n=-\infty}^{\infty}
u_n(t)e^{-in\theta}.
\]

{{< /math >}}

The inverse Fourier transform is

{{< math >}}

\[
u_n(t)
=
\frac{1}{2\pi}
\int_{-\pi}^{\pi}
\widehat{u}(\theta,t)
e^{in\theta}
\,d\theta.
\]

{{< /math >}}

Recall the modal representation

{{< math >}}

\[
u_n(t)
=
\int_{-\pi}^{\pi}
C(\theta)
e^{(2\cos\theta-2)t}
e^{in\theta}
\,d\theta.
\]

{{< /math >}}

Both expressions represent {{< math >}}\(u_n(t)\){{< /math >}} as a continuous superposition of the same Fourier modes {{< math >}}\(e^{in\theta}\){{< /math >}}.

Comparing the coefficients of these modes gives

{{< math >}}

\[
C(\theta)
e^{(2\cos\theta-2)t}
=
\frac{1}{2\pi}
\widehat{u}(\theta,t).
\]

{{< /math >}}

Setting {{< math >}}\(t=0\){{< /math >}}, we obtain

{{< math >}}

\[
C(\theta)
=
\frac{1}{2\pi}
\widehat{u}(\theta,0).
\]

{{< /math >}}

Therefore, the initial condition determines {{< math >}}\(C(\theta)\){{< /math >}} through its Fourier transform.

---

### Applying the Initial Condition

The initial condition is

{{< math >}}

\[
u_n(0)
=
\delta_{n0}.
\]

{{< /math >}}

Its Fourier transform is

{{< math >}}

\[
\begin{aligned}
\widehat{u}(\theta,0)
&=
\sum_{n=-\infty}^{\infty}
u_n(0)e^{-in\theta}
\\
&=
\sum_{n=-\infty}^{\infty}
\delta_{n0}e^{-in\theta}.
\end{aligned}
\]

{{< /math >}}

Since {{< math >}}\(\delta_{n0}=0\){{< /math >}} whenever {{< math >}}\(n\neq0\){{< /math >}}, every term vanishes except the term corresponding to {{< math >}}\(n=0\){{< /math >}}.

Therefore,

{{< math >}}

\[
\widehat{u}(\theta,0)
=
e^{-i(0)\theta}
=
1.
\]

{{< /math >}}

Hence,

{{< math >}}

\[
\boxed{
\widehat{u}(\theta,0)
=
1.
}
\]

{{< /math >}}

It follows that

{{< math >}}

\[
C(\theta)
=
\frac{1}{2\pi}
\widehat{u}(\theta,0)
=
\frac{1}{2\pi}.
\]

{{< /math >}}

Thus,

{{< math >}}

\[
\boxed{
C(\theta)
=
\frac{1}{2\pi}.
}
\]

{{< /math >}}

---

## Solution on the Infinite Lattice

Substituting

{{< math >}}

\[
C(\theta)
=
\frac{1}{2\pi}
\]

{{< /math >}}

into the modal representation gives

{{< math >}}

\[
\boxed{
u_n(t)
=
\frac{1}{2\pi}
\int_{-\pi}^{\pi}
e^{(2\cos\theta-2)t}
e^{in\theta}
\,d\theta.
}
\]

{{< /math >}}

This is the Fourier integral representation of the solution.

Since

{{< math >}}

\[
e^{(2\cos\theta-2)t}
=
e^{-2t}e^{2t\cos\theta},
\]

{{< /math >}}

we may rewrite the solution as

{{< math >}}

\[
u_n(t)
=
\frac{e^{-2t}}{2\pi}
\int_{-\pi}^{\pi}
e^{2t\cos\theta}
e^{in\theta}
\,d\theta.
\]

{{< /math >}}

Using Euler's formula,

{{< math >}}

\[
e^{in\theta}
=
\cos(n\theta)
+
i\sin(n\theta),
\]

{{< /math >}}

we obtain

{{< math >}}

\[
e^{2t\cos\theta}e^{in\theta}
=
e^{2t\cos\theta}\cos(n\theta)
+
i\,e^{2t\cos\theta}\sin(n\theta).
\]

{{< /math >}}

The factor {{< math >}}\(e^{2t\cos\theta}\){{< /math >}} is even in {{< math >}}\(\theta\){{< /math >}}, while {{< math >}}\(\sin(n\theta)\){{< /math >}} is odd in {{< math >}}\(\theta\){{< /math >}}. Therefore,

{{< math >}}

\[
e^{2t\cos\theta}\sin(n\theta)
\]

{{< /math >}}

is an odd function.

Its integral over the symmetric interval {{< math >}}\([-\pi,\pi]\){{< /math >}} is therefore zero:

{{< math >}}

\[
\int_{-\pi}^{\pi}
e^{2t\cos\theta}
\sin(n\theta)
\,d\theta
=
0.
\]

{{< /math >}}

Hence, only the real part remains:

{{< math >}}

\[
u_n(t)
=
\frac{e^{-2t}}{2\pi}
\int_{-\pi}^{\pi}
e^{2t\cos\theta}
\cos(n\theta)
\,d\theta.
\]

{{< /math >}}

The remaining integrand is even, so

{{< math >}}

\[
\int_{-\pi}^{\pi}
e^{2t\cos\theta}
\cos(n\theta)
\,d\theta
=
2
\int_0^\pi
e^{2t\cos\theta}
\cos(n\theta)
\,d\theta.
\]

{{< /math >}}

Therefore,

{{< math >}}

\[
\boxed{
u_n(t)
=
\frac{e^{-2t}}{\pi}
\int_0^\pi
e^{2t\cos\theta}
\cos(n\theta)
\,d\theta.
}
\]

{{< /math >}}

The modified Bessel function of the first kind has the integral representation

{{< math >}}

\[
I_{|n|}(2t)
=
\frac{1}{\pi}
\int_0^\pi
e^{2t\cos\theta}
\cos(n\theta)
\,d\theta.
\]

{{< /math >}}

Therefore,

{{< math >}}

\[
\boxed{
u_n(t)
=
e^{-2t}I_{|n|}(2t).
}
\]

{{< /math >}}

Thus, the solution of the infinite-lattice discrete diffusion problem

{{< math >}}

\[
\frac{d}{dt}u_n(t)
=
u_{n+1}(t)
+
u_{n-1}(t)
-
2u_n(t),
\qquad
u_n(0)=\delta_{n0},
\]

{{< /math >}}

is

{{< math >}}

\[
\boxed{
u_n(t)
=
\frac{1}{2\pi}
\int_{-\pi}^{\pi}
e^{(2\cos\theta-2)t}
e^{in\theta}
\,d\theta
=
e^{-2t}I_{|n|}(2t).
}
\]

{{< /math >}}
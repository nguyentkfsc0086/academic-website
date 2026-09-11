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
\mathbf{u}'(t)=A\mathbf{u}(t),
\]

{{< /math >}}

where the discrete Laplacian operator \(A\) is defined componentwise by

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
\mathbf{u}(t)=c(t)\mathbf{v},
\]

{{< /math >}}

where \(\mathbf{v}\) is independent of time.

Substituting this into

{{< math >}}

\[
\mathbf{u}'(t)=A\mathbf{u}(t)
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

For the spatial profile \(\mathbf{v}\) to remain fixed as time changes, \(A\mathbf{v}\) must be proportional to \(\mathbf{v}\). Therefore,

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
v_{n+1}-(2+\lambda)v_n+v_{n-1}=0.
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
r^{n+1}-(2+\lambda)r^n+r^{n-1}=0.
\]

{{< /math >}}

Dividing by \(r^{n-1}\), we obtain the characteristic equation

{{< math >}}

\[
r^2-(2+\lambda)r+1=0.
\]

{{< /math >}}

If the two roots are \(r_1\) and \(r_2\), then

{{< math >}}

\[
r_1r_2=1.
\]

{{< /math >}}

Therefore, the roots may be written as

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

Thus, we write

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

the modes are periodic in \(\theta\) with period \(2\pi\).

Therefore, it is sufficient to consider

{{< math >}}

\[
-\pi\leq\theta\leq\pi.
\]

{{< /math >}}

---

### Eigenvalue as a Function of \(\theta\)

Consider one Fourier mode

{{< math >}}

\[
v_n^{(\theta)}
=
e^{in\theta}.
\]

{{< /math >}}

Then

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
\lambda(\theta)=2\cos\theta-2.
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

Thus, \(\theta\) determines the spatial oscillation of the mode, while \(\lambda(\theta)\) determines how quickly that mode changes in time.

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

the time factor associated with the mode \(\theta\) is

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

Therefore, many modes must be combined.

For a discrete collection of values

{{< math >}}

\[
\theta_1,\theta_2,\ldots,
\]

{{< /math >}}

we may write

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

However, in the infinite-lattice problem, the parameter \(\theta\) varies continuously over

{{< math >}}

\[
[-\pi,\pi].
\]

{{< /math >}}

Divide this interval into \(N\) equal pieces. The width of each piece is

{{< math >}}

\[
\Delta\theta
=
\frac{2\pi}{N}.
\]

{{< /math >}}

The discrete coefficient \(C_i\) may then be interpreted as

{{< math >}}

\[
C_i
\approx
C(\theta_i)\Delta\theta,
\]

{{< /math >}}

where \(C(\theta)\) represents the coefficient density associated with the mode corresponding to \(\theta\).

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

Since

{{< math >}}

\[
v_n^{(\theta)}
=
e^{in\theta},
\]

{{< /math >}}

this becomes

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

---

### Fourier Transform

For the sequence

{{< math >}}

\[
\{u_n(t)\}_{n\in\mathbb{Z}},
\]

{{< /math >}}

define the discrete Fourier transform by

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

Recall that the modal representation is

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

Comparing the coefficients of the same mode \(e^{in\theta}\), we obtain

{{< math >}}

\[
C(\theta)
e^{(2\cos\theta-2)t}
=
\frac{1}{2\pi}
\widehat{u}(\theta,t).
\]

{{< /math >}}

Setting \(t=0\),

{{< math >}}

\[
C(\theta)
=
\frac{1}{2\pi}
\widehat{u}(\theta,0).
\]

{{< /math >}}

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

Therefore,

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

Since \(\delta_{n0}=0\) for every \(n\neq0\), only the \(n=0\) term remains:

{{< math >}}

\[
\widehat{u}(\theta,0)
=
e^{-i(0)\theta}
=
1.
\]

{{< /math >}}

Thus,

{{< math >}}

\[
\boxed{
\widehat{u}(\theta,0)=1.
}
\]

{{< /math >}}

Therefore,

{{< math >}}

\[
\boxed{
C(\theta)=\frac{1}{2\pi}.
}
\]

{{< /math >}}

---

## Solution on the Infinite Lattice

Substituting

{{< math >}}

\[
C(\theta)=\frac{1}{2\pi}
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

we may also write

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

Using

{{< math >}}

\[
e^{in\theta}
=
\cos(n\theta)
+
i\sin(n\theta),
\]

{{< /math >}}

the imaginary part is odd in \(\theta\) and integrates to zero over the symmetric interval \([-\pi,\pi]\).

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

Hence,

{{< math >}}

\[
\boxed{
u_n(t)
=
e^{-2t}I_{|n|}(2t).
}
\]

{{< /math >}}

Therefore, the solution of the infinite-lattice discrete diffusion problem

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
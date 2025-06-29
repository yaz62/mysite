+++
title = "Prove That Meridians Are Geodesics With LLMs"
date = 2025-06-27
draft = false
tags = ["differential geometry", "meridian", "geodesic", "covariant parallel", "chatgpt", "claude"]
+++

I've learned bits of differential geometry over the years, and I always use Theodore Shifrin's notes, 
*Differential Geometry: A First Course in Curves and Surfaces*, as my textbook. Recently, I decided to
pick it back up just for fun. 

In Chapter 2, after reading about Clairaut's relation and trying to get an intuitive picture of it, it occurred 
to me that the meridians of a surface of revolution should always be geodesics. This makes sense because the "terrain" 
is symmetrical about the meridian, so if you are walking along the meridian, you are not going either left or right but straight. 
But to show this formally, we need to use the mathematical definition of a geodesic, and I'll use the one from the 
notes:

**Definition.** We say a parametrized curve $\alpha$ in a surface M is a geodesic if its tangent vector is parallel along the curve, 
i.e., if $\nabla_{\alpha^\prime}\alpha^\prime=0.$

A surface of revolution can generally be parametrized as:
$$
    x(u, v) = \big(f(u)\cos v, f(u)\sin v, g(u)\big)
$$
where $f$ and $g$ are two arbitrary functions describing the curve that generates the surface by revolution. Then 
a meridian is simply a $u$-curve, namely, a curve that's parametrized only by $u$, at a constant $v=v_0$:
$$
    \alpha(u) = \big(f(u)\cos v_0, f(u)\sin v_0, g(u)\big)
$$
To calculate the surface normal, we first calculate $x_u$ nad $x_v$ to get the two basis vectors for the tangent space:
$$
\begin{align\*}
    x_u &= \big(f^\prime(u)\cos v, f^\prime(u)\sin v, g^\prime(u)\big) \\\\\[1.5ex]
    x_v &= \big(-f(u)\sin v, f(u)\cos v, 0\big)
\end{align\*}
$$
Then take the cross-product:
$$
\begin{align\*}
    \tilde n &= x_u \times x_v \\\\\[1.5ex]
             &= \begin{vmatrix}
                    i & j & k \\\\\\
                    f^\prime(u)\cos v & f^\prime(u)\sin v & g^\prime(u) \\\\\\
                    -f(u)\sin v & f(u)\cos v & 0
                \end{vmatrix} \\\\\[1.5ex]
             &= \big(-fg^\prime\cos v, -fg^\prime\sin v, f^\prime f\cos^2v + f^\prime f\sin^2v\big) \\\\\[1.5ex]
             &= f(-g^\prime\cos v, -g^\prime\sin v, f^\prime)
\end{align\*}
$$
The normalized surface normal is therefore:
$$
\begin{align\*}
    n &= \frac{\tilde n}{\lVert \tilde n \rVert} 
      = \frac{f(-g^\prime\cos v, -g^\prime\sin v, f^\prime)}{\sqrt{f^2(g^{\prime 2} + f^{\prime 2})}} \\\\\[1.5ex]
      &= \frac{(-g^\prime\cos v, -g^\prime\sin v, f^\prime)}{\sqrt{(g^{\prime 2} + f^{\prime 2})}}
\end{align\*}
$$

The directional derivative of the tangent vector in the direction of the tangent vector is:
$$
    D_{\alpha^\prime(u)} \alpha^\prime(u) = \alpha^{\prime\prime}(u)
$$

Also, the principal normal vector of the curve is always parallel to the surface normal vector in my mental picture 
of the meridian, which we can check easily.
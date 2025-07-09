+++
title = "Geodesics via the Calculus of Variations"
date = 2025-07-09
draft = false
tags = ["differential geometry", "geodesic", "calculus of variation", "euler-lagrange equation"]
+++

When I explain geodesics to people, I usually use two intuitions:
- Geodesics are the "straight lines" on curved surfaces, and;
- Geodesics minimize distances between two points on curved surfaces.

The **definition** I used in [this post](https://yaz62.github.io/posts/prove-meridians-are-geodesics/) is basically a more precise version of the first intuition, using the tool of parallel transport to define what is considered "straight" on a curved surface. However, for people who study Lagrangian mechanics, a definition based on the second intuition might be more straightforward, as the geodesic is the path that minimizes the action, if we define the action as the Euclidean distance between points.

Consider two points $P$ and $Q$ on a curved space $x$, connected by a curve $\alpha$. A particle moves from $P$ to $Q$ at speed $\lVert\alpha^\prime\rVert$, taking time $T$. The distance functional is defined as the following integral:
$$
    S\[\alpha\] = \int_0^T \lVert\alpha^\prime(t)\rVert \mathrm dt = \int_0^T \sqrt{\alpha^\prime(t) \cdot \alpha^\prime(t)} \mathrm dt 
$$

To make things easier, instead of optimizing the distance functional, I used the following energy functional:
$$
    E\[\alpha\] = \int_0^T \lVert\alpha^\prime(t)\rVert^2 \mathrm dt = \int_0^T \alpha^\prime(t) \cdot \alpha^\prime(t) \mathrm dt 
$$

Seemingly, this is just a mathematical trick to reduce the workload of applying the chain rule later, and minimizing the norm is equivalent as minimizing the squared. However, later we will see that this is not as innocent as it seems. Parametrize the curve with surface parameters $u$ and $v$, we have:
$$
    \alpha(t) = x\big(u(t), v(t)\big)
$$

Now we can proceed to expand the energy functional:
$$
\begin{align\*}
    E\[\alpha\] &= \int_0^T \alpha'(t) \cdot \alpha'(t) \mathrm dt \\\\\[1.5ex]
    &= \int_0^T \frac{\mathrm d}{\mathrm dt}x\big(u(t), v(t)\big) \cdot \frac{\mathrm d}{\mathrm dt}x\big(u(t), v(t)\big) \mathrm dt \\\\\[1.5ex]
    &= \int_0^T x'\big(u, v, u', v'\big) \cdot x'\big(u, v, u', v'\big) \mathrm dt
\end{align\*}
$$

It is essential to realize that $x'$ is function of not only $u$ and $v$, but also $u'$ and $v'$. Explicitly:
$$
    x' = \frac{\mathrm d}{\mathrm dt}x(u, v) = u' x_u + v' x_v
$$
So, later when I introduce variations $\delta \alpha$ to the curve, this will not only result in the coordinates $[u(t), v(t)]$ of the curve, but also the tangent $[u'(t), v'(t)]$. 
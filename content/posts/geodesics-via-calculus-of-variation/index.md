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
    E\[\alpha\] &= \frac{1}{2}\int_0^T \alpha^\prime(t) \cdot \alpha^\prime(t) \mathrm dt \\\\\[1.5ex]
    &= \frac{1}{2}\int_0^T \frac{\mathrm d}{\mathrm dt}x\big(u(t), v(t)\big) \cdot \frac{\mathrm d}{\mathrm dt}x\big(u(t), v(t)\big) \mathrm dt \\\\\[1.5ex]
    &= \frac{1}{2}\int_0^T x^\prime\big(u, v, u^\prime, v^\prime\big) \cdot x^\prime\big(u, v, u^\prime, v^\prime\big) \mathrm dt
\end{align\*}
$$

It is essential to realize that $x^\prime$ is function of not only $u$ and $v$, but also $u^\prime$ and $v^\prime$. Explicitly:
$$
    x^\prime(u, v, u^\prime, v^\prime) = \frac{\mathrm d}{\mathrm dt}x(u, v) = u^\prime x_u + v^\prime x_v
$$

So, when a small variation is introduced to the curve, this will not only result in the coordinates $[u(t), v(t)]$ of the curve, but also the tangent $[u^\prime(t), v^\prime(t)]$. The shortcut to solve the optimization of $E$ is to use the Euler-Lagrange equation:
$$
\begin{align\*}
\begin{cases}
  \displaystyle\ \frac{\partial E}{\partial u} - \frac{\mathrm d}{\mathrm dt}\frac{\partial E}{\partial u^\prime} = 0 \\\\\[3ex]
  \displaystyle\ \frac{\partial E}{\partial v} - \frac{\mathrm d}{\mathrm dt}\frac{\partial E}{\partial v^\prime} = 0
\end{cases}
\end{align\*}
$$

Now if there's a small variation $\delta \alpha$ applied to the curve, the energy functional is perturbed:
$$
\begin{align\*}
    E + \delta E &= \frac{1}{2}\int_0^T (x^\prime+\delta x^\prime) \cdot (x^\prime+\delta x^\prime) \mathrm dt \\\\\[1.5ex]
    &= \frac{1}{2}\int_0^T x^\prime\cdot x^\prime \mathrm dt + \int_0^T x^\prime \cdot \delta x^\prime \mathrm dt + O(\delta x^{\prime 2}) \\\\\[1.5ex]
    &= E + \int_0^T x^\prime \cdot \delta x^\prime \mathrm dt + O(\delta x^{\prime 2})
\end{align\*}
$$

The higher order term $O(\delta x^{\prime 2})$ is omitted, which leads to:
$$
    \delta E = \int_0^T x^\prime \cdot \delta x^\prime \mathrm dt
$$

$\delta x^\prime$ can be expanded the same way as the total differential, and as mentioned before, it's a function of $u$, $v$, $u^\prime$, and $v^\prime$:
$$
\begin{align\*}
    \delta x^\prime &= \frac{\partial x^\prime}{\partial u}\delta u + \frac{\partial x^\prime}{\partial v}\delta v + \frac{\partial x^\prime}{\partial u^\prime}\delta u^\prime + \frac{\partial x^\prime}{\partial v^\prime}\delta v^\prime \\\\\[1.5ex]
    &= (u^\prime x_{uu} + v^\prime x_{uv}) \delta u + (u^\prime x_{uv} + v^\prime x_{vv}) \delta v + x_u \delta u^\prime + x_v \delta v^\prime
\end{align\*}
$$

Plug this back in the integral for the variation of the energy functional:
$$
\begin{align\*}
    \delta E &= \int_0^T \textcolor{blue}{x^\prime} \cdot \textcolor{red}{\delta x^\prime} \mathrm dt \\\\\[1.5ex]
    &= \int_0^T \textcolor{blue}{(u^\prime x_u + v^\prime x_v)} \cdot \textcolor{red}{\Big\\{(u^\prime x_{uu} + v^\prime x_{uv}) \delta u + (u^\prime x_{uv} + v^\prime x_{vv}) \delta v + x_u \delta u^\prime + x_v \delta v^\prime\Big\\}} \mathrm dt \\\\\[1.5ex]
    &= \int_0^T \mathrm dt\ \big(u^{\prime 2}x_u\cdot x_{uu} + u^\prime v^\prime x_u \cdot x_{uv} + u^\prime v^\prime x_v\cdot x_{uu} + v^{\prime 2}x_v\cdot x_{uv}\big)\delta u  \\\\\[1.5ex]
    &\ \ \ \ \ \ \ \ \ + \big(u^{\prime 2}x_u\cdot x_{uv} + u^\prime v^\prime x_u \cdot x_{vv} + u^\prime v^\prime x_v\cdot x_{uv} + v^{\prime 2}x_v\cdot x_{vv}\big)\delta v  \\\\\[1.5ex]
    &\ \ \ \ \ \ \ \ \ + (u^\prime E + v^\prime F)\delta u^\prime + (u^\prime F + v^\prime G)\delta v^\prime
\end{align\*}
$$
where $E$, $F$, and $G$ are dot products of $x_u$ and $x_v$, which are elements in the first fundamental form:
$$
    I = \begin{bmatrix}
        x_u\cdot x_u & x_u\cdot x_v \ \\\\\\
        x_u\cdot x_v & x_v\cdot x_v \ 
    \end{bmatrix}
    = \begin{bmatrix}
        E & F \ \\\\\\
        F & G \ 
    \end{bmatrix}
$$

The next step is to eliminate $\delta u^\prime$ and $\delta v^\prime$ through integration by parts. The idea is:
$$
    \int_0^T f\ \delta u^\prime \mathrm dt = \int_0^T f\ \delta\Big(\frac{\mathrm du}{\mathrm dt}\Big) \mathrm dt = \int_0^T f\ \frac{\mathrm d\delta u}{\mathrm dt} \mathrm dt = f\delta u\big|_0^T - \int_0^T f^\prime\delta u\ \mathrm dt
$$
Because we introduce variations to the curve with the start and end points fixed, so $\delta u(0)=0$ and $\delta u(T)=0$, and the boundary term $f\delta u\big|_0^T=0$. Therefore,
$$
    \int_0^T f\ \delta u^\prime \mathrm dt = - \int_0^T f^\prime\delta u\ \mathrm dt
$$

Apply the the above idea to the $\delta u^\prime$ and $\delta v^\prime$ terms in the integral for $\delta E$:
$$
\begin{align\*}
    \int_0^T \mathrm dt\ (u^\prime E + v^\prime F)\delta u^\prime + (u^\prime F + v^\prime G)\delta v^\prime = -\int_0^T &\mathrm dt\ (u^{\prime\prime} E + v^{\prime\prime} F + u^\prime E^\prime + v^\prime F^\prime)\delta u  \\\\\[1.5ex]
    &+ (u^{\prime\prime} F + v^{\prime\prime} G + u^\prime F^\prime + v^\prime G^\prime)\delta v
\end{align\*}
$$

The derivatives of first fundamental form elements are:
$$
\begin{align\*}
    E^\prime &= 2 x_u \cdot x_u^\prime = 2u^\prime x_u\cdot x_{uu} + 2v^\prime x_u\cdot x_{uv}  \\\\\[1.5ex]
    F^\prime &= x_u \cdot x_v^\prime + x_v \cdot x_u^\prime = u^\prime x_u\cdot x_{uv} + v^\prime x_u\cdot x_{vv} + u^\prime x_v\cdot x_{uu} + v^\prime x_v\cdot x_{uv}  \\\\\[1.5ex]
    G^\prime &= 2 x_v \cdot x_v^\prime = 2u^\prime x_v\cdot x_{uv} + 2v^\prime x_v\cdot x_{vv}
\end{align\*}
$$

So, continue from above:
$$
\begin{align\*}
    &-\int_0^T \mathrm dt\ (u^{\prime\prime} E + v^{\prime\prime} F + \textcolor{red}{u^\prime E^\prime} + \textcolor{blue}{v^\prime F^\prime})\delta u + (u^{\prime\prime} F + v^{\prime\prime} G + \textcolor{blue}{u^\prime F^\prime} + \textcolor{green}{v^\prime G^\prime})\delta v  \\\\\[1.5ex]
    =& -\int_0^T \mathrm dt\ \Big(u^{\prime\prime} E + v^{\prime\prime} F + \textcolor{red}{2u^{\prime 2}x_u\cdot x_{uu}} + \textcolor{red}{2u^\prime v^\prime x_u\cdot x_{uv}}   \\\\\[1.5ex]
    &\ \ \ \ \ \ \ \ \ + \textcolor{blue}{u^\prime v^\prime x_u\cdot x_{uv}} + \textcolor{blue}{v^{\prime 2} x_u\cdot x_{vv}} + \textcolor{blue}{u^\prime v^\prime x_v\cdot x_{uu}} + \textcolor{blue}{v^{\prime 2} x_v\cdot x_{uv}}\Big)\delta u   \\\\\[1.5ex]
    &-\int_0^T\mathrm dt\  \Big(u^{\prime\prime} F + v^{\prime\prime} G + \textcolor{orange}{u^{\prime 2} x_u\cdot x_{uv}} + \textcolor{orange}{u^\prime v^\prime x_u\cdot x_{vv}} + \textcolor{orange}{u^{\prime 2} x_v\cdot x_{uu}} + \textcolor{orange}{u^\prime v^\prime x_v\cdot x_{uv}}    \\\\\[1.5ex]
    &\ \ \ \ \ \ \ \ \ + \textcolor{green}{2u^\prime v^\prime x_v\cdot x_{uv}} + \textcolor{green}{2v^{\prime 2} x_v\cdot x_{vv}}\Big)\delta v
\end{align\*}
$$

Now, plug this back into the integral for $\delta E$ and cancel things out, we get:
$$
\begin{align\*}
    \delta E &= -\int_0^T \mathrm dt\ \big(u^{\prime\prime} E + v^{\prime\prime} F + u^{\prime 2}x_u\cdot x_{uu} + 2u^\prime v^\prime x_u\cdot x_{uv} + v^{\prime 2} x_u\cdot x_{vv}\big)\delta u  \\\\\[1.5ex]
    &\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ + \big(u^{\prime\prime} F + v^{\prime\prime} G + u^{\prime 2}x_v\cdot x_{uu} + 2u^\prime v^\prime x_v \cdot x_{uv} + v^{\prime 2}x_v\cdot x_{vv}\big)\delta v  \\\\\[1.5ex]
    &= -\int_0^T \mathrm dt\ (u^{\prime\prime} x_u + v^{\prime\prime} x_v + u^{\prime 2}x_{uu} + 2u^\prime v^\prime x_{uv} + v^{\prime 2} x_{vv}) \cdot x_u \ \delta u  \\\\\[1.5ex]
    &\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ + (u^{\prime\prime} x_u + v^{\prime\prime} x_v + u^{\prime 2}x_{uu} + 2u^\prime v^\prime x_{uv} + v^{\prime 2}x_{vv})\cdot x_v\ \delta v  \\\\\[1.5ex]
\end{align\*}
$$

To further simplify the expression, note that:
$$
\begin{align\*}
    & u^{\prime\prime} x_u + v^{\prime\prime} x_v + u^{\prime 2}x_{uu} + 2u^\prime v^\prime x_{uv} + v^{\prime 2}x_{vv}  \\\\\[1.5ex]
    =\ & u^{\prime\prime} x_u + v^{\prime\prime} x_v + u^\prime \big(u^\prime x_{uu} + v^\prime x_{uv}\big) + v^\prime\big(u^\prime x_{uv} + v^\prime x_{vv}\big)  \\\\\[1.5ex]
    =\ & u^{\prime\prime} x_u + v^{\prime\prime} x_v + u^\prime x_u^\prime + v^\prime x_v^\prime \\\\\[1.5ex]
    =\ & (u^\prime x_u + v^\prime x_v)^\prime \\\\\[1.5ex]
    =\ & x^{\prime\prime}
\end{align\*}
$$

So,
$$
    \delta E = -\int_0^T\ (x^{\prime\prime}\cdot x_u\delta u +  x^{\prime\prime}\cdot x_v\delta v)\ \mathrm dt
$$

As in any optimization problem, the minimum of $E$ is found when the variation $\delta E=0$. This leads to the following equations:
$$
\begin{cases}
  \ x^{\prime\prime}\cdot x_u = 0 \\\\
  \ x^{\prime\prime}\cdot x_v = 0
\end{cases}
$$

Since $x_u$ and $x_v$ are the two (not necessarily orthogonal) basis vectors of the tangent plane, the above equations suggest that:
$$
    \big(x^{\prime\prime}\big)^\parallel = \big(D_{\alpha^\prime}\alpha^\prime\big)^\parallel = \nabla_{\alpha^\prime}\alpha^\prime=0
$$
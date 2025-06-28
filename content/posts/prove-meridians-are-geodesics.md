+++
title = "Prove That Meridians Are Geodescis With LLMs"
date = 2025-06-27
draft = false
tags = ["differential geometry", "meridian", "geodesic", "covariant parallel", "chatgpt", "claude"]
+++

I've learned bits of differential geometry over the years, and I always use Theodore Shifrin's notes, 
*Differential Geometry: A First Course in Curves and Surfaces*, as the textbook. Recently I've decided to
pick it back up just for fun. 

In Chapter 2, after reading about Clairaut's relation and trying to get an intuitive picture of it, it came 
to me that the meridians of a surface of revolution should be always geodesics. This makes sense because ...

A surface of revolution can be generally parametrized as:
$$
x(u, v) = (f(u)\cos v, f(u)\sin v, g(u))
$$
where $f$ and $g$ are two arbitrary functions describing the curve that generates the surface by revolution.

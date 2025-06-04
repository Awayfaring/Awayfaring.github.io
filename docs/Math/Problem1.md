---
layout: home
title: Feynman Technique 
nav_order: 2
parent: Math
---
# Feynman's Technique

A niche technique for solving certain integrals that involves having the entire integral as a function of a newly created parameter 
. 

Not to be confused with [Feynman's Technique] or [Feynman Parametrization]. In fact this method was originally derived by [Leibniz] 

---
Let's start with a simple example 

Assume we have to solve the following integral.
{% katex display %}
\int_0^1 \frac{x^7-1}{\ln{x}} dx
{% endkatex %}
Traditional methods for this will not work, in fact [Integral Calculator] returns a numerical estimation as it's unable to find a closed form solution.  

---
First we parameterize the function
{% katex display %}
I(\alpha) = \int_0^1 \frac{x^{7\alpha}-1}{\ln{x}} dx
{% endkatex %}
{% katexmm %}
We can see that our initial integral is equal to $I(1)$
{% endkatexmm %}
We take the derivative of both sides with respect to the parameter.
{% katex display %}
I'(\alpha) = \frac{\partial I}{\partial \alpha}\int_0^1 \frac{x^{7\alpha}-1}{\ln{x}} dx
{% endkatex %}
Since the bounds of the integral are **not** functions of our parameter, *and* our function **is** continuous within said bound. We are able to "flip" the order of integration and differentiation
{% katexmm %}
$$\begin{aligned}
    I'(\alpha) &= \int_0^1  \frac{\partial I}{\partial \alpha} \ \left(\frac{x^{7\alpha}-1}{\ln{x}}\right) \ dx \\
    &= \int_0^1 \frac{7x^{7\alpha}\ln{x}}{\ln{x}} dx \\
    &= \int_0^1 7x^{7\alpha} dx \\
    &= \left. \frac{7x^{7\alpha + 1}}{7\alpha + 1}\right|_0^1 \\
    &= \frac{7}{7\alpha + 1}
\end{aligned}$$
{% endkatexmm %}

---
If we remember the fundamental theorem of calculus we know that 
{% katexmm %}
$$ F(b) - F(a) = \int_a^b f(x) dx \qquad \text{where  }\ f(x) = F'(x) $$
Applying this to out context we can write that 
$$ I(1) - I(0) = \int_0^1 I'(\alpha) \ d\alpha$$
From our original parameterization we see that if we set $\alpha = 0$ 
$$I(0) = \int_0^1 \frac{x^{0}-1}{\ln{x}}=0$$
Therefore our equation becomes
$$\begin{aligned}
    I(1) &= \int_0^1 I'(\alpha) \ d\alpha \\
    &= \int_0^1 \frac{7}{7\alpha + 1} \ d\alpha \\
    &= \left.\ln{(7\alpha + 1)} \right|_0^1 \\
    &= \ln{8} - \ln{1} \\
    &= \boxed{\ln{8}} 
\end{aligned}$$
{% endkatexmm %}

---
{% katexmm %}
Thus we arrive at our final answer
$$\int_0^1 \frac{x^7-1}{\ln{x}}\ dx = \ln{8}$$
{% endkatexmm %}

___
[Feynman's Technique]: https://en.wikipedia.org/wiki/Learning_by_teaching
[Feynman Parametrization]: https://en.wikipedia.org/wiki/Feynman_parametrization
[Integral Calculator]: https://www.integral-calculator.com/
[Leibniz]: https://en.wikipedia.org/wiki/Leibniz_integral_rule
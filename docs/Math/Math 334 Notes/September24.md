---
layout: home
title: September 24 Notes
nav_order: 2
parent: Math 334 Notes

---
# Topology of Euclidean Space

---
## Balls
This lecture introduces us to Topology, we start by defining the **Open Ball**
{% katexmm %}
Let 
$$a \in \mathbb{R}^n$$
$$r \in \mathbb{R}, \ r \geq 0$$
We can define a **Ball** centered at $a$ with radius $r$ as 
$$B(r,a)$$
More formally (and since the ball is open)
$$B(r,a) = \{x: \lvert x - a\rvert < r\}$$
Building off this idea we can represent a closed ball
$$\overline B(r,a) = \{x: \lvert x - a\rvert \leq r\}$$

if $n = 1$ space, the open and closed balls represet the interval
$$(a - r, a + r)$$ 
and 
$$[a - r, a + r]$$ 
respectively.
{% endkatexmm %}

---
## Bounded Set
{% katexmm %}
We can use our previously defined balls to define certain types of sets.
In this case we can call a set $S \subseteq \mathbb{R}^n$ bounded if
$$\exists R \in \mathbb{R} \text{ such that } R > 0 \text{ and } S \subseteq B(R,0)$$
Notice that it doesnt matter if we use a closed or open ball. 
If there was a case where
$$S \nsubseteq B(R,0), S \subseteq \overline B(R,0)$$
then
$$\exists \delta > 0, \  S \subseteq B(R + \delta, 0)$$

Basically there is some $\delta > 0$ such that if I were to increase $R$ by said $\delta$ then $S \subseteq B(R',0)$ where $R' = R + \delta$

As a side note we should recognize that the complement of this set would be unbounded while we're at it, I'll formalize the definition of the complement as 
$$S^c = \{x : x \notin S\} = \mathbb{R}^n \setminus S$$
{% endkatexmm %}
___

## Interior

{% katexmm %}
Given a set
$$S \subset \mathbb{R}^n$$
$x$ in an **interior** point of $S$ if for some $r > 0$, the **Ball** centered at $x$ with $r$ radius is a subset of $S$. 
$$B(r,x) \subset S$$ 
We notate this as 
$$\boxed{S^{\text{int}}}$$  

---
## Exterior 
We can define **exterior** points in a similar way. \\
Given a set 
$$S \subset \mathbb{R}^n$$
$x$ is an exterior point of $S$ if for some $r > 0$, the Ball centered at $x$ with $r$ radius has no overlap with $S$ 
$$B(r,x) \cap S = \emptyset$$
We can take this a slight step further, if our Ball has no overlap with $S$ then that means it's a subset of the complement, $S^c$.
$$B(r,x) \subset S^c$$
which means that it's the "interior" of $S^c$, the complement of $S$. \\
As such we can notate this as
$$\boxed{(S^c)^{\text{int}}}$$

---
## Boundary
As the name suggests the **boundary** points for $S$ exist "between" the sets of **interior** and **exterior** points of $S$.
Formally, given a set $$S \subset \mathbb{R}^n$$
$x$ is a boundary point of $S$ if for all $r > 0$ the Ball centered at $x$ with radius $r$ has overlap with both $S$ and $S^c$
$$B(r,x) \cap S \neq \emptyset$$
$$B(r,x) \cap S^c \neq \emptyset$$
We can denote the set of **boundary** points of $S$ as $$\boxed{\partial S}$$


---
## Circling Back 
With out new knowledge of **inteior**, **exterior**, and **boundary**.
We can define Open and Closed Sets in a new manner
\\
An **Open** set is a set $S$ where
$$ S = S^\text{int}$$
A **Closed** set is a set $S$ where
$$S = S^\text{int} \cup \delta S$$

---
## Important Takeaways 

Given a set $$S \subset \mathbb{R}^n$$ 
Any point $x \in \mathbb{R}^n$ is in either the **interior**, **exterior** or **boundary**. We can write this formally as 
$$\forall x \in \mathbb{R}^n, x \in S^\text{int} \uplus (S^c)^\text{int} \uplus \delta S$$
{% endkatexmm %}

--- 


## Visual

Visual representation of interior, exterior and boundary.

![](/assets/images/Math334/Interior-Exterior-Boundary.png)
---
title: "HoTT Math 1: Elementary group theory"
date: 2013-06-23 18:00:38
permalink: /archives/1438/
published: true
topics: [type-theory]
tags: [Homotopy Type Theory]
---
This is the first in a series of posts on doing mathematics in Homotopy Type Theory (HoTT). Various conventions and notations are explained in [the preamble]({{ site.baseurl }}{% post_url 2013-06-23-hott-math-series %}); there are no additional prerequisites for this post. 

* * *

A group is a _set_ $$G$$ equipped with a constant $$e:1 \to G$$, a unary operation $$\square^{-1}:G \to G$$ and a binary operation $${\square\cdot\square}:G \times G \to G$$ that satisfy the usual axioms. In HoTT the group axioms must be motivated, so the group $$G$$ comes with three more components:
^
$$\begin{aligned}
{\small\fbox{\(\phantom{Q}\)associativity\(\phantom{Q}\)}} &:
\prod_{x,y,z:G} (x\cdot(y\cdot z) =_G (x\cdot y)\cdot z) \\ {\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}} &:
\prod_{x:G} (x \cdot e =_G x) \times \prod_{x:G}(e \cdot x = x)\\ {\small\fbox{\(\phantom{Q}\)inverse\(\phantom{Q}\)}} &:
\prod_{x:G} (e = x^{-1} \cdot x) \times \prod_{x:G} (e =_G x \cdot x^{-1}) \\
\end{aligned}$$
^
The axioms are concrete objects in proof-relevant mathematics! The last two axioms are actually the conjunction of two axioms since conjunction in HoTT correspond to products. It's conceptually convenient to package them together and use $${\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_1$$ and $${\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_2$$ for the two conjuncts obtained by applying the projections. In fact, it makes sense to pack all of these into one
^
$${\small\fbox{\(\phantom{Q}\)group\(\phantom{Q}\)}} :
\equiv{\small\fbox{\(\phantom{Q}\)associativity\(\phantom{Q}\)}}\times{\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}\times{\small\fbox{\(\phantom{Q}\)inverse\(\phantom{Q}\)}}$$
^
(but, for the sake of clarity, it is best to refrain from using things like $${\small\fbox{\(\phantom{Q}\)group\(\phantom{Q}\)}}_1$$ for $${\small\fbox{\(\phantom{Q}\)associativity\(\phantom{Q}\)}}$$). 

The axioms types above are parametrized by $$G:\mathsf{Set}$$ and the three components $$e$$, $$\square^{-1}$$, $$\square\cdot\square$$, so one can form the type of all groups:
^
$$\mathsf{Grp}:\equiv\sum_{\substack{G:\mathsf{Set}\\{e}:1\to G\\{\square^{-1}}:G\to G\\{\square\cdot\square}:G\times G \to G}} {\small\fbox{\(\phantom{Q}\)group\(\phantom{Q}\)}}(G,e,\square^{-1},\square\cdot\square).$$
^
This level of formalism is cumbersome and since it is perfectly clear what the type $$\mathsf{Grp}$$ is from the narrative description, it is best to avoid it. The only difference from classical mathematics is that the axioms are given as concrete objects rather than abstract statements. 

Familiar identities, for example the fact that $$e$$ is its own inverse, can be obtained by combining the group axioms. We have a path $${\small\fbox{\(\phantom{Q}\)inverse\(\phantom{Q}\)}}_1(e):e =_G e^{-1}\cdot e$$ and another path $${\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_1(e^{-1}):e^{-1}\cdot e =_G e^{-1}$$. Concatenating these two paths yields the desired path $${\small\fbox{\(\phantom{Q}\)inverse\(\phantom{Q}\)}}_1(e)\cdot{\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_1(e^{-1}):e^{-1} =_G e.
$$
^
There are other ways to see this, for example, symmetric reasoning yields
^
$${\small\fbox{\(\phantom{Q}\)inverse\(\phantom{Q}\)}}_2(e)\cdot{\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_2(e^{-1}):e^{-1} =_G e.$$
^
In general, these two paths are need not be the same but since $$G$$ is a set, i.e., a 0-type, there is at most one path in $$e^{-1} =_G e$$ and therefore the two paths above must be the same. 

Let's try something a tad more complicated — [an old favorite](http://mathoverflow.net/a/11379) — the uniqueness of identity elements. To say that $$u:G$$ is a left identity element means exhibiting an element of the type 
^
$$\prod_{x:G} (u \cdot x =_G x);$$
^
 so $${\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_1$$ shows that $$e$$ is an identity element. Similarly, $${\small\fbox{\(\phantom{Q}\)identity\(\phantom{Q}\)}}_2$$ shows that $$e$$ is a right identity element. Classically, we know that if $$u$$ is a left identity and if $$v$$ is a right identity then we must have $$u = v$$. In HoTT, this corresponds to exhibiting an element of type 
^
$$\mathsf{lrid}:\equiv\prod_{u,v:G} \Big(\prod_{x:G} (u \cdot x =_G x) \times \prod_{y:G} (y \cdot v =_G y) \to (u =_G v)\Big).$$
^


To prove this, let's fix $$u,v:G$$. Given $$p:\prod_{x:G} (u \cdot x =_G x)$$ and $$q:\prod_{y:G} (y \cdot v =_G y)$$ we have paths 
^
$$\begin{aligned} p(v) &: u \cdot v =_G v, & q(u)&:u \cdot v =_G u,\end{aligned}$$
^
 and therefore a path 
^
$$q(u)^{-1} \cdot p(v): u =_G v.$$
^
 The classical proof would end here but to get the desired element of $$\mathsf{lrid}$$, we need to wrap things up as follows. Since the final path was obtained uniformly from $$p,q$$, we have an element 
^
$$\lambda p,q.q(u)^{-1} \cdot p(v):\prod_{x:G} (u \cdot x =_G x) \times \prod_{y:G} (y \cdot v =_G y) \to (u =_G v)$$
^
and we can then unfix $$u,v:G$$ to obtain the desired element 
^
$$\lambda u,v.\lambda p,q . q(u)^{-1} \cdot p(v):\mathsf{lrid}.$$
^
I slightly abused $$\lambda$$-notation in the argument above but the idea was only to give a hint how the argument could be formalized. In fact, we did not need to worry about this at all. Since $$G$$ is a set, there is at most one path in $$u =_G v$$ and thus there is also at most one element in 
^
$$\prod_{x:G} (u \cdot x =_G x) \times \prod_{y:G} (y \cdot v =_G y) \to (u =_G v)$$
^
by function extensionality (§4.9). Therefore, the unique choice principle (§3.9) applies to give the desired element of $$\mathsf{lrid}$$. In fact, $$\mathsf{lrid}$$ also has exactly one element by function extensionality. 

In the end, the classical proof of uniqueness of inverses was sufficient and unambiguous. In fact, the same is true for essentially all similar facts of elementary algebra. This is good for multiple reasons but most importantly this means that doing math in HoTT does not involve getting caught up in elementary stuff like this: you can invoke $$\mathsf{lrid}$$ any time without referencing a particular proof since the proof is unique. There is one important caveat: 

**It is very important that the carrier type of a group is a set!**

I fell into this trap when I asked [this MathOverflow question](http://mathoverflow.net/q/134449). It is very tempting to think that the loop space $$\Omega(A,x) :\equiv(x =_A x)$$ is a group for every $$x:A$$. This is only true if $$A$$ is a 1-type. Otherwise the carrier of $$\Omega(A,x)$$ is not necessarily a 0-type, the uniqueness of paths is lost, $$\mathsf{lrid}$$ can have many different proofs, which are all relevant and must not be forgotten! 

* * *

In conclusion, elementary group theory works fine in HoTT. The general feel is a bit different but it's more fun than cumbersome to see how the axioms work in relevant mathematics. The same is true for much of elementary algebra and, ultimately, proof relevance is never cumbersome since proofs are almost always unique. It is important to remember that the carrier of an algebraic structure must always be a set for this to work! 

In the next installment of HoTT Math, we will continue with elementary field theory which presents an additional difficulty since we must handle the fact that multiplicative inverses do not always exist...

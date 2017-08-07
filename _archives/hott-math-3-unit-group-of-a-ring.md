---
title: "HoTT Math 3: Unit group of a ring"
date: 2013-07-14 20:30:01
permalink: /archives/1488/
published: true
topics: [type-theory]
tags: [Homotopy Type Theory]
---
In this installment of [HoTT Math]({{ site.baseurl }}{% post_url 2013-06-23-hott-math-series %}), we are taking one more step toward elementary field theory by exploring the unit group of a ring.

* * *

A commutative (unital) ring is a set $$R$$ with two constants $$\mathsf{O},\mathsf{I}:1\to R$$, one unary operation $${-\square}:R \to R$$, two binary operations $${\square+\square},{\square\cdot\square}:R \times R \to R$$ along with the usual axioms: $${\small\fbox{\(\phantom{b}\)group\(\phantom{q}\)}}(\mathsf{O},-\square,\square+\square)$$, $${\small\fbox{\(\phantom{b}\)monoid\(\phantom{q}\)}}(\mathsf{I},{\square\cdot\square})$$,
^
$${\small\fbox{\(\phantom{b}\)distributivity\(\phantom{q}\)}}({\square+\square},{\square\cdot\square}) : \prod_{x,y,z:R} ((x+y)\cdot z =_R x \cdot z + y \cdot z) \times \prod_{x,y,z:R} (x\cdot(y+z) =_R x \cdot y+x \cdot z),$$
^
and
^
$${\small\fbox{\(\phantom{b}\)commutativity\(\phantom{q}\)}}({\square\cdot\square}) : \prod_{x,y:R} (x \cdot y =_R y \cdot x).$$
^
Commutativity of addition can be derived as usual using the fact that
^
$$x+(x+y)+y =_R (x+y)\cdot(\mathsf{I}+\mathsf{I}) =_R x + (y + x) + y.$$
^
If you want to test your path manipulation skills, you can try to write down the resulting term for
^
$${\small\fbox{\(\phantom{b}\)commutativity\(\phantom{q}\)}}({\square+\square}) : \prod_{x,y:R} (x + y =_R y+x).$$
^
However, as we discussed last time, this is not necessary since the proof is ultimately not relevant when the carrier of an algebra is a set.

Reading off the usual definition of unit, we obtain the type
^
$$\operatorname{\mathsf{unit}}(x) :\equiv\sum_{y:R} (x\cdot y =_R \mathsf{I}).$$
^
Elements of type $$\operatorname{\mathsf{unit}}(x)$$ are pairs $$(y,p)$$, where $$y:R$$ and $$p: x \cdot y =_R \mathsf{I}$$. Because $$R$$ is a set and inverses are unique, there is always at most one such $$(y,p)$$, which means that $$\operatorname{\mathsf{unit}}(x)$$ is a proposition. Therefore, we can comprehend the set of units: 
^
$$R^\times :\equiv\set{x:R \mid \operatorname{\mathsf{unit}}(x)} :\equiv\sum_{x:R} \operatorname{\mathsf{unit}}(x).$$
^
(Subset comprehension is discussed in §3.5 of the book.) Technically, elements of $$R^\times$$ are triples $$(x,y,p)$$ where $$x,y:R$$ and $$p:(x \cdot y =_R \mathsf{I})$$. Thus $$R^\times$$ is not merely a subset of $$R$$ but each element of $$R^\times$$ comes equipped with a justification for being in $$R^\times$$. Since for each $$x:R$$ there is at most one $$(x,y,p):R^\times$$, we can identify the two without much confusion but the extra coordinates are actually helpful for proving things about $$R^\times$$.

To illustrate this, let's outline the verification that $$R^\times$$ is a group under multiplication. We will view elements of $$R^\times$$ as pairs $$(x,y)$$ but we will forget the path witnessing that $$x \cdot y =_R \mathsf{I}$$. Since we're working with sets, we shouldn't worry about paths anyway.1 To begin, we need to isolate the group operations:

  * First, we see that $$(\mathsf{I},\mathsf{I}):R^\times$$ since we have a path $$\mathsf{I}\cdot\mathsf{I}=_R \mathsf{I}$$ by the identity axiom; this will be our group identity.

  * Next, we see that if $$(x_0,y_0),(x_1,y_1):R^\times$$ then $$(x_0 \cdot x_1,y_1 \cdot y_0):R^\times$$. Indeed, if $$x_0 \cdot y_0 =_R \mathsf{I}$$ and $$x_1 \cdot y_1 =_R \mathsf{I}$$ then 

	$$x_0 \cdot x_1 \cdot y_1 \cdot y_0 =_R x_0 \cdot \mathsf{I}\cdot y_0 =_R x_0 \cdot y_0 =_R \mathsf{I}.$$

	From this, we directly extract our group multiplication $$\square\cdot\square:R^\times \times R^\times \to R^\times$$.

  * Finally, we see that if $$(x,y):R^\times$$ then $$(y,x):R^\times$$. (This is immediate from commutativity but a slightly longer argument shows that this works even without this assumption.) As a result, we get the group inverse $$\square^{-1}:R^\times \to R^\times$$.

To conclude the argument, it suffices to verify that $${\small\fbox{\(\phantom{b}\)group\(\phantom{q}\)}}(R^\times,\square^{-1},\square\cdot\square)$$ is inhabited. Associativity and identity are immediate consequences of $${\small\fbox{\(\phantom{b}\)monoid\(\phantom{q}\)}}(R,\mathsf{I},\square\cdot\square)$$. The tacit path coordinates are handy for inverses: the path $$(x,y)\cdot(y,x) =_{R^\times} (\mathsf{I},\mathsf{I})$$ simply consists of the two implied paths $$x \cdot y =_R \mathsf{I}$$ and $$y \cdot x =_R \mathsf{I}$$!

The key difference between this proof and the classical proof that $$R^\times$$ is a group is the way we used the definition of $$R^\times$$. At each step of the classical proof, we need to invoke the definition of $$R^\times$$ to get the relevant inverses, do the same computations, and then forget the extra information. In the proof-relevant argument, the subset $$R^\times$$ incorporates its definition and the relevant inverses are already there to be used in computations. To keep the argument from involving too many (ultimately irrelevant) path computations, we still forgot one piece of the definition of $$R^\times$$ in the outline above. This kind of selective unraveling can be useful since formal definitions can rapidly become unwieldy. We did end up invoking the path coordinates at the very end to verify the identity axiom. However, we didn't really need the paths themselves, we just needed to remember that elements $$(x,y)$$ aren't arbitrary pairs, they are pairs such that $$x \cdot y =_R \mathsf{I}$$. This is what the seemingly irrelevant path coordinate does, the relevant data is not the path itself, it is the type $$x \cdot y =_R \mathsf{I}$$ of the path that matters.

* * *

The lesson is that while proof-relevant mathematics does force you to carry extra baggage, that baggage is actually handy. Moreover, you can always manage the burden by selectively unraveling the contents of the baggage. In fact, you also carry this baggage when doing classical mathematics except that you conceal the baggage in your memory, recalling each item as you need it. The problem with this strategy is that it's easy to forget things if you are not careful. Proof-relevant mathematics forces you to keep track of everything!

* * *

### Post Scriptum

In the comments, Toby Bartels pointed out that the argument above contains a major type-theoretic _faux pas_: using type declarations as propositions. The cause of this is the deliberate omission of the path coordinate which leads to phrases like "we see that $$(\mathsf{I},\mathsf{I}):R^\times$$ since [...]" and "we see that if $$(x,y):R^\times$$ then $$(y,x):R^\times$$." The problem is that type declarations are either correct or not (and this is decidable!) but not true or false. Indeed, true and false are both values that can be used but correct and incorrect are not — there is no value in being incorrect! This may seem like a subtle difference but it is actually a very important one in type theory since there is little other separation of syntax and semantics.

Below, I produced three more variants of the above argument that avoid the trouble with Version 0 above. The first is simply does not omit the path coordinates. The second uses the membership relation $$\in$$ where the original used an erroneous type declaration. The third is a direct translation of the classical proof, also using the membership relation. To facilitate comparison, I tried to keep the three versions as close as possible to the original. I am curious to know which of the four versions you prefer, or if you have yet another version that you prefer!

* * *

**Version 1.** Let's outline the verification that $$R^\times$$ is a group under multiplication. To begin, we need to isolate the group operations:

* First, $$(\mathsf{I},\mathsf{I},i):R^\times$$ is our group identity where $$i:\mathsf{I}\cdot\mathsf{I}=_R \mathsf{I}$$ is an instance of the identity axiom.

* Next, the group product is defined by $$(x_0,y_0,p_0)\cdot(x_1,y_1,p_1) := (x_0 \cdot x_1,y_1 \cdot y_0,q)$$, where

	$$q:x_0 \cdot x_1 \cdot y_1 \cdot y_0 =_R x_0 \cdot \mathsf{I}\cdot y_0 =_R x_0 \cdot y_0 =_R \mathsf{I}.$$

* Finally, group inverses are defined by $$(x,y,p)^{-1} := (y,x,q)$$, where $$q:y \cdot x =_R x \cdot y =_R \mathsf{I}.$$ (A slightly longer argument shows that this works even without the commutativity assumption.)

To conclude the argument, it suffices to verify that $${\small\fbox{\(\phantom{b}\)group\(\phantom{q}\)}}(R^\times,\square^{-1},\square\cdot\square)$$ is inhabited. Associativity and identity are immediate consequences of $${\small\fbox{\(\phantom{b}\)monoid\(\phantom{q}\)}}(R,\mathsf{I},\square\cdot\square)$$. The path $$(x,y,p)\cdot(y,x,q) =_{R^\times} (\mathsf{I},\mathsf{I},i)$$ is composed of $$p:x \cdot y =_R \mathsf{I}$$, $$q:y \cdot x =_R \mathsf{I}$$, and the paths must match since $$R$$ is a set.

* * *

**Version 2.** Let's outline the verification that $$R^\times$$ is a group under multiplication. By virtue of univalence, there are multiple ways to look at $$R^\times$$. Instead of viewing it as a subset of $$R$$ we can also view it as a subset of $$R \times R$$, namely 
^
$$R^\times = \set{(x,y):R \times R \mid x \cdot y =_R \mathsf{I}} = \sum_{x,y:R} (x \cdot y =_R \mathsf{I}).$$
^
 Thus $$(x,y) \in_{R \times R} R^\times$$ denotes the proposition $$x \cdot y =_R \mathsf{I}.$$ It turns out that this view of $$R^\times$$ will be easier to work with. To begin, we need to isolate the group operations:

* First, we see that $$(\mathsf{I},\mathsf{I}) \in_{R\times R} R^\times$$ since we have a path $$\mathsf{I}\cdot\mathsf{I}=_R \mathsf{I}$$ by the identity axiom; this will be our group identity.

* Next, we see that if $$(x_0,y_0),(x_1,y_1) \in_{R \times R} R^\times$$ then $$(x_0 \cdot x_1,y_1 \cdot y_0) \in_{R \times R} R^\times$$ too. Indeed, if $$x_0 \cdot y_0 =_R \mathsf{I}$$ and $$x_1 \cdot y_1 =_R \mathsf{I}$$ then 

	$$x_0 \cdot x_1 \cdot y_1 \cdot y_0 =_R x_0 \cdot \mathsf{I}\cdot y_0 =_R x_0 \cdot y_0 =_R \mathsf{I}.$$
	
	From this, we directly extract our group multiplication $$\square\cdot\square:R^\times \times R^\times \to R^\times$$.

* Finally, we see that if $$(x,y) \in_{R \times R} R^\times$$ then $$(y,x) \in_{R \times R} R^\times$$ since $$x \cdot y =_R \mathsf{I}$$ implies $$y \cdot x =_R \mathsf{I}$$ by commutativity. (A slightly longer argument shows that this works even for non-commutative rings.) As a result, we get the group inverse $$\square^{-1}:R^\times \to R^\times$$.

To conclude the argument, it suffices to verify that $${\small\fbox{\(\phantom{b}\)group\(\phantom{q}\)}}(R^\times,\square^{-1},\square\cdot\square)$$ is inhabited. Associativity and identity are immediate consequences of $${\small\fbox{\(\phantom{b}\)monoid\(\phantom{q}\)}}(R,\mathsf{I},\square\cdot\square)$$. The path $$(x,y)\cdot(y,x) =_{R^\times} (\mathsf{I},\mathsf{I})$$ is composed of $$x \cdot y =_R \mathsf{I}$$ and $$y \cdot x =_R \mathsf{I}$$, which hold because $$(x,y), (y,x) \in_{R \times R} R^\times$$.

* * *

**Version 3.** Let's outline the verification that $$R^\times$$ is a group under multiplication. Per definition of $$R^\times$$, we will write $$x \in_R R^\times$$ to mean $$\mathsf{unit}(x)$$. To begin, we need to isolate the group operations:

* First, we see that $$\mathsf{I}\in_{R} R^\times$$ since $$\mathsf{I}\cdot\mathsf{I}=_R \mathsf{I}$$ by the identity axiom; this will be our group identity.

* Next, we see that if $$x_0,x_1 \in_{R} R^\times$$ then $$x_0 \cdot x_1 \in_{R} R^\times$$ too. Indeed, since $$\mathsf{unit}(x_0)$$ and $$\mathsf{unit}(x_1)$$ there are $$y_0,y_1:R$$ such that $$x_0 \cdot y_0 =_R \mathsf{I}$$ and $$x_1 \cdot y_1 =_R \mathsf{I}.$$ Then 

  $$x_0 \cdot x_1 \cdot y_1 \cdot y_0 =_R x_0 \cdot \mathsf{I}\cdot y_0 =_R x_0 \cdot y_0 =_R \mathsf{I}$$

  which shows that $$\mathsf{unit}(x_0 \cdot x_1).$$ Thus our group multiplication is (the restriction of) the usual ring multiplication.

* Finally, we see that if $$x \in_{R} R^\times$$ then, by definition of the proposition $$\mathsf{unit}(u)$$, there is a unique $$y:R$$ such that $$x \cdot y =_R \mathsf{I}$$. By commutativity, $$y \cdot x =_R \mathsf{I}$$ which means that $$y \in_{R} R^\times$$ and this $$y$$ is the group inverse of $$x$$.

To conclude the argument, it suffices to verify that $${\small\fbox{\(\phantom{b}\)group\(\phantom{q}\)}}(R^\times,\square^{-1},\square\cdot\square)$$ is inhabited. Associativity and identity are immediate consequences of $${\small\fbox{\(\phantom{b}\)monoid\(\phantom{q}\)}}(R,\mathsf{I},\square\cdot\square)$$. The remaining identity $$x \cdot x^{-1} =_{R^\times} \mathsf{I}$$ follows immediately from the definition of group inverses.

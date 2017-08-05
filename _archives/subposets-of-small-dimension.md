---
title: Subposets of small dimension
date: 2012-02-18 16:18:28
permalink: /archives/656/
published: true
categories: [combinatorics, reverse-math, set-theory]
tags: [Dushnik-Miller Dimension, MathOverflow, Open Problems, Posets, Ramsey Theory]
people: [Denis Hirschfeldt, Justin Tatch Moore, Richard Shore, Tom Goodwillie, Wacław Sierpiński]
bibliography: [HirSho07y, Moo06u]
---
Behind the scenes at Boole's Rings, there was some talk on asking more open questions related to our research. I have three related problems that I would like to share. They are strikingly similar in nature, but they properly belong in three different branches of mathematics: the first problem is about finite combinatorics, the second problem is about reverse mathematics, and the third problem is about infinite combinatorics. To me they are three faces of the same question and I currently don't know how to answer any of them. 

**Three Problems.** _Let $$d \geq 2$$_: 

  1. _Let $$F_d(n)$$ denote the largest number such that every poset of size $$n$$ has a $$d$$-dimensional subposet of size $$F_d(n)$$. What is the asymptotic growth of $$F_d(n)$$_?
  2. _Every (countably) infinite poset has an infinite subposet of dimension at most $$d$$. What is the logical strength of this statement over $$\mathsf{RCA}_0$$_?
  3. _Is there an uncountable poset that has no uncountable $$d$$-dimensional subposet_?

In all three cases, dimension refers to the _Dushnik–Miller dimension_ of the poset $$(P,{\leq})$$, which is the smallest number $$d$$ of linear orders $${\leq_1},\dots,{\leq_d}$$ on the set $$P$$ such that 
^
$$x \leq y \IFF x \leq_1 y \land \cdots \land x \leq_d y$$
^
 for all $$x,y \in P$$. In other words, $${\leq} = {\leq_1} \cap \cdots \cap {\leq_d}$$ when thinking of each relation as a set of ordered pairs. Equivalently, for countable and finite posets, this is the smallest number $$d$$ such that $$(P,{\leq})$$ is embeddable in $$\mathbb{R}^d$$ with the coordinatewise ordering (which explains the name). 

I asked the first question [on MathOveflow in Summer 2010](http://mathoverflow.net/q/29169). Observing that the dimension of a finite poset never exceeds its width, [Tom Goodwillie](https://mathoverflow.net/users/6666/tom-goodwillie) showed that $$F_d(n) \geq \sqrt{dn}$$ for sufficiently large $$n$$. This feels correct for $$d = 2$$, but it doesn't feel optimal for $$d \gt 2$$. (No, I don't have a concrete reason why I feel that way.) Goodwillie's argument (for general $$d$$) runs as follows. Let $$(P,{\leq})$$ be a poset of size $$n$$ and width $$w$$. If $$w \geq \sqrt{dn}$$ then, by definition, $$(P,{\leq})$$ has an antichain of size at least $$\sqrt{dn}$$. Since antichains have dimension at most $$2$$, we're done. If $$w \lt \sqrt{dn}$$ then, by Dilworth's Theorem, $$(P,{\leq})$$ can be partitioned into $$w$$ chains of average size at least $$\sqrt{n/d}$$. If $$n$$ is large enough, the union of the $$d$$ largest chains in this partition forms a $$d$$-dimensional subposet of $$(P,{\leq})$$ with size at least $$\sqrt{dn}$$. My main motivation for asking this question on MathOverflow was to get some inspiration to attack the other two questions. I was hoping that this question had already been answered in the finite combinatorics literature, perhaps in a different guise, but this does not appear to be the case. 

The second question is a ramification of a problem from Denis Hirschfeldt and Richard Shore. In their paper {% include p cite='HirSho07y' %}, they studied the Chain-Antichain Principle ($$\mathsf{CAC}$$), which is the statement that every (countably) infinite poset either has an infinite chain or an infinite antichain. Since chains have dimension $$1$$ and antichains have dimension $$2$$, this immediately implies that every infinite poset has an infinite subposet of dimension at most $$2$$. Hirschfeldt and Shore also studied the Ascending-Descending Sequence Principle ($$\mathsf{ADS}$$), which they show is equivalent to the restriction of $$\mathsf{CAC}$$ to $$2$$-dimensional posets (Theorem 5.3). A straightforward induction shows that $$\mathsf{ADS}$$ is equivalent to the restriction of $$\mathsf{CAC}$$ to $$d$$-dimensional posets for any standard integer $$d \geq 2$$. Although Hirschfeldt and Shore show that $$\mathsf{CAC}$$ is strictly weaker than Ramsey's Theorem for pairs and two colors ($$\mathsf{RT}^2_2$$), it is still an open question whether $$\mathsf{ADS}$$ is strictly weaker than $$\mathsf{CAC}$$. This is where the second problem comes in. If $$\mathsf{ADS}$$ proves that every infinite poset has an infinite subposet of dimension at most $$d$$ then $$\mathsf{ADS}$$ is equivalent to $$\mathsf{CAC}$$, if not then we have a separation of $$\mathsf{CAC}$$ and $$\mathsf{ADS}$$. 

The third question may be a little surprising. In the infinite case, the partition relation $$\aleph_0 \to (\aleph_0)^2_2$$ guarantees that every infinite poset has an infinite subposet of dimension at most $$2$$. Since $$\aleph_1 \to (\aleph_1)^2_2$$ is false, it may seem unlikely that every uncountable poset has an uncountable $$2$$-dimensional subposet. However, Sierpiński's classical argument to prove that $$\aleph_1 \not\to (\aleph_1)^2_2$$ simply shows that there is an uncountable $$2$$-dimensional poset that has no uncountable chains and no uncountable antichains, so this is of little help. Is there an uncountable poset that has no uncountable finite-dimensional subposet? I suspect that such monsters do exist, at least in some models of ZFC, but they are certainly very elusive! 

There is a little side story to this last question. In {% include p cite='Moo06u' %}, Justin Moore showed that, assuming PFA, every uncountable linear ordering contains an isomorphic copy of one of the following five uncountable linear orders: 

  * The ordinal $$\omega_1$$ or its reverse $$\omega_1^*$$
  * An $$\aleph_1$$-dense set of reals $$X$$
  * A Countryman line $$C$$ or its reverse $$C^*$$
  
Sierpiński's counterexample is the comparability graph of the two-dimensional poset obtained by combining $$\omega_1$$ and $$X$$. Similar counterexamples can be made by combining $$\omega_1$$ and $$C$$, or $$X$$ and $$C$$, or all three $$\omega_1$$, $$X$$, and $$C$$. Moore's five element basis guarantees that every finite-dimensional poset contains a combination of this kind (assuming PFA). If every uncountable poset has an uncountable finite-dimensional subposet, then we obtain a nice basis for the class of uncountable posets! 


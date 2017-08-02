---
title: Uncountable perfect graphs
date: 2011-11-06 15:03:58
permalink: /archives/431/
published: true
categories: [combinatorics, set-theory]
tags: [Chordal Graphs, Comparability Graphs, Interval Graphs, Perfect Graphs]
people: [Claude Berge, Fred Galvin, László Lovász, Maria Chudnovsky, Misha Perles, Neil Robertson, Paul Seymour, Richard Rado, Robin Thomas, Ron Aharoni, Stan Wagon, Stevo Todorcevic, Uri Abraham]
bibliography:
  - authors: [U. Abraham]
    year: 1987
    title: "A note on Dilworth's theorem in the infinite case"
    cite: "Order 4, no. 2, 107-125"
    doi: "10.1007/BF00337691"
    mr: "0916489"
    zbl: "0629.06002"
  - authors: [R. Aharoni] 
    year: 1984
    title: "König's duality theorem for infinite bipartite graphs" 
    cite: "J. London Math. Soc. (2) 29, no. 1, 1-12"
    doi: "10.1112/jlms/s2-29.1.1"
    mr: "0734985"
    zbl: "0505.05049"
  - authors: [M. Chudnovsky, N. Robertson, P. Seymour, R. Thomas] 
    year: 2006
    title: "The strong perfect graph theorem"
    cite: "Ann. of Math. (2) 164, no. 1, 51-229"
    doi: "10.4007/annals.2006.164.51"
    mr: "2233847"
    zbl: "1112.05042"
  - authors: [F. G. Dorais]
    year: 2013
    title: "A note on conjectures of F. Galvin and R. Rado" 
    cite: "Canad. Math. Bull. 56, 317-325"
    arxiv: "1110.6563"
    doi: "10.4153/CMB-2011-192-8"
    mr: "3043059"
    zbl: "1315.03077"
  - authors: [L. Lovász] 
    year: 1972
    title: "Normal hypergraphs and the perfect graph conjecture"
    cite: "Discrete Math. 2, no. 3, 253-267"
    doi: "10.1016/0012-365X(72)90006-4"
    mr: "0302480"
    zbl: "0239.05111"
  - authors: [L. Lovász]
    year: 1972
    title: "A characterization of perfect graphs"
    cite: "J. Combinatorial Theory Ser. B 13, 95-98"
    doi: "10.1016/0095-8956(72)90045-7"
    mr: "0309780"
    zbl: "0241.05107"
  - authors: [M. A. Perles] 
    year: 1963
    title: "On Dilworth's theorem in the infinite case"
    cite: "Israel J. Math. 1, 108-109"
    doi: "10.1007/BF02759806"
    mr: "0168497"
    zbl: "0115.01703"
  - authors: [S. Todorcevic]
    year: 1983
    title: "On a conjecture of R. Rado" 
    cite: "J. London Math. Soc. (2) 27, no. 1, 1-8"
    doi: "10.1016/0012-365X(81)90208-9"
    mr: "0620672"
    zbl: "0463.06001"
  - authors: [S. Todorcevic]
    year: 2011
    title: "Combinatorial dichotomies in set theory" 
    cite: "Bull. Symbolic Logic 17, no. 1, 1-72"
    doi: "10.2178/bsl/1294186662"
    mr: "2760116"
    zbl: "1230.03075"
  - authors: [S. Wagon] 
    year: 1978
    title: "Infinite triangulated graphs"
    cite: "Discrete Math. 22, no. 2, 183-189"
    doi: "10.1016/0012-365X(78)90123-1"
    mr: "0523302"
    zbl: "0382.05047"
---
I have been fascinated with perfect graphs for many years. These graphs are very intensely studied in finite combinatorics and new wonderful properties of finite perfect graphs are discovered on a regular basis. However, it is still unclear whether or how these wonderful properties might extend to the countable and uncountable cases. There are several deep questions about this. One of the most interesting question is the consistency of Galvin's Conjecture. I recently wrote a paper on this question (Dorais 2013). Since I believe this and related questions deserve more attention, here is a brief survey of known results around Galvin's Conjecture. 

Perfection has to do with some cardinal characteristics of graphs. Throughout the following, $$G$$ will denote a graph with vertex set $$V$$. If $$X \subseteq V$$, then $$G_X$$ will denote the induced subgraph of $$G$$ with vertex set $$X$$. The four cardinal characteristics of a graph $$G$$ that we need are: 

  * The **clique number** is $$\omega(G) = \sup \set{\card{X}:\text{\(X\) is a clique of \(G\)}}.$$
  * The **stability number** is $$\alpha(G) = \sup\set{\card{X}:\text{\(X\) is an anticlique of \(G\)}}.$$
  * The **chromatic number** $$\chi(G)$$ is the smallest size of a cover of $$V$$ by anticliques.
  * The **clique-cover number** $$\theta(G)$$ is the smallest size of a cover of $$V$$ by cliques.

We have the following obvious inequalities between these cardinals 
^
$$\omega(G) \leq \chi(G) \qquad \alpha(G) \leq \theta(G).$$
^
When does equality hold? 

It's not hard to see that in the case of an odd cycle $$C_{2n+1}$$ with $$n \geq 2$$, we have 
^
$$2 = \omega(C_{2n+1}) \lt \chi(C_{2n+1}) = 3$$
^
and 
^
$$n = \alpha(C_{2n+1}) \lt \theta(C_{2n+1}) = n+1.$$
^
By duality, we also have strict inequalities for the complement $$\overline{C}_{2n+1}$$ of an odd cycle for $$n \geq 2$$. In the 1960's, Claude Berge conjectured that odd cycles and their complements were the minimal finite graphs for which the equalities $$\omega = \chi$$ and $$\alpha = \theta$$ fails. This conjecture became known as the Strong Perfect Graph Conjecture, which remained open for a long time until Maria Chudnovsky, Neil Robertson, Paul Seymour, and Robin Thomas finally proved the conjecture in 2002. Since then, Berge's conjecture has become the Strong Perfect Graph Theorem: 

**Theorem (Lovász 1972, Chudnovsky–Robertson–Seymour–Thomas 2006).** _The following are equivalent for every graph $$G$$:_

  1. _$$G$$ contains no induced copies of the odd cycle $$C_{2n+1}$$ nor its complement $$\overline{C}_{2n+1}$$ for $$n \geq 2$$._
  2. _$$\omega(G_X) = \chi(G_X)$$ for every finite $$X \subseteq V$$._
  3. _$$\alpha(G_X) = \theta(G_X)$$ for every finite $$X \subseteq V$$._
  4. _$$\alpha(G_X)\omega(G_X) \geq \card{X}$$ for every finite $$X \subseteq V$$._

A graph $$G$$ with these properties is called a **perfect graph**. Several classes of graphs are known to be perfect: 

  * Bipartite graphs are perfect.
  * Line graphs of bipartite graphs are perfect.
  * Comparability graphs are perfect.
  * Interval graphs are perfect.
  * Chordal graphs are perfect.

All of these families make sense for infinite graphs. It is natural to ask whether the equalities $$\omega = \chi$$ and $$\alpha = \theta$$ continue to hold in the uncountable case. 

Both equalities are trivial for infinite bipartite graphs. The fact that $$\alpha = \theta$$ for line graphs of bipartite graphs are perfect is known as König's Duality Theorem; it is a deep result of Ron Aharoni (1984) that this result continues to hold in the uncountable case. Unfortunately, the equalities $$\omega = \chi$$ and $$\alpha = \theta$$ can fail very badly for uncountable perfect graphs. For example, Misha Perles (1963) observed that if $$\kappa$$ is an infinite cardinal then the comparability graph of the product ordering $$\kappa\times\kappa$$ has no infinite anticliques but cannot be covered by fewer than $$\kappa$$ cliques. 

There is an alternative way to think of the equalities $$\omega = \chi$$ and $$\alpha = \theta$$ which is much more promising in the uncountable case. 

**Theorem.** _Suppose $$G$$ is a perfect graph and $$k$$ is a positive integer._

  1. _$$\chi(G) \leq k$$ if and only if $$\chi(G_X) \leq k$$ for every $$X \in [V]^{k+1}$$._
  2. _$$\theta(G) \leq k$$ if and only if $$\theta(G_X) \leq k$$ for every $$X \in [V]^{k+1}$$._

_Proof._ The two statements are dual, so I will only prove the first. The forward implication is trivial. For the backward implication, note that the fact that $$\chi(G_X) \leq k$$ for every $$X \in [V]^{k+1}$$ means that $$G$$ has no clique of size $$k+1$$. Therefore, $$\omega(G) \leq k$$ and hence $$\chi(G_X) \leq k$$ for every finite $$X \subseteq V$$. By compactness, it follows that $$\chi(G) \leq k$$. _QED_

It is natural to ask whether this result continues to hold when $$k$$ is replaced by an infinite cardinal $$\kappa$$, and $$k+1$$ is replaced by its cardinal successor $$\kappa^+$$. Since compactness plays a key role in the above proof, this type of generalization is intimately tied with infinitary generalizations of compactness. It is therefore expected that large cardinals will play a role in determining whether such generalizations are plausible or not. Todorcevic [bibcite key=TodorcevicB] is an excellent survey of the type of compactness issues involved here. 

The first case $$\kappa = \aleph_0$$, $$\kappa^+ = \aleph_1$$ is already interesting to look at. This leads us to a pair of conjectures: 

  * In 1968, Fred Galvin conjectured that if $$G$$ is a comparability graph then $$\theta(G) \leq \aleph_0$$ if and only if $$\theta(G_X) \leq \aleph_0$$ for every $$X \in [V]^{\aleph_1}$$.
  * In 1981, Richard Rado conjectured that if $$G$$ is an interval graph then $$\chi(G) \leq \aleph_0$$ if and only if $$\chi(G_X) \leq \aleph_0$$ for every $$X \in [V]^{\aleph_1}$$.

Note that Galvin's Conjecture implies Rado's Conjecture since the complement of an interval graph is a comparability graph. 

It turns out that both conjectures are consistently false. However, Rado's Conjecture was shown to be consistent relative to a supercompact cardinal by Stevo Todorcevic (1983). Recently, I extended Todorcevic's result to the class of all chordal graphs. 

**Theorem (Dorais 2013).** _It is consistent relative to the existence of a supercompact cardinal that_ 
^
$$\chi(G) \leq \aleph_0 \IFF (\forall X \in [V]^{\aleph_1})(\chi(G_X) \leq \aleph_0)$$
^
_holds for every chordal graph $$G$$._

The dual statement for chordal graphs had already been proved by Stan Wagon. 

**Theorem (Wagon 1978).** _If $$G$$ is a chordal graph, then_ 
^
$$\theta(G) \leq \aleph_0 \IFF (\forall X \in [V]^{\aleph_1})(\theta(G_X) \leq \aleph_0).$$
^

In fact, Wagon showed that if $$G$$ is an uncountable chordal graph with $$\alpha(G) \leq \aleph_0$$ and $$\theta(G) \geq \aleph_1$$, then $$G$$ must contain the comparability graph of a Suslin tree. Since Suslin trees have size $$\aleph_1$$, the result follows immediately. However, note that if Suslin's Hypothesis is true then the equality $$\alpha = \theta$$ continues to hold up to $$\aleph_1$$. 

Towards Galvin's conjecture, the best unconditional result is due to Uri Abraham. 

**Theorem (Abraham 1987).** _If $$G$$ is a comparability graph without infinite anticliques, then_ 
^
$$\theta(G) \leq \aleph_0 \IFF (\forall X \in [V]^{\aleph_1})(\theta(G_X) \leq \aleph_0).$$
^

To prove this, Abraham looked at Perles's example $$\omega_1 \times \omega_1$$. He then generalized this example and showed that all graphs $$G$$ without infinite anticliques such that $$\theta(G) \geq \aleph_1$$ must contain an induced subgraph of Perles type. Since graphs of Perles type have size $$\aleph_1$$, the result follows immediately. 

Another step towards Galvin's conjecture is due to Stevo Todorcevic, who showed that Rado's conjecture is equivalent to the restriction of Galvin's conjecture to finite-dimensional comparability graphs. 

**Theorem (Todorcevic 2011).** _It is consistent relative to the existence of a supercompact cardinal that_
^
$$\theta(G) \leq \aleph_0 \IFF (\forall X \in [V]^{\aleph_1})(\theta(G_X) \leq \aleph_0)$$
^
_holds for every finite-dimensional comparability graph $$G$$._

This follows from a remark without proof in [bibcite key=TodorcevicB]. However, I had obtained an independent proof of this fact sometime ago, you can find my proof in (Dorais 2013). 

It appears that not much is known about the dual of Galvin's Conjecture. 

**Theorem (Dorais 2013).** _It is consistent relative to the existence of a supercompact cardinal that_
^
$$\chi(G) \leq \aleph_0 \IFF (\forall X \in [V]^{\aleph_1})(\chi(G_X) \leq \aleph_0)$$
^
_holds for every two-dimensional comparability graph $$G$$._

In fact, I show that the dual of Galvin's Conjecture restricted to two-dimensional comparability graphs is equivalent to Rado's Conjecture. Since trees are two-dimensional, this includes an earlier result of Todorcevic (1983). The consistency of the dual of Galvin's Conjecture restricted to three-dimensional comparability graphs appears to be open. 

It follows from results of (Todorcevic 1983) that Rado's Conjecture is the equivalent to the statement that a comparability graph $$G$$ can be covered by countably many sets $$V_0,V_1,\dots$$ such that each $$G_{V_i}$$ has no infinite clique if and only if this is true for every $$G_X$$ with $$X \in [V]^{\aleph_1}$$. Therefore, the dual of Abraham's Theorem would suffice to establish the consistency of the dual of Galvin's Conjecture. 


---
title: Stationary strategies in Choquet games
date: 2011-10-14 04:46:41
permalink: /archives/38/
published: true
categories: [topology, games]
tags: [Choquet game, MF spaces]
people: [Carl Mummert, Frank Stephan]
---
The (_strong_) _Choquet game_ on a topological space $$X$$ is played as follows. There are two players, Empty and Nonempty, who alternate turns for infinitely many rounds. On round $$i$$, Empty moves first, choosing a point $$x_i$$ and an open neighborhood $$U_i$$ of $$x_i$$ and, if $$i \geq 1$$, such that $$U_i \subseteq V_{i-1}$$ (the open set that Nonempty played on the previous round). Then, Nonempty responds with an open neighborhood $$V_i$$ of the same point $$x_i$$ such that $$V_i \subseteq U_i$$. After all the rounds have been played, we obtain a descending sequence of open sets 
^
$$U_0 \supseteq V_0 \supseteq U_1 \supseteq V_1 \supseteq U_2 \supseteq V_2 \supseteq \cdots$$
^
 together with a sequence of points $$x_0,x_1,x_2,\dots$$ Empty wins this play if $$\bigcap_{i=0}^\infty V_i = \emptyset$$; Nonempty wins if $$\bigcap_{i=0}^\infty V_i \neq \emptyset$$. 

A _Choquet space_ is a topological space $$X$$ such that Nonempty has a winning strategy in the Choquet game played on the topological space $$X$$. The Choquet game was originally designed by Choquet to give a topological characterization of which metrizable spaces admit a complete metric. However, not all Choquet spaces are metrizable. In general, the Choquet game turns out to be a good measure of completeness for topological spaces. 

In the case of complete metric spaces $$X$$, Nonempty has a relatively simple winning strategy in the Choquet game on $$X$$. Once Empty has played the point-neighborhood pair $$x_i \in U_i$$, Nonempty responds by picking an open ball $$V_i$$ around $$x_i$$ that fits inside $$U_i$$ and has radius no larger than $$1/2^i$$. This forces Empty to play a Cauchy sequence of points $$x_0,x_1,x_2,\dots$$ whose limit witnesses that $$\bigcap_{i=0}^\infty V_i \neq \emptyset$$. Note that to carry out this strategy, Nonempty only needs to know the last move played by Empty and to remember which round is currently being played. In fact, with just a small change in strategy, Nonempty doesn't even need to remember which round is being played: Nonempty simply needs to pick an open ball $$U_i$$ around $$x_i$$ whose radius is no larger than a quarter of the diameter of $$V_i$$ since that ensures that the radius of each open ball played by Nonempty decreases by at least one half at each step. 

A strategy for Nonempty that only uses the last move played by Empty to decide what to play next is called a _stationary strategy_. Thus, we see that for a metrizable space $$X$$, the following are equivalent: 

  1. $$X$$ admits a complete metric.
  2. Nonempty has a winning strategy in the Choquet game played on $$X$$.
  3. Nonempty has a stationary winning strategy in the Choquet game played on $$X$$.

Since the Choquet game makes sense for arbitrary topological spaces, it makes sense to ask whether items 2 and 3 are equivalent in the general case. This is not the case, but it is known that the equivalence holds for classes of spaces much broader than metrizable spaces. 

In our paper {% include p.cite _='DorMum10e' %}, Carl Mummert and I show that the equivalence between the existence of general and stationary strategies for Nonempty in the Choquet game holds for an interesting class of spaces, which includes all second-countable T1 spaces. To state our main result, I must introduce an unusual property of topological bases. A base $$\mathcal{B}$$ for a topology is said to be _open-finite_ if every open set has only finitely many supersets in $$\mathcal{B}$$. While it is unusual for a base to have this property, it turns out that many spaces happen to have such a base. For example, all second-countable T1 spaces have such a base. The main result of our paper is the following. 

**Theorem {% include p.cite _='DorMum10e' %}.** _Let $$X$$ be a topological space with an open-finite base. If Nonempty has a winning strategy in the Choquet game on $$X$$, then Nonempty has a stationary winning strategy in the Choquet game on $$X$$._

The method for proving this is new and interesting, but you will have to read our paper to find out... 

The Choquet game appears to be tied with certain types of representability of topological spaces. Representability issues are very important in the context of reverse mathematics since second-order arithmetic offers very limited resources to talk about large multi-layered objects like topological spaces. In {% include p.cite _='Mum06c' %}, Carl Mummert introduced a broad class of topological spaces that can be represented in second-order arithmetic: countably based maximal filter (MF) spaces. The basic datum for these spaces consists of a countable partial order $$(\mathcal{P},{\leq})$$, the points of the space is the class $$MF(\mathcal{P},{\leq})$$ of maximal filters on $$(\mathcal{P},{\leq})$$, and the basic open sets consist of all classes $$U_p = \set{F \in MF(\mathcal{P},{\leq}) : p \in F}$$. It is not hard to see that these second-countable spaces are all T1 and Choquet. 

A topological characterization of countably based MF spaces was obtained by {% include t.cite _='MumSte10o' %}, who established that the countably based MF spaces are precisely the second-countable T1 Choquet spaces. The original proof of this result is long and intricate. The existence of stationary winning strategies for Nonempty in such spaces leads to a much easier proof of this representation theorem. This proof was not included in our paper since it was too far from the main topic and not short enough to include in passing. Therefore, I am recording this proof here for prosperity. 

**Theorem {% include p.cite _='MumSte10o' %}.** _Every second-countable T1 Choquet space is homeomorphic to a countably based MF space._

_Proof._ Suppose that $$X$$ is a second-countable T1 Choquet space. Let $$\mathcal{B}$$ be a countable open-finite base for $$X$$, and let $$\mathfrak{S}$$ be a stationary strategy for Nonempty in the Choquet game on $$X$$. We will define a transitive relation $${\prec}$$ on $$\mathcal{B}$$ such that $$X$$ is homeomorphic to $$MF(\mathcal{B},{\preceq})$$. (Although the notation suggests otherwise, the relation $${\prec}$$ is not necessarily irreflexive.) 

A natural choice for $${\prec}$$ would be to define $$V \prec U$$ to hold if and only if $$V \subseteq \mathfrak{S}(x,U)$$ for some $$x \in V$$. However, this relation is not necessarily transitive. To remedy this, we define $$V \prec U$$ to hold if and only if there is a point $$x \in V$$ such that $$V \subseteq \mathfrak{S}(x,W)$$ for every $$W \in \mathcal{B}$$ such that $$U \subseteq W$$. This relation is clearly transitive. Moreover, since $$\mathcal{B}$$ is open-finite, there are only finitely many such $$W$$, so the intersection of all corresponding $$\mathfrak{S}(x,W)$$ is an open neighborhood of $$x$$. This guarantees that for every $$x \in U$$, there is a $$V \in \mathcal{B}$$ such that $$x \in V$$ and $$V \prec U$$. 

We begin by recording a lemma that will be used repeatedly in this proof. 

**Lemma.** _For every maximal filter $$F$$ on $$(\mathcal{B},{\preceq})$$ there is a descending sequence_ 
^
$$\cdots \prec U_2 \prec U_1 \prec U_0$$
^
_such that $$F = \set{W \in \mathcal{B} : (\exists i)(U_i \preceq W)}$$._

_Proof._ Since $$F$$ is countable and downward directed in $$(\mathcal{B},{\preceq})$$, it is easy to get a sequence 
^
$$\cdots \preceq V_2 \preceq V_1 \preceq V_0$$
^
 such that $$F = \set{W \in \mathcal{B} : (\exists i)(V_i \preceq W)}$$. If this sequence is not eventually constant, we can eliminate repeated elements to obtain the a sequence as required by the lemma. Otherwise, we may assume that $$V_0 = V_i$$ for every $$i$$. As observed above, there must be some $$U \in \mathcal{B}$$ such that $$U \prec V$$. Since $$F$$ is a maximal filter in $$(\mathcal{B},{\preceq})$$, we must have $$U = V$$, which means that the constant sequence $$U_i = U$$ is as required by the lemma. _QED_

The first step of the proof is to define the map $$h:MF(\mathcal{B},{\preceq}) \to X$$ that will witness that the two spaces are homeomorphic. Fix $$F \in MF(\mathcal{B},{\preceq})$$, we will show that $$\bigcap F$$ is always a singleton, so that we may define $$h(F)$$ to be the unique point of $$X$$ that belongs to every element of $$F$$. 

First find a descending sequence 
^
$$\cdots \prec U_2 \prec U_1 \prec U_0$$
^
 that generates $$F$$ as in the above lemma. By definition of $$\prec$$, we can find corresponding points $$x_1,x_2,\dots$$ such that $$x_i \in U_{i+1}$$ and $$U_{i+1} \subseteq \mathfrak{S}(x_i,U_i)$$. This defines a valid sequence of moves for Empty against Nonempty's stationary strategy $$\mathfrak{S}$$ in the Choquet game on $$X$$. Since $$\mathfrak{S}$$ is a winning strategy for Nonempty, it follows that $$\bigcap_{i=0}^\infty U_i = \bigcap F$$ is nonempty. 

To see that $$\bigcap F$$ has only one point, suppose for the sake of contradiction that $$\bigcap_{i=0}^\infty U_i$$ contains two distinct points $$x$$ and $$y$$. Because $$X$$ is T1, we can find a neighborhood $$V_0$$ of $$x$$ in $$\mathcal{B}$$ that does not contain $$y$$. Define the descending sequence 
^
$$\cdots \prec V_2 \prec V_1 \prec V_0$$
^
 so that $$x \in V_{i+1}$$ and $$V_{i+1} \subseteq \mathfrak{S}(x,W)$$ for every $$W \in \mathcal{B}$$ such that $$V_i \cap U_i \subseteq W$$. The filter 
^
$$G = \set{W \in \mathcal{B} : (\exists i)(V_i \preceq W)}$$
^
 extends $$F$$ since $$V_i \preceq U_i$$ for each $$i$$. Since $$V_0 \in G$$ but $$V_0 \notin F$$, this contradicts the maximality of $$F$$. 

Now that $$h:MF(\mathcal{B},{\preceq}) \to X$$ is properly defined, it remains to show that it is a homeomorhism. We first show that $$h$$ is a bijection, which we break into two facts: 

  * _$$h$$ is injective_. Suppose that $$F_0$$ and $$F_1$$ are maximal filters that map to the same point $$x$$. By the lemma, we can find two sequences 
^
$$\cdots \prec U_2^d \prec U_1^d \prec U_0^d \qquad (d \in \set{0,1})$$
^
 that generate these two filters. Since $$x \in U_i^0 \cap U_i^1$$ for each $$i$$, we can find another sequence 
^
$$\cdots V_2 \prec V_1 \prec V_0$$
^
 of neighborhoods of $$x$$ in $$\mathcal{B}$$ such that $$V_{i+1} \subseteq \mathfrak{S}(x,W)$$ for every $$W \in \mathcal{B}$$ such that $$U_i^0 \cap U_i^1 \cap V_i \subseteq W$$. Then the filter 
^
$$G = \set{W \in \mathcal{B} : (\exists i)(V_i \preceq W)}$$
^
 extends both $$F_0$$ and $$F_1$$, which means that $$F_0 = G = F_1$$.
  * _$$h$$ is surjective_. Let $$U_0,U_1,U_2,\dots$$ be an enumeration of $$\mathcal{B}$$ (possibly with repetitions). Given $$x \in X$$, define the descending sequence 
^
$$\cdots \preceq V_2 \preceq V_1 \preceq V_0$$
^
 of neighborhoods of $$x$$ in $$\mathcal{B}$$ as follows. Pick $$V_0 \in \mathcal{B}$$ so that $$x \in V_0$$. If $$x \in U_i$$ then pick $$V_{i+1}$$ in such a way that $$V_{i+1} \subseteq \mathfrak{S}(x,W)$$ for every $$W \in \mathcal{B}$$ such that $$V_i \cap U_i \subseteq W$$; if $$x \notin U_i$$ then simply set $$V_{i+1} = V_i$$. Since $$X$$ is T1, we immediately see that $$\bigcap_{i=0}^\infty V_i = \set{x}$$. Therefore, any maximal filter extending 
^
$$F = \set{W \in \mathcal{B} : (\exists i)(V_i \preceq W)}$$
^
 will map to $$x$$. (In fact, $$F$$ is already maximal.)
Since the choice of $$V_0$$ was essentially arbitrary in the process we just used to show that $$h$$ is surjective, for every $$V_0 \in \mathcal{B}$$ and every $$x \in V_0$$ we can find some $$F \in MF(\mathcal{B},{\preceq})$$ such that $$V_0 \in F$$ and $$h(F) = x$$. It follows that 
^
$$h(F) \in V_0 \quad\IFF\quad V_0 \in F,$$
^
which shows that $$h$$ is a homeomorphism. _QED_



{% include cite.md %}

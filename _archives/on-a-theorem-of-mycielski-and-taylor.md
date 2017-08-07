---
title: On a theorem of Mycielski and Taylor
date: 2011-11-06 19:28:03
permalink: /archives/503/
published: true
topics: [combinatorics, set-theory]
tags: [Cardinal Characteristics, Independent Sets, Polish Spaces, Ramsey Theory]
people: [Alan Taylor, Andreas Blass, Fred Galvin, Jan Mycielski, Rafał Filipów, Tomasz Natkaniec]
---

{% include t.cite _='Myc64n' %} proved a wonderful theorem about independent sets in Polish spaces. He showed that if $$X$$ is an uncountable Polish space and $$R_n$$ is a meager subset of $$X^n$$ for each $$n \geq 1$$, then there is a perfect set $$Z \subseteq X$$ such that $$(z_1,\dots,z_n) \notin R_n$$ whenever $$z_1,\dots,z_n$$ are distinct elements of $$Z$$. In other words, $$Z$$ is $$R_n$$-independent for each $$n \geq 1$$. This is a wonderfully general theorem that has a multitude of applications. 

One of my favorite theorems where Mycielski's Theorem comes in handy is a remarkable partition theorem due to Fred Galvin. 

**Theorem {% include p.cite _='Gal68c' %}.** _Let $$X$$ be an uncountable Polish space and let $$c:[X]^2\to\set{0,\dots,k-1}$$ be a Baire measurable coloring where $$k$$ is a positive integer. Then $$X$$ has a perfect $$c$$-homogeneous subset._

Galvin proved a similar result for colorings of $$[X]^3$$, but with a weaker conclusion that triples from the perfect set take on at most two colors. {% include t.cite _='Bla81l' %} then extended Galvin's result to colorings of $$[X]^n$$, showing that there is a perfect set that takes on at most $$(n-1)!$$ colors. 

Galvin's result has many applications too. For example, Rafał Filipów and I used it in {% include p.cite _='DorFil05p' %} it to show that if $$X$$ is a perfect Abelian Polish group, then $$X$$ contains a Marczewski null set $$A$$ such that the algebraic sum $$A + A$$ is not Marczewski measurable. 

{% include t.cite _='Tay78b' %} generalized the result to Baire measurable colorings $$c:[X]^2\to\kappa$$ where $$\kappa$$ is any cardinal smaller than $$\DeclareMathOperator{\cov}{cov}\newcommand{\meager}{\mathcal{M}}\cov(\meager)$$. Doing so, Taylor similarly generalized Mycielski's Theorem, but he only stated the result for binary relations. Recently, Rafał Filipów, Tomasz Natkaniec and I needed this generalization for relations of arbitrary arity. Unfortunately, the Mycielski–Taylor result has never been stated in full generality, so we included a proof in our paper {% include p.cite _='DorFilNat13u' %}. I am copying this proof here because I think the result is of independent interest and our proof is a nice application of Cohen forcing. A nice consequence of this extended Mycielski–Taylor Theorem is that Blass's result extends to Baire measurable colorings $$c:[X]^n\to\kappa$$ where $$\kappa \lt \cov(\meager)$$ in the same way that Taylor generalized Galvin's result for partitions of pairs. 

**Theorem {% include p.cite _='Myc64n Tay78b' %}.** _Let $$X$$ be an uncountable Polish space and let $$\mathcal{R}$$ be a family of fewer than $$\cov(\meager)$$ closed nowhere dense relations on $$X$$, i.e., each $$R \in \mathcal{R}$$ is a closed nowhere dense subset of $$X^n$$ for some $$n = n(R)$$. Then $$X$$ contains a perfect set which is $$R$$-independent for every $$R \in \mathcal{R}$$._

Our proof relies on the following forcing characterization of $$\cov(\meager)$$, which can be found in {% include p.cite _='BarJud95v' %}. 

**Lemma.** _If $$\mathcal{P}$$ is a countable partial order and $$\mathcal{D}$$ is a family of dense subsets of $$\mathcal{P}$$ with $$\vert \mathcal{D} \vert \lt \cov(\meager)$$, then there is a filter on $$\mathcal{P}$$ that meets every element of $$\mathcal{D}$$._

In other words, $$\cov(\meager) = \mathfrak{m}(\text{Cohen})$$, in the notation of {% include p.cite _='BarJud95v' %}.

For simplicity, we will assume that $$X$$ is Baire space $$\omega^\omega$$. As usual, we write 
^
$$[s] = \set{x \in \omega^\omega : s \subset x}$$
^
 for $$s \in \omega^{\lt\omega}$$. 

We may assume that the family $$\mathcal{R}$$ at least contains the diagonal $$\set{(x,x): x \in \omega^\omega}$$. We may also assume that all relations $$R\in\mathcal{R}$$ are symmetric. (Otherwise, replace each $$R \in \mathcal{R}$$ by the relation $$\bigcup_{\sigma\in\mathrm{Sym}(n)} \set{ (x_{\sigma(1)},\dots, x_{\sigma(n)}): (x_1,\dots, x_n)\in R}$$, where $$n=n(R)$$ and $$\mathrm{Sym}(n)$$ denotes the set of all permutations of $$\set{1,2,\dots,n}$$.) 

Consider the partial order $$\mathcal{P}$$ whose conditions are pairs $$p = (d_p,f_p)$$ where $$d_p \in \omega$$ and $$f_p:2^{d_p}\to\omega^{\lt\omega}$$ is such that $$\vert f_p(s) \vert \geq d_p$$ for all $$s \in 2^{d_p}$$; the ordering of $$\mathcal{P}$$ is defined by $$p \leq q$$ iff $$d_p \leq d_q$$ and $$f_p(s{\upharpoonright}d_p) \subseteq f_q(s)$$ for all $$s \in 2^{d_q}$$. 

For $$k \in \omega$$ and $$R \in \mathcal{R}$$, consider the set $$\mathcal{D}_{k,R}$$ of all conditions $$p \in \mathcal{P}$$ such that $$k \leq d_p$$ and 
^
$$R \cap \prod_{s \in \Sigma} [f_p(s)] = \emptyset$$
^
 for all $$n(R)$$-element subset $$\Sigma$$ of $$2^{d_p}$$. (Note that this condition is slightly ambiguous since no ordering of $$\Sigma$$ is given, but since $$R$$ is assumed to be symmetric any ordering will do.) 

We claim $$\mathcal{D}_{k,R}$$ is always dense in $$\mathcal{P}$$. To see this fix a condition $$p \in \mathcal{P}$$. We may assume that $$d_p \geq k$$. Fix an enumeration $$\Sigma_1,\dots,\Sigma_m$$ of all $$n(R)$$-element subsets of $$2^{d_p}$$ and successively define conditions $$p \leq p_1 \leq \cdots \leq p_m$$ in such a way that $$d_p = d_{p_1} = \cdots = d_{p_m}$$ and $$R \cap \prod_{s\in\Sigma_i} [f_{p_i}(s)] = \emptyset$$ for every $$i = 1,\dots,m$$. This is always possible since $$R$$ is closed nowhere dense. Then, $$p_m$$ is the desired extension of $$p$$ in $$\mathcal{D}_{k,R}$$. 

By the Lemma, there is a filter $$G$$ over $$\mathcal{P}$$ that meets all dense sets $$\mathcal{D}_{k,R}$$ for $$k \in \omega$$ and $$R \in \mathcal{R}$$. We claim that the set 
^
$$Z = \set{ x \in \omega^\omega : (\forall p \in G)(\exists s \in 2^{d_p})(f_p(s) \subset x) } = \bigcap_{p \in G} \bigcup_{s \in 2^{d_p}} [f_p(s)]$$
^
 is as required. 

Note that when $$R$$ is the diagonal relation, then $$p \in D_{k,R}$$ if and only if $$d_p \geq k$$ and the clopen sets $$[f_p(s)]$$ are pairwise disjoint for $$s \in 2^{d_p}$$. It follows that $$Z$$ is a perfect set. 

Now, we show that $$Z$$ is $$R$$-independent for each $$R\in\mathcal{R}$$. Let $$z_1,\dots,z_n \in Z$$ be distinct, where $$n = n(R)$$ is the arity of $$R$$. There is $$k\in\omega$$ such that $$z_i\restriction k \neq z_j\restriction k$$ for distinct $$i,j=1,\dots,n$$. Let $$p\in G \cap D_{k,R}$$. For every $$i=1,\dots,n$$ there are $$s_i\in 2^{d_p}$$ with $$z_i\in[f_p(s_i)]$$. Since $$d_p\geq k$$ and $$z_i\restriction d_p \subset f_p(s_i) $$, $$s_1,\dots,s_n$$ are pairwise distinct. Let $$\Sigma=\set{s_1,\dots,s_n}$$. Since $$p\in D_{k,R}$$, $$R \cap \prod_{s \in \Sigma} [f_p(s)] = \emptyset.$$ In particular, $$(z_1,\dots,z_n) \notin R$$. 


{% include cite.md %}

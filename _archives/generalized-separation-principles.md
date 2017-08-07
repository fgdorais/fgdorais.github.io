---
title: Generalized separation principles
date: 2012-02-26 16:09:16
permalink: /archives/650/
published: true
categories: [computability, reverse-math]
tags: [Weak König Lemma]
people: [Carl Jockusch, Doug Cenzer, Itay Neeman, Peter Hinman, Richard Friedberg]
---
It is well-known that computability theory and reverse mathematics have very strong ties. Indeed, the base theory $$\newcommand{\RCA}{\mathsf{RCA}_0}\RCA$$ used in reverse mathematics was designed as the minimal theory that can adequately formulate and prove the basic results of computability theory. Based on the Church–Turing thesis, this is a very reasonable way to capture the proof method known as direct computation in everyday mathematics. Although the ties run very deep, there are always frictions when translating results between computability theory and reverse mathematics. The aim of this post is to talk about different ways of doing this translation but I will do so by talking about a family of generalized separation principles that I recently realized were (non-trivially) equivalent, a fact that had been well known in computability theory for several decades. 

Three central notions in computability theory are _computable sets and functions_, _computably enumerable sets_, and _partial computable functions_. The better known way to translate these into reverse mathematics is to use the correspondences 
^
$$\fbox{computable} = \Delta^0_1, \qquad \fbox{computably enumerable} = \Sigma^0_1.$$
^
 Since $$\RCA$$ includes $$\Delta^0_1$$-comprehension, computable sets correspond to actual sets in reverse mathematics but, since $$\Sigma^0_1$$-comprehension is only available in $$\newcommand{\ACA}{\mathsf{ACA}_0}\ACA$$ and beyond, computably enumerable sets must always be accessed by indirect means such as $$\Sigma^0_1$$-formulas. The drawback of this translation is that $$\Sigma^0_1$$-formulas are not part of the everyday language of mathematics so the principles that arise in this way, no matter how useful, do not fit well with the goals of reverse mathematics. 

A poignant example is the very handy _$$\Sigma^0_1$$-separation scheme_: 
^
$$(\forall n)(\lnot\phi(n) \lor \lnot\psi(n)) \lthen (\exists C)(\forall n)((\phi(n) \lthen n \in C) \land (\psi(n) \lthen n \notin C)),$$
^
 where $$\phi$$ and $$\psi$$ range over $$\Sigma^0_1$$ formulas. This principle is directly inspired by _inseparable pairs_ in computability theory, i.e., a pair of disjoint computably enumerable sets $$A$$ and $$B$$ such that there is no computable set $$C$$ such that $$A \subseteq C$$ and $$B \cap C = \varnothing.$$ The existence of such pairs shows that some instances of $$\Sigma^0_1$$-separation fail in $$\mathrm{REC}$$ and hence are not provable in $$\RCA.$$ 

It turns out that the $$\Sigma^0_1$$-separation scheme is equivalent to $$\newcommand{\WKL}{\mathsf{WKL}_0}\WKL$$ over $$\RCA.$$ Since the weak König lemma is widely used in combinatorics, this is a well justified object of study for reverse mathematics. In practice, though, many reversals involving the weak König lemma go through $$\Sigma^0_1$$-separation instead. To avoid bringing in $$\Sigma^0_1$$-formulas, the scheme is often stated in the following alternate form: 

_If $$f,g:\N\to\N$$ are one-to-one functions with disjoint ranges, then there is a set $$C$$ such that $$f(n) \in C$$ and $$g(n) \notin C$$ for all $$n.$$_

This translation uses the fact that infinite computably enumerable sets are precisely the ranges of one-to-one computable functions. Separating sets always exist when one of the two computably enumerable sets is finite so it is harmless to exclude that case. 

While using enumerations as above makes a lot of sense, excluding finite sets is sometimes harmful; even if repetitions are allowed, excluding the empty set is also sometimes harmful. This issue pops up in computability theory too and, fortunately, computability theorists have found a nice solution. Every computably enumerable can be represented as the union of a computable sequence of finite sets, in fact, a nondecreasing sequence of finite sets. In other words, every computably enumerable set can be enumerated by a process that outputs a finite (possibly zero) number of elements into the set at every stage. This idea is interesting since it is not too far removed from mathematical practice. It is unusual to enumerate things in such a general manner, but this extra generality is there to fix a genuine problem; standard enumerations can be substituted when this is harmless. 

Recently, I've taken the habit of using the term _enumerable set_ for a nondecreasing sequence $$A = \seq{a_s}_{s=0}^\infty$$ of (coded) finite sets. Since the actual enumeration is usually irrelevant, I often use these as if they were actual sets. So I write $$n \in A$$ to mean 
^
$$(\exists s)(n \in a_s),$$
^
 $$A \subseteq B$$ to mean 
^
$$(\forall n)((\exists s)(n \in a_s) \lthen (\exists t)(n \in b_t)),$$
^
 and even $$A = B$$ to mean 
^
$$(\forall n)((\exists s)(n \in a_s) \liff (\exists t)(n \in b_t)).$$
^
 The term enumerable set is a slightly dangerous abuse since enumerable sets are not necessarily sets in the context reverse mathematics. Nevertheless, I find the translation 
^
$$\fbox{computable} = \fbox{set}, \qquad \fbox{computably enumerable} = \fbox{enumerable set}$$
^
 very compelling. I sometimes use decidable set instead of plain set for emphasis. With this convention, $$\Sigma^0_1$$-separation can be stated as follows. 

_If $$A$$ and $$B$$ are disjoint enumerable sets, then there is a decidable set $$C$$ such that $$A \subseteq C$$ and $$B \cap C = \varnothing.$$_

This is almost identical to the negation of the existence of an inseparable pair. 

Since partial computable functions are precisely the partial functions with computably enumerable graphs, it seems appropriate to use _partial enumerable function_ to mean a partial function whose graph is an enumerable set. Note that if a partial enumerable function $$F$$ happens to be total, then $$F(n) = m$$ is a $$\Delta^0_1$$ predicate so $$F$$ is a total function whose graph is a set in $$\RCA.$$ If $$A$$ and $$B$$ are disjoint enumerable sets, then $$F = A\times\set{0} \cup B \times\set{1}$$ is a partial enumerable function and $$C$$ is a separating set for $$A$$ and $$B$$ precisely when $$\bar{F} = C\times\set{0}\cup(\N-C)\times\set{1}$$ is a total extension of $$F.$$ Thus we obtain yet another formulation of $$\Sigma^0_1$$-separation: 

_Every partial enumerable function $$F:\N\to\set{0,1}$$ can be extended to a total function $$\bar{F}:\N\to\set{0,1}.$$_

It seems we just gained a new parameter. Instead of extending a partial enumerable function $$\N\to\set{0,1}$$ we could try to extend a partial enumerable function $$\N\to\set{0,\dots,k-1}.$$ Because of binary representation, there is no gain here: separating $$k$$ mutually disjoint enumerable sets is not harder than separating just two. However, the ability to extend any partial enumerable function $$\N\to\N$$ to a total one is equivalent to arithmetic comprehension. 

This brings us to the most computably-theoretic reverse mathematics principle: $$\newcommand{\DNR}{\mathsf{DNR}}\DNR.$$ In computability theory, a function $$F:\N\to\N$$ is _diagonally non-computable_ if $$F(n) \neq \phi_n(n)$$ where $$\phi_n$$ is the $$n$$-th partial computable function in the standard enumeration. This concept relativizes as usual, and $$\DNR$$ is the statement that there is an $$A$$-diagonally non-computable function for every set $$A.$$ While this is perhaps the most natural way to state $$\DNR,$$ we can avoid the reference to the standard enumeration of the partial computable functions by formulating it as follows: 

_For every partial enumerable function $$F:\N\to\N$$ there is a total function $$G:\N\to\N$$ such that $$F(n) \neq G(n)$$ for every $$n \in \operatorname{dom}(F).$$_

This clearly implies the usual formulation of $$\DNR$$ and the universal properties of the standard enumeration show that this statement is equivalent. The reason why $$\DNR$$ is so handy is that it is a non-trivial consequence of $$\WKL$$ which is easily accessible to methods from computability theory. To see that $$\DNR$$ follows from $$\WKL,$$ consider the strengthened version $$\DNR_2$$: 

_For every partial enumerable function $$F:\N\to\set{0,1}$$ there is a total function $$G:\N\to\set{0,1}$$ such that $$F(n) \neq G(n)$$ for every $$n \in \operatorname{dom}(F).$$_

The function $$G:\N\to\set{0,1}$$ is as required exactly when $$\bar{F}(n) = 1-G(n)$$ is a total extension of $$F.$$ 

Once again, we have gained an extra parameter. Could the sequence of principles 
^
$$\DNR_2 \lthen \DNR_3 \lthen \DNR_4 \lthen \DNR_5 \lthen \cdots$$
^
 form a strictly descending chain from $$\WKL$$ to $$\DNR$$? It turns out that these principles are all equivalent to $$\WKL$$ but before we see why that is, let's consider yet another way to formulate these principles. It is easy to see that $$\DNR_k$$ is equivalent to: 

_If $$A_0,\dots,A_{k-1}$$ are mutually disjoint enumerable sets, then there is a total function $$G:\N\to\set{0,\dots,k-1}$$ such that $$n \notin A_{G(n)}$$ for every $$n.$$_

In this light, we see that the assumption that the enumerable sets are mutually disjoint is unnecessarily strong: the minimal requirement for the conclusion to hold is that $$A_0 \cap \cdots \cap A_{k-1} = \varnothing.$$ This fact was observed by {% include t.cite _='CenHin08r' %}, who introduced yet another parameter to formulate the generalized separation principles $$\newcommand{\Sep}{\mathsf{S}}\Sep^\ell_k$$: 

_If $$A_0,\dots,A_{k-1}$$ are enumerable sets such that the intersection of any $$\ell+1$$ of them is empty, then there is a total function $$G:\N\to\set{0,\dots,k-1}$$ such that $$n \notin A_{G(n)}$$ for every $$n.$$_

Cenzer and Hinman looked at these from the perspective of Medvedev degrees of $$\Pi^0_1$$-classes. They found that the Medvedev degrees associated to these generalized separation principles have a rich structure, but that this structure trivializes when considering Muchnik degrees instead. From the perspective of reverse mathematics, this suggests that all of these principles are equivalent to $$\WKL.$$ This pretty much the case but we will soon see that there is a little twist to this story... 

At this point, we have a doubly indexed array of generalized separation principles and the following implications: 
^
$$\begin{array} && &&& & & \Sep^4_5&\lthen&\cdots\cr && && && \downarrow \cr && && \Sep^3_4 & \lthen & \Sep^3_5&\lthen&\cdots\cr && && \downarrow && \downarrow \cr && \Sep^2_3 &\lthen& \Sep^2_4 &\lthen& \Sep^2_5&\lthen&\cdots\cr && \downarrow && \downarrow && \downarrow\cr \Sep^1_2 &\lthen& \Sep^1_3 &\lthen& \Sep^1_4 &\lthen&\Sep^1_5&\lthen&\cdots \end{array}$$
^
 Note that all of these are easy consequences of $$\WKL,$$ so the question is whether any of them are strictly weaker. The following lemma allows us to walk backwards in this array. The argument is due to Richard Friedberg, but it was first published by {% include t.cite _='Joc89f' %} (for $$\ell=1$$). 

**Lemma ($$\RCA$$).** _For all positive integers $$k$$ and $$\ell,$$ $$\Sep^{\ell^2}_{k^2}$$ implies $$\Sep^\ell_{k}$$. In particular, $$\DNR_{k^2}$$ implies $$\DNR_k.$$_

**Proof.** Let $$A_0,\dots,A_{k-1}$$ be enumerable sets such that the intersection of any $$\ell+1$$ of them is empty. Our goal is to find a function $$F:\N\to\set{0,\dots,k-1}$$ such that $$n \notin A_{F(n)}$$ for every $$n.$$ 

Consider the enumerable sets $$B_0,\dots,B_{k^2-1}$$ defined by 
^
$$B_{i+jk} = \set{\seq{m,n} : m \in A_i, n \in A_j}$$
^
 for $$i,j \lt k.$$ These sets have the property that the intersection of any $$\ell^2+1$$ of them is empty. It follows from $$\Sep^{\ell^2}_{k^2}$$ that there is a function $$H:\N\to\set{0,\dots,k^2-1}$$ such that $$B_\ell \cap H^{-1}(\ell) = \varnothing$$ for every $$\ell \lt k^2.$$ Define $$G_0,G_1:\N^2\to\set{0,\dots,k-1}$$ by the equation 
^
$$H(\seq{m,n}) = G_0(m,n) + G_1(m,n)k.$$
^
 Note that if $$m \in A_i$$ and $$n \in A_j$$ then either $$G_0(m,n) \neq i$$ or $$G_1(m,n) \neq j.$$ We now consider two cases. 

If for every $$m$$ there is a $$n$$ such that $$n \in A_{G_1(m,n)},$$ then let $$N:\N\to\N$$ be such that $$N(m) \in A_{G_1(m,N(m))}$$ for every $$m.$$ Note that we must then have $$m \notin A_{G_0(m,N(m))}$$ for every $$m,$$ which means that $$F(m) = G_0(m,N(m))$$ is as required. 

Otherwise, there is an $$m_0$$ such that $$n \notin A_{G_1(m_0,n)}$$ for every $$n.$$ In that case, $$F(n) = G_1(m_0,n)$$ is as required. **QED**

This collapses the entire array of generalized separation principles, but the final alternative in the proof requires to decide a $$\Sigma^0_2$$ statement. This is why the Medvedev degrees associated to these principles have such a rich structure, but the associated Muchnik degrees do not. Reverse mathematics also shows little sensitivity to such complex decisions, but it is not completely insensitive since the ability to compound such decisions requires some induction. 

**Lemma ($$\RCA + \mathsf{I}\Sigma^0_2$$).** _For all positive integers $$k,$$ $$\ell$$ and $$m,$$ $$\Sep^{\ell^m}_{k^m}$$ implies $$\Sep^\ell_{k}.$$ In particular, $$\DNR_{k^m}$$ implies $$\DNR_k$$._

**Proof.** We proceed as in the previous proof, except that the sets $$B_0,\dots,B_{k^m-1}$$ are now defined by 
^
$$B_{i_0+i_1k+\cdots+i_{m-1}k^{m-1}} = \set{\seq{n_0,n_1,\dots,n_{m-1}} : n_0 \in A_{i_0}, n_1 \in A_{i_1},\dots,n_{m-1} \in A_{i_{m-1}}}$$
^
 for all $$i_0,i_1,\dots,i_{m-1} \lt k.$$ These enumerable sets again have the property that the intersection of any $$\ell^m+1$$ of them is empty, so it follows from $$\Sep^{\ell^m}_{k^m}$$ that there is a function $$H:\N\to\set{0,\dots,k^m-1}$$ such that $$n \notin B_{H(n)}$$ for every $$n.$$ Again, define $$G_0,\dots,G_{m-1}:\N^m\to\N$$ by 
^
$$H(\seq{n_0,\dots,n_{m-1}}) = \sum_{i=0}^{m-1} G_i(n_0,\dots,n_{m-1})k^i.$$
^
 (Note that since $$m$$ could be non-standard, all $$m$$-tuples are understood to be coded $$m$$-tuples but we will not be too fussy about proper notation.) 

By $$\mathsf{I}\Sigma^0_2,$$ we can find the largest index $$j \lt m$$ for which there is some sequence $$\seq{n_0,\dots,n_{j-1}}$$ such that 
^
$$\seq{n_j,\dots,n_{m-1}} \notin A_{G_j(n_0,\dots,n_{m-1})}\times\cdots\times A_{G_{m-1}(n_0,\dots,n_{m-1})}$$
^
 holds for all choices of $$n_j,\dots,n_{m-1}.$$ It follows that for every choice of $$n$$ we can find some sequence $$\seq{n_{j+1},\dots,n_{m-1}}$$ such that 
^
$$\seq{n_{j+1},\dots,n_{m-1}} \in A_{G_{j+1}(n_0,\dots,n_{m-1})} \times\cdots\times A_{G_{m-1}(n_0,\dots,n_{m-1})}.$$
^
 Thus, the function $$F:\N\to\set{0,\dots,k-1}$$ defined by 
^
$$F(n) = G_j(n_0,\dots,n_{j-1},n,n_{j+1},\dots,n_{m-1})$$
^
 for the first sequence $$\seq{n_{j+1},\dots,n_{m-1}}$$ as above is necessarily such that $$n \notin A_{F(n)}$$ for all $$n.$$ **QED**

So, assuming $$\mathsf{I}\Sigma^0_2,$$ we can walk backwards along the bottom row of the array even by a non-standard number of steps. Now $$\Sep^1_k$$ (or $$\DNR_k$$) does not make sense as a stand-alone principle when $$k$$ is nonstandard, but the limiting principle $$(\exists k)\Sep^1_k$$ (equivalently $$(\exists k)\DNR_k$$) does make sense and it does allow for the witness $$k$$ to be non-standard. 

**Proposition ($$\RCA + \mathsf{I}\Sigma^0_2$$).** _$$(\exists k)\DNR_k$$ is equivalent to the weak König lemma._

While $$\mathsf{I}\Sigma^0_2$$ is the precise amount of induction needed to carry out the above proof, that does not mean that so much induction is necessary for the reversal. 

_Is the assumption $$\mathsf{I}\Sigma^0_2$$ necessary for the last proposition?_

Perhaps there is another argument that only uses $$\mathsf{I}\Sigma^0_1$$ or $$\mathsf{B}\Sigma^0_2$$? Such necessary uses of induction are rare, but an example of this was recently found by {% include t.cite _='Nee11m' %}. It would be interesting to see if this happens again in this case... 


{% include cite.md %}

---
title: Envelope forcing
date: 2012-05-06 18:02:01
permalink: /archives/827/
published: true
categories: [combinatorics, computability, independence-proofs, reverse-math]
tags: [Forcing, Ramsey Theory]
people: [Denis Hirschfeldt, Jared Corduan, Reed Solomon, Richard Shore, Rod Downey, Steffen Lempp]
bibliography: [CorDor12n, DowHirLemSol01m, HirSho07y]
---
In a recent paper (Corduan-Dorais 2012), Jared Corduan and I considered various notions of combinatorial indecomposability for finite ordinal powers of $$\omega.$$ In this process, we uncovered two weak forms of Ramsey's theorem for pairs ($$\newcommand{\RT}[2]{\mathsf{RT}^{#1}_{#2}}\RT2k$$): 

**The Weak Ramsey Theorem ($$\newcommand{\Wk}{\mathsf{W}}\Wk\RT2k$$).**
: For every coloring $$c:\N^2\to\set{0,\dots,k-1}$$ there are a color $$d \lt k$$ and an infinite set $$H$$ such that $$\set{y \in \N : c(x,y) = d}$$ is infinite for every $$x \in H.$$

**The Hyper-Weak Ramsey Theorem ($$\newcommand{\HWk}{\mathsf{HW}}\HWk\RT2k$$).**
: For every coloring $$c:\N^2\to\set{0,\dots,k-1}$$ there are a color $$d \lt k$$ and an increasing function $$h:\N\to\N$$ such that $$\bigcup_{x=h(i-1)}^{h(i)-1} \set{y \in \N : c(x,y) = d}$$ is infinite for every $$i \in \N.$$

The first is equivalent to what we called the game indecomposability of the ordinal $$\omega^2,$$ and the second is related to the lexicographic indecomposability of $$\omega^2.$$ You can find out more about these notions of indecomposability in our paper, what I want to write about here is the forcing technique that we used to show that $$\HWk\RT22$$ is $$\Pi^1_1$$-conservative over $$\mathsf{RCA}_0$$ with $$\Sigma^0_2$$-induction and to separate the two principles $$\Wk\RT22$$ and $$\HWk\RT22.$$ I've been calling the method envelope forcing since the basic idea is to force over a larger model that envelops the original one rather than forcing over the ground model itself. In the following, I will give a brief tour of this method, skipping all the gory details (that can be found in our paper). 

The forcing for $$\HWk\RT22$$ is a twist on Cohen forcing. Given a coloring $$c:\N^2\to\set{0,1},$$ we want to generically add an increasing function $$g:\N\to\N$$ such that the sets
^
$$\bigcup_{x=g(i-1)}^{g(i)-1} \set{y \in \N : c(x,y) = 0}$$
^
are all cofinite (and hence infinite). Obviously, we can't do this for every coloring so we will only consider coloring for which there is no increasing function $$h:\N\to\N$$ such that the sets 
^
$$\bigcup_{x=h(i-1)}^{h(i)-1} \set{y \in \N : c(x,y) = 1}$$
^
 are all infinite. The obvious idea is to force with the poset $$\newcommand{\PP}{\mathbb{P}}\PP$$ that consists of all finite functions $$p:\set{0,\dots,\card{p}-1}\to\N$$ such that the sets 
^
$$\bigcup_{x=p(i-1)}^{p(i)-1} \set{y \in \N : c(x,y) = 0}$$
^
 are cofinite when $$0 \lt i \lt \card{p}.$$ This is just another variant of Cohen forcing, which is well understood, so we should be all set! Unfortunately, this is not the case since this poset has a $$\Sigma^0_2$$ definition so our ground model $$\newcommand{\MN}{\mathcal{N}}\MN,$$ so we will have a very hard time understanding forcing with $$\PP$$ from inside $$\MN.$$ The trick to get around this issue is to force over an envelope model $$\MN'$$ where $$\PP$$ has a more manageable $$\Sigma^0_1$$ definition. 

So we start with a ground model $$\MN$$ of $$\newcommand{\RCA}{\mathsf{RCA}_0}\RCA + \newcommand{\Ind}[1]{\mathsf{I}#1}\Ind{\Sigma^0_2}.$$ The fact that $$\MN$$ satisfies $$\Ind{\Sigma^0_2}$$ guarantees that the $$\omega$$-extension $$\MN',$$ obtained by adding all sets that are $$\Delta^0_2$$ definable over $$\MN,$$ satisfies $$\RCA.$$ In $$\MN',$$ the poset $$\PP$$ described above has a $$\Sigma^0_1$$ definition, so there is no trouble forcing with $$\PP$$ and thereby adding a generic function $$g:\N\to\N$$ that does make all the sets 
^
$$\bigcup_{x=g(i-1)}^{g(i)-1} \set{y \in \N : c(x,y) = 0}$$
^
 cofinite. Of course, adding $$g$$ to $$\MN'$$ is of no use, we want to add $$g$$ to the ground model $$\MN.$$ We can certainly form the model $$\MN[g]$$ obtained by adding $$g$$ to $$\MN$$ and closing under $$\Delta^0_1$$-comprehension. The result will certainly be a model of $$\RCA$$ because $$\MN[g] \subseteq \MN'[g]$$ but we also want $$\MN[g]$$ to satisfy $$\Ind{\Sigma^0_2}$$ so we can iterate this process and obtain a model of $$\HWk\RT22$$ in the limit. 

It turns out that $$\PP$$ is relatively large in the poset $$\PP_0$$ of all finite increasing functions $$p:\set{0,\dots,\card{p}-1}\to\N$$ — which is just a variation of Cohen forcing for our base model $$\MN.$$ The following lemma (corresponding to Lemma 3.10 in [bibcite key=CorduanDorais]) shows that the generic $$g$$ for $$\PP$$ over $$\MN'$$ is also somewhat generic for $$\PP_0$$ over the original model $$\MN,$$ sufficiently generic that the extension $$\MN[g]$$ will satisfy $$\RCA + \Ind{\Sigma^0_2}.$$ 

**Relative Largeness Lemma.** _Suppose $$U \subseteq \PP_0$$ is $$\Sigma^0_1$$-definable over $$\MN.$$ For every $$p \in \PP,$$ if for every $$q \leq p,$$ $$q \in \PP,$$ there is a $$r \leq q$$ (in $$\PP_0$$ but not necessarily in $$\PP$$) such that $$r \in U,$$ then for every $$q \leq p,$$ $$q \in \PP,$$ there is a $$r \leq q$$ such that $$r \in U \cap \PP.$$_

In particular, if $$U$$ is dense below $$p$$ in $$\PP_0$$ then $$U \cap \PP$$ is dense below $$p$$ in $$\PP.$$ Therefore, $$g$$ is $$\Sigma^0_1$$-generic for $$\PP_0$$ over $$\MN$$: 

For every $$U \subseteq \PP_0$$ which is $$\Sigma^0_1$$-definable in $$\MN,$$ there is a $$p \subset g$$ that either $$p \in U,$$ or $$p$$ has no extension in $$U$$ at all.

Note that $$g$$ is unlikely to be much more generic than that since no initial segment of $$g$$ lies in $$\PP_0-\PP,$$ which could be dense in $$\PP_0$$ for a suitable coloring $$c.$$ Nevertheless, $$g$$ just generic enough to ensure that $$\MN[g]$$ satisfies $$\Ind{\Sigma^0_2}.$$ More precisely, relative largeness ensures that $$g$$ is low over the ground model: 

**Lowness Lemma.** _Every $$\Sigma^0_2$$ formula with parameters in $$\MN[g]$$ is equivalent to a $$\Sigma^0_1$$ formula with parameters in $$\MN'[g].$$_

The reason for this is that $$\MN'[g]$$ contains Skolem functions for $$\Pi^0_2$$ formulas with parameters in $$\MN[g]$$ (Corduan-Dorais 2012, Proposition 3.13). Once Skolemized, a $$\Pi^0_2$$ formula becomes $$\Pi^0_1.$$ Because $$\MN'[g]$$ satisfies $$\Ind{\Sigma^0_1}$$ and $$\MN'[g]$$ is an $$\omega$$-extension of $$\MN[g],$$ it follows that $$\MN[g]$$ satisfies $$\Ind{\Sigma^0_2}.$$ So now we can iterate this process externally, taking care of any coloring $$c:\N^2\to\set{0,1}$$ that appears along the way, to obtain a model of $$\HWk\RT22.$$ 

Is this envelope forcing technique useful for anything else? Yes! In fact, the method was inspired by Hirschfeldt and Shore, who used a similar technique in (Hirschfeldt-Shore 2007) for $$\mathsf{SADS}$$ and $$\mathsf{SCAC}.$$ (The main differences are that they use methods from computability theory and they mostly care about $$\omega$$-models, so they have no need for enveloping models.) Let's see how to recast these two examples in terms of envelope forcing. 

Recall that a (countable) linear ordering $$L$$ is stable if every element either has finitely many predecessors or has finitely many successors. Finite linear orderings are stable, and so are the infinite linear orderings $$\omega+n,$$ $$n + \omega^*,$$ and $$\omega+\omega^*.$$ The principle $$\mathsf{SADS}$$ says that these are the only stable linear orderings, which boils down to saying that every infinite stable linear ordering has an infinite ascending or descending sequence. This is not provable in $$\RCA$$ but it is $$\Pi^1_1$$ conservative over $$\RCA + \Ind{\Sigma^0_2},$$ as can be shown by an envelope forcing argument. 

The forcing $$\PP$$ for the infinite stable linear ordering $$L$$ consists of all finite increasing sequences $$p = \seq{p_0,\dots,p_{\ell-1}}$$ of elements of $$L$$ such that $$p_{\ell-1} = \max(p)$$ has only finitely many predecessors in $$L.$$ Note that $$\PP$$ is $$\Sigma^0_2$$-definable over the ground model, so we are in a very similar situation to the above. Hirschfeldt and Shore observed that if $$L$$ has no infinite descending sequence, then $$\PP$$ is relatively large in the partial order $$\PP_0$$ of all finite increasing sequences of elements of $$L.$$ It then follows that an envelope generic for $$\PP$$ is necessarily low over the ground model and we can generically add an increasing sequence to $$L$$ without destroying $$\Ind{\Sigma^0_2}.$$ 

It turns out that $$\HWk\RT22$$ implies $$\mathsf{SADS},$$ but the relationship between $$\HWk\RT22$$ and $$\mathsf{SCAC}$$ is unknown. The methods that Hirschfeldt and Shore used for $$\mathsf{SCAC}$$ can also be recast in terms of envelope forcing. However, rather than doing that, I will present another application of envelope forcing that incidentally forces $$\mathsf{SCAC}.$$ 

**The Path Ramsey Theorem ($$\newcommand{\Pth}{\mathsf{Path}}\Pth\RT2k$$).**
: For every coloring $$c:\N^2\to\set{0,\dots,k-1}$$ there are a color $$d \lt k$$ and an increasing function $$h:\N\to\N$$ such that $$c(h(n),h(n+1)) = d$$ for all $$n$$ (a _$$d$$-homogeneous path_).

As usual, the Stable Increasing Path Ramsey Theorem ($$\newcommand{\St}{\mathsf{S}}\St\Pth\RT2k$$) is the restriction of $$\Pth\RT2k$$ to stable colorings, i.e., colorings $$c:\N^2\to\set{0,\dots,k-1}$$ such that $$\lim_{n\to\infty} c(m,n)$$ exists for every $$m.$$ 

Note that $$\St\Pth\RT22$$ directly implies $$\mathsf{SADS}.$$ The following asymmetric strengthening of $$\St\Pth\RT22$$ directly implies $$\mathsf{SCAC}:$$ 

**The Stable Mixed Ramsey Theorem ($$\newcommand{\Mix}{\mathsf{Mixed}}\St\Mix\RT22$$).**
: For every stable coloring $$c:\N^2\to\set{0,1}$$ either there is an infinite $$0$$-homogeneous set, or an infinite $$1$$-homogeneous path.

The technique of envelope forcing can be used to show that $$\St\Mix\RT22$$ is $$\Pi^1_1$$ conservative over $$\RCA + \Ind{\Sigma^0_2}.$$ The natural forcing $$\PP$$ to add a $$1$$-homogeneous path for a stable coloring $$c:\N^2\to\set{0,1}$$ consists of all finite $$1$$-homogeneous paths $$p = \seq{p(0),\dots,p(\card{p}-1)}$$ such that $$\lim_{n\to\infty} c(p(\card{p}-1),n) = 1.$$ Indeed, this $$\Sigma^0_2$$ condition on $$p$$ guarantees that the path can be continued further, provided that there are infinitely many $$m$$ such that $$\lim_{n\to\infty} c(m,n) = 1.$$ (If there are only finitely many such $$m,$$ it is easy to construct an infinite $$0$$-homogeneous set.) It turns out that if $$c$$ has no infinite $$0$$-homogeneous set in $$\MN$$ then $$\PP$$ is relatively large in the partial order $$\PP_0$$ of all finite $$1$$-homogeneous paths for $$c.$$ 

To see this, suppose $$U \subseteq \PP_0$$ is $$\Sigma^0_1$$-definable over the ground model $$\MN.$$ Suppose further $$p \in \PP$$ is such that for every $$q \leq p,$$ $$q \in \PP,$$ there is an $$r \leq q$$ (in $$\PP_0$$ but not necessarily in $$\PP$$) such that $$r \in U.$$ Finally, for the sake of contradiction, suppose that $$q \leq p$$ is an element of $$\PP$$ that has no extension in $$U \cap \PP.$$ Since $$q \in \PP,$$ there are infinitely many $$n$$ such that $$q{^{\frown}}\seq{n} \in \PP$$ too. So, by an effective search, we can find an infinite sequence $$\seq{r_s}_{s=0}^\infty$$ of extensions of $$q$$ in $$U$$ (in $$\PP_0$$ but not in $$\PP$$) such that the tips $$m_s = r_s(\card{r_s}-1)$$ enumerate an infinite set $$M$$ in increasing order. Since $$q$$ has no extension in $$U \cap \PP,$$ we must have that $$\lim_{n\to\infty} c(m,n) = 0$$ for every $$m \in M.$$ But then it is easy to recursively construct an infinite $$0$$-homogeneous subset of $$M,$$ which contradicts the fact that there are no such sets in $$\MN.$$ 

It follows that $$\St\Mix\RT22$$ is $$\Pi^1_1$$ conservative over $$\RCA + \Ind{\Sigma^0_2},$$ hence so are all of its consequences $$\St\Pth\RT2k,$$ $$\mathsf{SADS},$$ and $$\mathsf{SCAC}.$$ However, this does not separate any of these principles from $$\Wk\RT22$$ or even $$\RT22.$$ To do this, we need to recast the forcing arguments into the language of computability theory. The argument for $$\HWk\RT22$$ gives the following. 

**Theorem.** _If $$c:\N^2\to\set{0,1}$$ is a computable coloring, then one of the following is true_: 

  * _There is a computable increasing function $$h:\N\to\N$$ such that $$\bigcup_{x=h(i-1)}^{h(i)-1} \set{y \in \N : c(x,y) = 0}$$ is infinite for every $$i \geq 1.$$_
  * _There is a $$0'$$-computable $$1$$-generic increasing function $$g:\N\to\N$$ such that $$\bigcup_{x=g(i-1)}^{g(i)-1} \set{y \in \N : c(x,y) = 0}$$ is cofinite for every $$i \geq 1.$$_

It was shown by Downey, Hirschfeldt, Lempp and Solomon (2001) that some computable instances of $$\St\RT22$$ have no low solutions. Since $$\St\RT22$$ follows from $$\Wk\RT22,$$ this shows that there is an instance of $$\Wk\RT22$$ that has no low solutions either. A $${0}'$$-computable $$1$$-generic function is always low, so there is an $$\omega$$-model of $$\HWk\RT22$$ that contains only low sets. This $$\omega$$-model cannot be a model of $$\Wk\RT22,$$ which shows that $$\HWk\RT22$$ does not imply $$\Wk\RT22.$$ 

The argument for $$\St\Mix\RT22$$ gives the following. 

**Theorem.** _If $$c:\N^2\to\set{0,1}$$ is a stable computable coloring, then one of the following is true_: 

  * _There is a computable increasing function $$h:\N\to\N$$ such that $$c(h(i),h(j)) = 0$$ for all $$i \lt j.$$_
  * _There is a $${0}'$$-computable $$1$$-generic increasing function $$g:\N\to\N$$ such that $$c(g(i),g(i+1)) = 1$$ for all $$i.$$_

So $$\St\Mix\RT22$$ does not imply $$\St\RT22.$$ Neither do any of its consequences, such as $$\St\Pth\RT2k,$$ $$\mathsf{SADS}$$ and $$\mathsf{SCAC}.$$ 


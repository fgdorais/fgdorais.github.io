---
title: Paris-Harrington and Typing
date: 2011-10-14 04:44:34
permalink: /archives/107/
published: true
topics: [independence-proofs, set-theory]
tags: [New Foundations, Paris-Harrington Theorem, Peano Arithmetic]
people: [Harvey Friedman, Thomas Forster]
---

I just read an interesting paper by Thomas Forster: [The Paris–Harrington Theorem in an NF context](http://www.dpmms.cam.ac.uk/~tf/parisharringtontalk.pdf). This paper is a progress report on the status of the Paris–Harrington Theorem in Quine's New Foundations (NF). Forster shows that the Paris–Harrington Theorem is at least consistent with NF, but leaves open the question whether it is provable in NF. Recall that the Paris–Harrington Theorem is a variation on Ramsey's Theorem, where the homogeneous set $$x$$ is required to be relatively large: $$\min(x) \lt \vert x \vert$$. This result is not provable in Peano Arithmetic (PA). In fact, it is logically equivalent to $$\Sigma_1$$-reflection for PA. 

The main issue with the Paris–Harrington Theorem in NF is that the notion of relative largeness is ill-typed. In addition to Forster, Harvey Friedman had also observed this on [FOM](http://www.cs.nyu.edu/pipermail/fom/2007-October/012046.html):

> In 'relatively large', an integer is used both as an element of a finite set and as a cardinality (of that same set).

This is a serious problem in NF where cardinal numbers are defined as equivalence classes of equinumerous sets. Thus, the relative largeness condition $$\min(x) \lt \vert x\vert$$ entails a direct comparison between an element of the finite set $$x$$ and the cardinal number $$\vert x\vert$$ to which $$x$$ belongs. Needless to say that this is difficult to formulate in a stratified manner, as required for set comprehension in NF. Forster manages to work around this, but the winding road has so many twists that he only manages to get a consistency result rather than an actual proof. 

While Forster does not directly discuss the issue of the strength of the Paris–Harrington Theorem in the paper, he does raise an interesting question whether the added strength of the theorem has any link to this failure of typing. I used to believe that while the naturalness of the Paris–Harrington Theorem could honestly be questioned, there was one real advantage of this example over the non-provable statements of Gödel and Rosser in that the Paris–Harrington Theorem did not appear to directly depend on self-reference. This observation by Forster and Friedman casts some serious doubts on this... 

  * Is the notion of relative largeness really self-referential?
  * Is the fact that relative largeness is ill-typed the key to the strength of the Paris–Harrington Theorem?

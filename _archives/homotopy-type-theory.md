---
title: Homotopy Type Theory
date: 2013-06-22 16:41:15
permalink: /archives/1425/
published: true
topics: [mathematical-philosophy, proof-theory, type-theory]
tags: [HoTT, Univalence]
---
After a productive year at the Institute for Advanced Study, the Univalent Foundations Program has written a book on [Homotopy Type Theory](http://homotopytypetheory.org/book/) (HoTT). The foreword gives a succinct description of the purpose of this book:

> We did not set out to write a book. The present work has its origins in our collective attempts to develop a new style of "informal type theory" that can be read and understood by a human being, as a complement to a formal proof that can be checked by a machine. Univalent foundations is closely tied to the idea of a foundation of mathematics that can be implemented in a computer proof assistant. Although such a formalization is not part of this book, much of the material presented here was actually done first in the fully formalized setting inside a proof assistant, and only later "unformalized" to arrive at the presentation you find before you — a remarkable inversion of the usual state of affairs in formalized mathematics.

The danger in writing such a book is to fall into the minefields of logic wars. The authors successfully avoided much of these traps, so logicians from other perspectives can read the book without too much cringing. To avoid unnecessary confusion, I recommend mentally substituting most instances of "set theory" by the more apropos "classical mathematics." Readers from strongly opposing points of view should be prepared for a certain amount of propaganda, which is to be expected in a book written to promote one point of view. Barring these caveats, you will find an enjoyable and well-written book on a very interesting subject. Readers should not be too concerned with the word "homotopy" in the title, homotopy theory is not required background for the book though some basic knowledge of the ideas of topology and homotopy theory helps to understand the motivation behind certain concepts.

Having addressed all the necessary caveats, let's talk about why this book is interesting and why you should read it...

* * *

### What is so hot about HoTT?

The most interesting aspect from my point of view is that HoTT fully supports _proof-relevant mathematics_, a way of doing mathematics where proofs are real objects that are manipulated on the same level as numbers, sets, functions and all the usual objects of classical mathematics. This is not a brand new idea, logicians have been playing with proofs in this way for a long while, but HoTT brings this idea into the realm of everyday mathematics and that is a major step forward in mathematics.

The key difference with first-order logic is that equality is not primitive. To define a type $$A$$ one must also define what equality means for $$A$$. Formally if $$x,y:A$$ then $$x =_A y$$ (or $$\mathsf{Id}_A(x,y)$$) is another type, an identity type, which can be thought of as made of reasons to identify $$x$$ and $$y$$. Elements $$p:x =_A y$$ are often called "paths" by analogy with topolgy. Indeed, these paths can be inverted and concatenated to realize symmetry and transitivity of equality, respectively; reflexivity is realized by a path $$\mathsf{refl}_x:x =_A x$$. Thus each type $$A$$ is actually a groupoid rather than a plain set. In fact, since each $$x =_A y$$ is itself a type with its own identity types and so forth, the type $$A$$ is actually a kind of $$\infty$$-groupoid.

It is this rich structure associated with each type is what permits HoTT to support proof relevant mathematics. To get a basic feel of how this works, the statement "$$x =_A y$$ and $$y =_A z$$" is interpreted via the product type $$(x =_A y)\times(y =_A z)$$, whose elements are pairs of paths that explain why $$x$$ is to be identified with $$y$$ and why $$y$$ is to be identified with $$z$$. Similarly, "$$x =_A y$$ or $$y =_A z$$" is interpreted via the coproduct type $$(x =_A y) + (y =_A z)$$, whose elements are either paths that explain why $$x$$ is to be identified with $$y$$ or paths that explain why $$y$$ is to be identified with $$z$$. The catch, as you may have guessed from the last example, is that this form of constructive reasoning is intuitionistic and thus not as familiar to mathematicians.

Interestingly, the learning curve for constructive reasoning appears to be much less steep with HoTT than with other constructive frameworks. One of the reasons is that the topological interpretation of the key concepts is very intuitive but more significantly HoTT provides many tools to revert to more familiar territory. The analogue of a plain set in HoTT is a $$0$$-type: a type $$A$$ where the identity types $$x =_A y$$ always contain at most one path. In other words, these are types where the groupoid structure is trivial and contains no other information than how to handle equality of elements. It is consistent with HoTT that the $$0$$-types form a model of ETCS, a classical theory of sets and functions. Thus, by "truncating" thoughts to $$0$$-types, one can revert to a more familiar classical setting.

* * *

### What is the big deal with univalence?

It is natural to identify things that are not significantly different. For example, the axiom of extensionality in set theory identifies sets that have the same elements since the elements of a set are all that matter in this context. Extensionality for functions identifies functions that agree on all inputs. Univalence is an indiscernibility axiom in the same spirit: it identifies types that are not significantly different.

To make sense of equality for types, we first need to put them in an ambient type, a universe, with its associated identity types. We can't have a truly universal type since that directly leads to the usual paradoxes of self-reference. Instead, we have a bunch of universes such that each type belongs to some universe and each universe is closed under the basic type formation rules. Once we have a universe $$\mathcal{U}$$ we can talk about equality of types in $$\mathcal{U}$$, and because $$\mathcal{U}$$ is a type we have a lot of freedom in defining what equality means for types in $$\mathcal{U}$$.

This is exactly what the univalence axiom does. It can be stated elegantly: 
^
$$(A \simeq B) \simeq (A =_\mathcal{U} B).$$
^
 The equivalence relation $${\simeq}$$ is similar to isomorphism but it is slightly more permissive. To say $$A \simeq B$$ requires the existence of a function $$f:A \to B$$ together with $$\ell,r:B \to A$$ such that $$\ell \circ f$$ is homotopic to $$\mathsf{id}_A$$ and $$f \circ r$$ is homotopic to $$\mathsf{id}_B$$. Given two functions $$f$$ and $$g$$ of the same dependent product type $$\prod_{x:A} B(x)$$, a homotopy from $$f$$ to $$g$$ is an element of $$\prod_{x:A} (f(x) =_{B(x)} g(x))$$. So $$f$$ and $$g$$ are homotopic if they agree on all inputs, which does not mean that $$f = g$$ in the absence of function extensionality.

In general type theory, $$A \simeq B$$ is definitely a good way to say "$$A$$ and $$B$$ are not siginificantly different" and thus univalence arguably captures the right indiscernibility axiom for type theory. The surprising fact is that such a strong axiom does not appear to collapse more than it should. The benefits of univalence are interesting and need to be explored further.

* * *

I still need to digest the book so this is probably only the first of many posts on HoTT. The next posts will undoubtedly wander deeper into the technical levels of HoTT. There are a few interesting leads but nothing definite yet.

There is only one thing that bugs me right now, which is the way universes are handled in the book. However, since these assumptions do not appear to be crucial for the development of HoTT and there are plenty of alternatives out there, I'm not overly concerned about this at the moment.

I will eventually need to talk about higher inductive types. These are really interesting and I'm happy to see that the book devotes an entire chapter to them. This is a very interesting outgrowth of this project and which deserves study even independently of HoTT.

---
title: Super HoTT
date: 2014-01-19 20:31:52
permalink: /archives/1543/
published: true
categories: [type-theory]
tags: [Homotopy Type Theory]
people: [Andrej Bauer, Erik Palmgren]
---
This is a follow-up to my recent post [on the structure of universes in HoTT]({{ "archives/1532" | relative_url }}). In this post I will outline one of the possible alternative ways of handling universes in HoTT, which I will colorfully call Super HoTT for the time being. This is not an original idea; something like that (not in the context of HoTT) can be found in Erik Palmgren's paper [On Universes in Type Theory](http://www2.math.uu.se/~palmgren/universe.pdf).[^1] The idea comes from a [comment by Andrej Bauer]({{ "archives/1532" | relative_url | append: "#13902306230" }}) where he described a universe as "a structure $$(\mathcal{U},\tau,\pi,\sigma,\ldots)$$ where $$\mathcal{U}$$ is a type, $$\tau$$ is a type family indexed by $$\mathcal{U},$$ $$\pi$$ and $$\sigma$$ compute codes of dependent products and dependent sums, etc." This is a perfectly reasonable way of describing universes. By the Foundational Thesis of HoTT, this approach should be formalizable in some flavor of HoTT. This is indeed possible and the flavor (or rather flavor family) Super HoTT is one way to do that.

The issue with Bauer's description is the type family $$\tau.$$ Formally, a type family indexed by a type $$\mathcal{U}$$ is an element $$\tau:\mathcal{U}\to\mathcal{V},$$ where $$\mathcal{V}$$ is some larger universe. This type $$\tau$$ becomes a type family only after applying Tarski-style coercion associated to $$\mathcal{V}$$ that promotes elements of $$\mathcal{V}$$ to actual types. On the face of it, this is circular: $$\tau$$ is the Tarski-style coercion associated to the universe $$\mathcal{U},$$ which is defined in terms of that of $$\mathcal{V},$$ which...

One way to break this circularity is to have a designated _super universe_ $$\mathcal{U}^\ast$$ — hence the name Super HoTT — whose associated Tarski-style coercion and associated machinery are implemented in the formal system itself. In particular, $$\mathcal{U}^\ast$$ is associated to a primitive decoding function $$T$$ such that $$T(A)\ \mathsf{type}$$ for any element $$A:\mathcal{U}^\ast.$$ In Super HoTT, this is the only such decoding function. Other universes arise à la Bauer, i.e., as structures $$(\mathcal{U},\tau,\pi,\sigma,\ldots)$$ where now $$\tau:\mathcal{U}\to\mathcal{U}^\ast$$ is a type family that realizes this universe's Tarski-style coercion via composition with the super universe's decoding function $$T.$$ In fact, since there is only one super universe, the Russell-style approach doesn't lead to many problems. In other words, there is little harm in suppressing the decoding function $$T$$ in favor of a simple Russell-style rule 
^
$$\frac{A:\mathcal{U}^\ast}{A\ \mathsf{type}}.$$
^
 In fact, the $$\mathsf{type}$$ judgment is often informally confounded with an actual universal type $$\mathsf{Type}.$$ This type of identification can lead to serious issues such as Girard's Paradox; the super universe approach is one of the many safe ways around these problems.

So far, this is pure type theory, we haven't said anything HoTT specific. To make this a flavor of HoTT, we postulate that there are enough _univalent_ universes or even lots of them. Universes à la Bauer are mere structures, they can be univalent or not, they can have extra structure or lack some structure. Univalent universes can be identified among these structures so we can formalize a rule saying that any two $$A,B:\mathcal{U}^\ast$$ are contained in a univalent universe. One can also formalize rules saying that one can have cumulative univalent universes, cumulative univalent universes with propositional resizing, cumulative classical univalent universes, etc. The possibilities for specialized flavors of Super HoTT are vast and varied!

Note that the super universe doesn't have to be univalent. It doesn't need to have much fancy structure at all. It's not even necessary for $$\mathcal{U}^\ast$$ to have a natural number type. All of that can happen inside the univalent universes à la Bauer. In fact, a bare-bones super universe is probably more flexible framework than a rich one. Different choices of structure for the super universe and how it interacts with the universes inside it will lead to different flavors of Super HoTT with variable strength. Richer super universe structure allows one to express stronger and stronger properties for the univalent universes it contains.

One advantage of this approach is that universes can arise "on their own" in the sense that any suitable structure $$(\mathcal{U},\tau,\pi,\sigma,\ldots)$$ is a universe, no matter how it comes about. Though this can be a mixed blessing if one wants more hands-on control over which types are universes. One potential drawback of Super HoTT is that not all types can belong to univalent universes. In particular, the super universe $$\mathcal{U}^\ast,$$ cannot belong to any univalent universe inside $$\mathcal{U}^\ast.$$ In this way, Super HoTT is more like $$\mathsf{NBG}$$ or $$\mathsf{MK}$$ than $$\mathsf{ZF}.$$ For ontological reasons, it might be preferable to have a more self-contained system analogously to $$\mathsf{ZF}.$$ In any case, Super HoTT is one of the more flexible formal ways of handling universes in HoTT and it is a perfectly viable alternative to the formal system presented in the appendix of the [HoTT book](http://homotopytypetheory.org/book/).[^2]

---

[^1]: E. Palmgren, On universes in type theory. In Twenty-five years of constructive type theory (Venice, 1995), Oxford Logic Guides 36, Oxford University Press, New York, 1998, pages 191–204.

[^2]: Univalent Foundations Program, Homotopy Type Theory: Univalent Foundations of Mathematics, Institute for Advanced Study, Princeton, 2013.

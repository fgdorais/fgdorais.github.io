---
title: "HoTT Math 2: More on equational logic"
date: 2013-07-14 16:03:09
permalink: /archives/1476/
published: true
topics: [type-theory]
tags: [Equational Logic, Homotopy Type Theory, Universal Algebra]
people: [Garrett Birkhoff]
---
Last time, I promised we would look at fields. I have to delay this by one or two installments of HoTT Math since there is so much to say and I am struggling to keep these short. This edition of HoTT Math is a continuation of the first. The main lesson of [HoTT Math 1]({{ "archives/1438" | relative_url }}) was that equational logic still works, provided you're careful enough. As I was working through some algebra, I realized that I should have been more precise and nuanced. To make things more precise, I will briefly recall some basic universal algebra and then I will talk a little about Birkhoff's soundness and completeness theorem for equational logic.

* * *

A _signature_ is a sequence $$\sigma$$ of sets indexed by natural numbers. The elements of the set $$\sigma_n$$ are intended to be symbols for $$n$$-ary operations ($$0$$-ary operations are simply constants). For example, the signature for rings can be thought as 
^
$$(\set{0,1},\set{-},\set{+,\cdot},\varnothing,\varnothing,\dots).$$
^
 It is generally assumed that the sets $$\sigma_n$$ are mutually disjoint so that each symbol has a definite arity. In the end, only the cardinality of the sets $$\sigma_n$$ matters since the particular symbols used for the operations is mostly a matter of taste.

The logic of universal algebra is equational logic. The symbols from the signature $$\sigma$$ can be strung together to form terms. In addition to the symbols from $$\sigma$$, we need an infinite set $$\\{x_0,x_1,x_2,\dots\\}$$ of variable symbols. Formally, terms are defined inductively using the two rules:

  * Every variable symbol is a term.
  * If $$t_1,\dots,t_n$$ are terms and $$f$$ is an element of $$\sigma_n$$, then $$ft_1\dots t_n$$ is also a term.

Equational logic deals with identities of the form $$t \approx s$$ where $$t$$ and $$s$$ are terms. The rules for equational logic are reflexivity, symmetry, transitivity 
^
$$\frac{}{t \approx t}, \quad \frac{t \approx s}{s \approx t}, \quad \frac{t \approx s, s \approx r}{t \approx r}$$
^
 together with substitution and replacement 
^
$$\frac{t \approx s}{t[x/r] \approx s[x/r]}, \quad \frac{s \approx r}{t[x/r] \approx t[x/s]},$$
^
 where $$[x/r]$$ denotes the act of replacing every occurrence of the variable symbol $$x$$ with the term $$r$$. We write $$\Gamma \vdash t \approx s$$ to signify that the identity $$t \approx s$$ follows using a combination of these rules from the identities in $$\Gamma$$.

An algebra $$\mathfrak{A}$$ (with signature $$\sigma$$) is a type $$A$$ together with an interpretation 
^
$$I:\left({\textstyle\sum_{n:\mathbb{N}} \sigma_n \times A^n}\right) \to A.$$
^
 If $$f$$ is a symbol for an $$n$$-ary operation in $$\sigma_n$$, then the interpretation $$f^{\mathfrak{A}}:A^n \to A$$ is 
^
$$f^{\mathfrak{A}}(a_1,\dots,a_n) := I(f,a_1,\dots,a_n).$$
^
 These interpretations can be used to evaluate any term starting from a variable assignment $$\mathcal{V}:\mathbb{N}\to A$$ in the usual recursive manner: 
^
$$x_i^{\mathfrak{A},\mathcal{V}} := \mathcal{V}(i), \quad (f t_1 \dots t_k)^{\mathfrak{A},\mathcal{V}} := f^{\mathfrak{A}}(t_1^{\mathfrak{A},\mathcal{V}},\dots,t_k^{\mathfrak{A},\mathcal{V}}).$$
^
 The satisfaction relation for the algebra $$\mathfrak{A}$$ and the identity $$t \approx s$$ is then the type 
^
$$(\mathfrak{A} \vDash t \approx s) :\equiv \prod_{\mathcal{V}:\mathbb{N}\to A} (t^{\mathfrak{A},\mathcal{V}} =_A s^{\mathfrak{A},\mathcal{V}}).$$
^
 If the carrier $$A$$ is a set then each identity type $$t^{\mathfrak{A},\mathcal{V}} =_A s^{\mathfrak{A},\mathcal{V}}$$ has at most one element and hence $$\mathfrak{A} \vDash t \approx s$$ is a proposition with the usual meaning. In the general case, $$\mathfrak{A} \vDash t \approx s$$ can carry substantial path information.

The fact that equational logic is sound and complete for the semantics is called Birkhoff's Theorem: 
^
$$\Gamma \vdash t \approx s \quad\text{if and only if}\quad \Gamma \vDash t \approx s.$$
^
 Clasically, the right hand side means that every algebra $$\mathfrak{A}$$ with signature $$\sigma$$, _whose carrier $$A$$ is a set_, that satisfies all equations in $$\Gamma$$ also satisfies $$t \approx s$$. In HoTT, this translates to the type 
^
$$(\Gamma \vDash_{\operatorname{set}} t \approx s) :\equiv \prod_{\mathfrak{A}/\operatorname{set}} \left(\prod_{u \approx v:\Gamma} (\mathfrak{A} \vDash u \approx v) \to (\mathfrak{A} \vDash t \approx s)\right)$$
^
 where the outer product is over all set-based algebras $$\mathfrak{A}$$ with signature $$\sigma$$. An alternate interpretation is 
^
$$(\Gamma \vDash_{\operatorname{any}} t \approx s) :\equiv \prod_{\mathfrak{A}/\operatorname{any}} \left(\prod_{u \approx v:\Gamma} (\mathfrak{A} \vDash u \approx v) \to (\mathfrak{A} \vDash t \approx s)\right)$$
^
 where the outer product is over algebras with signature $$\sigma$$ based on any type. Consequently there are two possible ways to interpret Birkhoff's Theorem in HoTT!

The first is closest to the classical version:

**Weak Birkhoff Theorem.** _$$\left\Vert\Gamma \vdash t \approx s\right\Vert$$ is equivalent to $$\Gamma \vDash_{\operatorname{set}} t \approx s$$._

The vertical lines $$\Vert\square\Vert$$ indicate that one should take the propositional truncation of $$\Gamma \vdash t \approx s$$ (§3.7). Indeed, when translated into HoTT, $$\Gamma \vdash t \approx s$$ is the type of all proofs of $$t \approx s$$ from $$\Gamma$$ in equational logic. The propositional truncation agglomerates all these proofs into one and simply asserts the unqualified existence of such a proof. This is necessary since the right hand side $$\Gamma \vDash_{\operatorname{set}} t \approx s$$ is a proposition so the backward implication, without propositional truncation, would amount to a canonical choice of proof with basically no information.

On the other hand, $$\Gamma \vDash_{\text{any}} t \approx s$$ is much more expressive because of all the possible identity paths. With all that information on hand, it is not so unlikely that we could reconstruct a proof. This suggests another interpretation of Birkhoff's Theorem:

**Strong Birkhoff Theorem.** _$$\Gamma \vdash t \approx s$$ is equivalent to $$\Gamma \vDash_{\operatorname{any}} t \approx s$$._

As I stated it just now, this is unlikely to be true. However, I suspect it becomes true with some tweaking of $$\Gamma \vdash t \approx s$$ to only allow proofs that are normalized in some sense or to formally identify proofs that are trivial variations of each other. I haven't had much time to think about this so I'll leave it as an open conjecture for now and hope that I can come back to it later...

The soundness part (forward implication) of both forms are true. Last time, I emphasized the usefulness of the weak soundness theorem but I forgot to talk about substitution and replacement! We did talk about how paths could be reversed and composed to get symmetry and transitivity; details are in §2.1 of the book. Since I think it's important to know what goes on behind the scenes, let's talk about the remaining two rules. Unfortunately, and this explains the earlier omission, neither is particularly pleasant.

Substitution works exactly as you expect. An element $$p:(\mathfrak{A} \vDash t \approx s)$$ is a function that maps each variable assignment $$\mathcal{V}:\mathbb{N}\to A$$ to a path $$p(\mathcal{V}):t^{\mathfrak{A},\mathcal{V}} =_A s^{\mathfrak{A},\mathcal{V}}$$. Given a term $$r$$ and a variable $$x$$, the corresponding element of $$(\mathfrak{A} \vDash t[x/r] \approx s[x/r])$$ is the composition of $$p$$ with the function that sends each variable assignment $$\mathcal{V}:\mathbb{N}\to A$$ to the assignment where all values stay the same except that the value of $$x$$ is changed to $$r^{\mathfrak{A},\mathcal{V}}$$. Verifying that the result really is an element of $$\mathfrak{A} \vDash t[x/r] \approx s[x/r]$$ is a tedious computation which is best performed under a rug.

The trick behind replacement is revealed in §2.2: _functions are functors_. The identity types give each type a higher groupoid structure and functions act functorially in the sense that with any $$f:A \to B$$ comes with more functions $$\mathsf{ap}_f$$ which translate paths $$p:x =_A y$$ into paths $$\mathsf{ap}_f(p):f(x) =_B f(y)$$. The details for soundness of the replacement rule are gory but they are essentially the same as in the classical proof. There is some work needed to single out the variable $$x$$ and interpret the term $$t$$ as a function $$t^{\mathfrak{A},\mathcal{V}}_x:A \to A$$ where all other variables are fixed. Then, $$\mathsf{ap}_{t^{\mathfrak{A},\mathcal{V}}_x}$$ can be used to transform paths $$s^{\mathfrak{A},\mathcal{V}} =_A r^{\mathfrak{A},\mathcal{V}}$$ into paths $$t^{\mathfrak{A},\mathcal{V}}_x(s^{\mathfrak{A},\mathcal{V}}) =_A t^{\mathfrak{A},\mathcal{V}}_x(r^{\mathfrak{A},\mathcal{V}})$$. Thus, we obtain 
^
$$(\mathfrak{A} \vDash s \approx r) \to (\mathfrak{A} \vDash t[x/s] \approx t[x/r]).$$
^


Since each rule of equational logic is sound, we therefore have the strong soundness $$(\Gamma \vdash t \approx s) \to (\Gamma \vDash_{\operatorname{any}} t \approx s)$$. To get weak soundness, we compose this with the obvious implication $$(\Gamma \vDash_{\operatorname{any}} t \approx s) \to (\Gamma \vDash_{\operatorname{set}} t \approx s)$$ and we conclude that $$\left\Vert\Gamma \vdash t \approx s\right\Vert \to (\Gamma \vDash_{\operatorname{set}} t \approx s)$$ from the fact that $$\Gamma \vDash_{\operatorname{set}} t \approx s$$ is a proposition. The completenesss part of Birkhoff's theorem uses syntactic algebras and HoTT has a really neat way to construct these that we will talk about in a later HoTT Math post.

* * *

In conclusion, equational logic works just fine in HoTT. In general, because of proof relevance, it is best to keep track of the equational proofs in order to keep track of the identity paths. The strong soundness map 
^
$$(\Gamma \vdash t \approx s) \to (\Gamma \vDash_{\operatorname{any}} t \approx s)$$
^
 guarantees that equational proofs will lead to identities, but different proofs can lead to different identity paths! When the carrier is a set, less care is necessary, the weak soundness map 
^
$$\Vert\Gamma \vdash t \approx s\Vert \to (\Gamma \vDash_{\operatorname{set}} t \approx s)$$
^
 shows that the mere existence of an equational proof leads to the desired identities. This is exactly how algebra and equational logic are used classically.

---
title: Scheming schemes...
date: 2012-08-15 20:22:16
permalink: /archives/1080/
published: true
categories: [model-theory, reverse-math, set-theory]
tags: [MathOverflow, Reflection Principles]
people: [Joel David Hamkins]
---
In everyday language, the word scheme often has a negative connotation: scheme is used as a synonym for devious plan. In mathematical language, the word has no negative aspect at all. In fact, I think that mathematical schemes of all kinds are wonderful things and it often takes me a moment to understand when someone uses scheme to imply wrongful intent. This can lead to awkward social situations, but what I want to talk about here is how axiom schemes can sometimes behave badly and may lead to awkward mathematical situations. 

The main source of problems with axiom schemes is when one tries to internalize them in models with non-standard numbers. Many common theories, such as $$\mathsf{ZFC}$$ and $$\mathsf{PA}$$, include axiom schemes. Namely, comprehension and replacement are axiom schemes that are part of $$\mathsf{ZFC}$$, and induction is an axiom scheme that is part of $$\mathsf{PA}$$. These axiom schemes are infinite collections of axioms that can be enumerated by a straightforward process. When internalized, these are understood to be infinite lists of Gödel codes for sentences enumerated by a primitive recursive function. This is the source of problems: when a model has non-standard numbers, these can be understood as Gödel numbers for sentences in the scheme even though their meaning is rather dubious. 

It's not hard to imagine how this can lead to awkward situations, but these situations don't always have negative outcomes. Here is a wonderful and confounding fact that I learned from Joel David Hamkins on [MathOverflow](http://mathoverflow.net/q/15685): 
> Every model of $$\mathsf{ZFC}$$ contains a model of $$\mathsf{ZFC}$$!

This appears to contradict the second incompleteness theorem, but it does not because of a subtle ambiguity in the meaning of $$\mathsf{ZFC}$$. The following statement is false: 

> Every model $$V$$ of $$\mathsf{ZFC}$$ contains an $$U$$ such that $$V \vDash$$ "$$U \vDash \sigma$$ for every axiom $$\sigma$$ of $$\mathsf{ZFC}$$".

What the above theorem is intended to say is: 

> Every model $$V$$ of $$\mathsf{ZFC}$$ contains an $$U$$ such that $$V \vDash$$ "$$U \vDash \sigma$$" for every axiom $$\sigma$$ of $$\mathsf{ZFC}$$.

The difference is that the first statement requires $$U$$ to satisfy all sentences that $$V$$ believes are part of $$\mathsf{ZFC}$$, possibly including some non-standard sentences, but the second statement only requires $$U$$ to satisfy the standard axioms of $$\mathsf{ZFC}$$.[^1]

Subtleties like the above can be very confounding. A trained eye can usually sort things out but this is not always easy even if one knows what to look for. Here is one such situation that I recently ran into in the context of reverse mathematics. The following statement is something that I could say in a reverse mathematics talk: 

> $$\mathsf{ACA}_0^+$$ is equivalent to every set is contained in a countable coded $$\omega$$-model[^2] of $$\mathsf{ACA}_0$$.

There are a handful of immediate issues with this statement. For example, it's not clear what the base theory is, but these omissions are due to standard conventions in reverse mathematics: base theory is $$\mathsf{RCA}_0$$ unless stated otherwise. I recently had to explain this particular statement to a colleague who does not regularly dabble with reverse mathematics, so I had to be very careful to avoid major traps. That process turned out to be much more tedious than expected. After going through it, I'm not even sure a seasoned reverse mathematician would necessarily interpret this correctly! 

The difficulty lies with the precise meaning of $$\mathsf{RCA}_0$$, $$\mathsf{ACA}_0$$, and $$\mathsf{ACA}_0^+$$. Although these theories are usually stated in terms of comprehension schemes, they are all finitely axiomatizable.[^3] This is usually not a problem but these theories are so weak that the equivalence of these axiomatizations breaks down in very subtle ways when they are internalized. From the syntactic point of view there is no problem; all of these theories contain a sufficiently robust fragment of first-order arithmetic. The situation is vastly more complex from the point of view of semantics. Indeed, $$\mathsf{ACA}_0^+$$ is the weakest subsystem of second-order arithmetic where semantics work as one would normally expect. The situation degenerates quickly in weaker subsystems to the point where the analysis of model-theoretic statements over $$\mathsf{RCA}_0$$ actually requires a substantially different definition of model from the one used in model theory textbooks.[^4]

All of these systems can handle countable coded structures $$\mathfrak{A} = (A;\ldots)$$ which consist of a base set $$A$$ (of natural numbers) and appropriate interpretations for the constant, function and relation symbols of a countable language. This amounts to specifying the atomic diagram of the structure $$\mathfrak{A}$$. However, for serious work, we often need the elementary diagram of $$\mathfrak{A}$$. It turns out that the subsystem $$\mathsf{ACA}_0^+$$ is equivalent (over $$\mathsf{RCA}_0$$) to every countable coded structure has an elementary diagram. So, when we work in weaker subsystems, we need to find ways to work around the fact that the elementary diagram of a structure is not always available. 

In order to determine whether $$\mathfrak{A} \vDash \sigma$$, we don't actually need the full elementary diagram of $$\mathfrak{A}$$, the part of the elementary diagram that contains $$\sigma$$ and all of its subformulas suffices. Since $$\sigma$$ only has finitely many subformulas, the usual computations only require finitely many compound instances of arithmetic comprehension rather than infinitely many for the full elementary diagram. When $$\sigma$$ is a standard formula $$\mathsf{ACA}_0$$ is enough to carry this out, but if we want to evaluate $$\mathfrak{A} \vDash \sigma$$ in this way for non-standard formulas we need a slight extension which is usually denoted $$\mathsf{ACA}'_0$$. So, if we apply this to the situation we're interested in, $$\mathsf{ACA}_0$$ can make sense of countable coded $$\omega$$-model of $$\mathsf{ACA}_0$$ when $$\mathsf{ACA}_0$$ is understood using it's finite axiomatization, but $$\mathsf{ACA}'_0$$ is needed to make sense of this using the more common formulation of $$\mathsf{ACA}_0$$ which uses the axiom scheme of arithmetic comprehension. 

The situation is even worse over $$\mathsf{RCA}_0$$ since we aren't necessarily able to perform even the first step of the usual computation to check whether $$\mathfrak{A} \vDash \sigma$$. We can still work around this for standard formulas by directly translating them into the language of second-order arithmetic. For example, if the language has a binary relation symbol $$E$$ which is interpreted by $$E^{\mathfrak{A}}$$ in the countable coded structure $$\mathfrak{A}$$, we can translate 
^
$$\mathfrak{A} \vDash \forall x \forall y(\forall z(z \mathrel{E} x \liff z \mathrel{E} y) \lthen x = y)$$
^
 to 
^
$$(\forall x, y \in A)((\forall z \in A)((z,x) \in E^{\mathfrak{A}} \liff (z,y) \in E^{\mathfrak{A}}) \lthen x = y).$$
^
 Using this process for every sentence of the finite axiomatization of $$\mathsf{ACA}_0$$, we can make adequate sense of countable coded $$\omega$$-model of $$\mathsf{ACA}_0$$ but there is no hope to make sense of this using the axiom scheme of arithmetic comprehension. 

Now we know what is actually meant by: 

> $$\mathsf{ACA}_0^+$$ is equivalent (over $$\mathsf{RCA}_0$$) to every set is contained in a countable coded $$\omega$$-model of $$\mathsf{ACA}_0$$.

Since I had never gone through all the finer details, I always thought that this fact as more or less self-evident.[^4] However, with all the extra baggage we put into it, it's really not that obvious anymore. In fact, the most straightforward argument I know actually walks backward through all the decoding steps above. First show that every set is contained in a countable coded $$\omega$$-model of $$\mathsf{ACA}_0$$ (in the $$\mathsf{RCA}_0$$ sense) implies $$\mathsf{ACA}_0$$. Then argue that every set is contained in a countable coded $$\omega$$-model of $$\mathsf{ACA}_0$$ (in the $$\mathsf{ACA}_0$$ sense) implies $$\mathsf{ACA}_0^+$$. The whole argument is not difficult but it is definitely not self-evident! 

---

[^1]: The proof of the confounding statement involves more than just the fact that $$\mathsf{ZFC}$$ is not finitely axiomatizable. Because of the reflection theorem, $$\mathsf{ZFC}$$ proves that every standard finite fragment of itself is satisfiable. Therefore, in every model of $$\mathsf{ZFC} + \lnot\operatorname{Con}(\mathsf{ZFC})$$, the root cause of the perceived inconsistency must be some of the dubious non-standard axioms and cannot be a non-standard consequence of the standard axioms alone.

[^2]: A countable coded $$\omega$$-model is a second-order structure $$(\mathbb{N},S;0,1,{+},{\times},{\lt},{\varepsilon})$$ where the arithmetical part $$(\mathbb{N};0,1,{+},{\times},{\lt})$$ is inherited from the ambient model but $$S$$ and $${\varepsilon} \subseteq \mathbb{N}\times S$$ are arbitrary. Typically, one just specifies the sequence of sets $$X_i = \lbrace n \in \mathbb{N} : n \mathrel{\varepsilon} i\rbrace$$ for $$i \in S$$ in some way or another since the rest of the structure is implied. The term $$\omega$$-model is a bit of a misnomer since this will be a non-standard model if the ambient model is non-standard, but it is exactly what the ambient model thinks $$\omega$$-models are.

[^3]: The fact that $$\mathsf{RCA}_0$$, $$\mathsf{ACA}_0$$, and $$\mathsf{ACA}_0^+$$ are finitely axiomatizable ultimately boils down to the existence of a universal Turing machine. These finite axiomatizations are not frequently used since they obscure the intended meaning of these theories.

[^4]: When analyzing theorems from model theory over $$\mathsf{RCA}_0$$, it makes sense to modify the usual definition of model to include the full elementary diagram as an integral part of the model. Indeed, without this modification we can barely make sense of countable models for finite theories so most theorems of model theory cannot even be formulated without this hack. However, countable coded $$\omega$$-models of second-order arithmetic play a different role in reverse mathematics and it makes more sense to think about them in the usual sense.

---
title: Diaconescu's Theorem
date: 2012-07-18 16:31:24
permalink: /archives/1031/
published: true
categories: [mathematical-philosophy, set-theory]
tags: [Axiom of Choice, Excluded Middle, Intuitionistic Logic]
people: [Per Martin-Löf, Peter Aczel, Radu Diaconescu]
---
{% include t.cite _='Dia75r' %} showed that the Axiom of Choice implies the Principle of Excluded Middle. More specifically, he showed that every topos that satisfies (a very mild form of) the Axiom of Choice is Boolean. Diaconescu's argument applies in many other contexts too. In this post, I will present a variant of that argument. I will keep the context of the argument deliberately ambiguous to demonstrate its broad applicability. 

A set $$a$$ is **decidable** if $$x = y \lor x \neq y$$ holds for all $$x, y \in a.$$ In other words, $$a$$ is decidable if the diagonal $$\set{(x,x) : x \in a}$$ is complemented in $$a \times a.$$ The empty set and singleton sets are trivially decidable, but some more complicated sets are decidable too. For example, one can use induction to show that the set of natural numbers is decidable. This and the following fact shows that every set of natural numbers, in particular $$\set{0,1},$$ is also decidable. 

_If $$r:b \to a$$ is an injection and $$a$$ is decidable then $$b$$ is also decidable._

This is because an $$r:b \to a$$ is an injection precisely when $$r(x) = r(y) \liff x = y$$ for all $$x,y \in b.$$ Since $$r(x) = r(y) \lor r(x) \neq r(y)$$ by hypothesis, we conclude that $$x = y \lor x \neq y$$ too. A set $$a$$ is **choice** if every surjection $$q:a \to b$$ splits (there is a map $$r:b \to a$$ such that $$qr = 1_a$$). Thus, the Axiom of Choice says that every set is choice. Decidability and choiceness play together very well. 

_If $$q:a \to b$$ is a surjection and $$a$$ is a decidable choice set, then $$b$$ is also a decidable choice set._

Indeed, the surjection $$q:a \to b$$ has a splitting $$r:b \to a$$ which is necessarily an injection; it follows that $$b$$ is decidable. To see that $$b$$ is choice, suppose that $$p:b \to c$$ is a surjection. Then $$pq:a \to c$$ is a surjection too and therefore there is a splitting $$s:c \to a$$ such that $$pqs = 1_a.$$ But then $$qs:c \to b$$ is a splitting of $$p:b \to c.$$ 

_If $$\set{0,1}$$ is a choice set then equality is decidable._

To see this, note that for all $$x,y$$ we have a surjection $$\set{0,1}\to\set{x,y}.$$ Since $$\set{0,1}$$ is decidable, it follows that if $$\set{0,1}$$ is a choice set then $$\set{x,y}$$ is decidable (and choice), hence $$x = y \lor x \neq y.$$ 

Now given a formula $$\phi,$$ we may use comprehension to form the set $$p = \set{x \in \set{0} : \phi}$$ (where $$x$$ does not occur free in $$\phi$$). Since $$p = \set{0} \liff \phi,$$ we see that $$\phi \lor \lnot\phi.$$ This completes the proof that: 

_If $$\set{0,1}$$ is a choice set then the Principle of Excluded Middle holds._

As you can see, the above argument goes through with very few assumptions. Pairing alone can be used to construct $$\set{0,1},$$ $$\set{x,y}$$ and even the graph of the surjection $$\set{0,1}\to\set{x,y}.$$ We implicitly used the set of natural numbers but we didn't really need the entire set of natural numbers. We only used the fact that $$0 \neq 1$$ and any two distinct objects $$a$$ and $$b$$ would work just as well. So pairing and nontriviality are sufficient to show that equality is decidable. Finally, we used a rather tame form of comprehension to get the decidability of any formula. Although some set theories do restrict comprehension, they all allow a certain amount of comprehension and this argument still has nontrivial conclusions in such contexts. 

A side effect of this result is the implausibility of set-theoretic semantics for constructive mathematics. Indeed, constructivism rejects the Principle of Excluded Middle but accepts the Axiom of Choice since choice is implicit in the constructive meaning of existence. So constructivism is incompatible with Diaconescu's result. How is this possible? The argument I presented looks perfectly constructive except perhaps for the ultimate use of comprehension, which could be impredicative. Even then, decidability of equality is enough to demonstrate incompatibility since constructivists reject the decidability of equality for real numbers. 

It so happens that one very important aspect of the argument is non constructive. It is so well hidden that you probably haven't noticed how often the Axiom of Extensionality was used in the above argument! Extensionality is not compatible with constructivism since constructions are inherently intensional. In a constructive set, each element comes with extra baggage. It is that extra baggage that allows us to choose elements from inhabited sets. So if we accept the above justification for the Axiom of Choice then we must reject the Axiom of Extensionality. In this context, Diaconescu's result only tells us that intensional equality is decidable: we can always tell whether the processes that generate $$x$$ and $$y$$ are the same or different. Whether the outcome of two processes is the same or not is an entirely different matter. To make the doubleton $$\set{x,y}$$ extensional, we should include all possible ways of constructing $$x$$ and $$y.$$ With all this extra baggage, we may not have a surjection $$\set{0,1}\to\set{x,y}$$ and the argument falls apart. 

Of course, there are constructive theories that are extensional, such as Aczel's CZF, but these theories reject the Axiom of Choice. On the other hand, Martin-Löf's constructive type theory (ML) is an example of an intensional constructive theory. Ironically, Aczel's interpretation of CZF in ML makes extensive use of the fact that ML validates the Axiom of Choice. 


{% include cite.md %}

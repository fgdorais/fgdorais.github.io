---
title: Santa Exists!
date: 2011-10-15 15:38:37
permalink: /archives/317/
published: true
categories: [mathematical-philosophy, proof-theory, set-theory]
tags: [Intuitionistic Logic, Minimal Logic, Russell's Paradox, Self-Reference]
people: [Bertrand Russell, Haskell Curry]
---
Here is a theorem that I like to mention during the first week when I teach set theory. 

**Theorem.** _Santa exists!_

_Proof._ Consider the set 
^
$$S = \set{X : X \in X \lthen \text{Santa exists}}.$$
^
 Then $$S \in S \liff (S \in S \lthen \text{Santa exists}).\tag{🎅}\label{hohoho}$$ The forward implication of \eqref{hohoho} gives that 
^
$$S \in S \lthen \text{Santa exists}.$$
^
 But then, the backward implication of $$(*)$$ gives that $$S \in S.$$ 

Knowing that $$S \in S$$ and $$S \in S \lthen \text{Santa exists}$$, we conclude that Santa does exist! _QED_

As you probably noticed, this is actually a disguised version of Russell's Paradox, which is due to Haskell Curry. Should Santa fail to exist, $$S$$ would simply become the usual paradoxical set $$R = \set{X : X \notin X}$$ (but we all know that $$S$$ simply consists of all sets). 

What I like about this variant of Russell's Paradox is that it does not rely on the law of excluded middle.[^1] The usual argument for Russell's Paradox proceeds by reaching a contradiction from $$R \in R$$ and another contradiction from $$R \notin R$$. In order to reach a final contradiction, this argument assumes that $$R \in R \lor R \notin R$$ is true, so all of your intuitionist students will immediately be disappointed. 

On the other hand, Curry's Paradox works even in minimal logic! The only sketchy step is the deduction of $$S \in S \lthen \text{Santa exists}$$ from \eqref{hohoho}. The forward implication actually is 
^
$$S \in S \lthen (S \in S \lthen \text{Santa exists})$$
^
 and the desired conclusion is reached by contraction (the fact that assuming $$S \in S$$ twice is not more powerful than assuming it once). Odds are that very few students will bother counting how many times the assumption $$S \in S$$ is used in this step. 

This shows that self-reference is not a problem unique to classical logic. It applies equally well to intuitionistic and minimal logic. In fact, to avoid self-referential paradoxes through logic it seems necessary to reject the contraction rule (as in linear logic). This is rather extreme from the foundational perspective, so we're probably better off resolving self-referential issues by other means. 

My personal conclusion from this story is that logicians will never be out of work... so Santa does exist!!! 

---

[^1]: As Andreas Blass pointed out in the comments, one can derive Russell's Paradox in intuitionistic logic. (By the same argument, replacing Santa exists by $$\bot$$.) The real strength of Curry's Paradox is that it does not even use negation!

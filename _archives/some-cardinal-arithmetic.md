---
title: Some Cardinal Arithmetic
date: 2014-11-09 20:09:55
permalink: /archives/1593/
published: true
topics: [combinatorics, set-theory]
tags: [Axiom of Choice, Cardinal Arithmetic]
people: [Asaf Karagila, Harvey Friedman, Peter Krautzberger]
---
Some time ago, Asaf Karagila wrote [wonderful post](http://boolesrings.org/asafk/2013/provable-equality-of-exponentiation) wherein he shows that, even without assuming the axiom of choice one can always find four cardinals $$\mathfrak{p} \lt \mathfrak{q}$$ and $$\mathfrak{r} \lt \mathfrak{s}$$ such that $$\mathfrak{p}^{\mathfrak{r}} = \mathfrak{q}^{\mathfrak{s}}.$$ In the comments, [Harvey Friedman asks](http://boolesrings.org/asafk/2013/provable-equality-of-exponentiation/#comment-2024):

> Your theorem is an example of an existential sentence about cardinals in the language with only $$\lt $$ and exponentiation. Can you determine which sentences in that language are provable in ZF? More generally, expand the set of sentences about cardinals considered, obviously to include addition and multiplication, and perhaps alternating quantifiers.

After [Peter Krautzberger's tiny blogging challenge](http://boolesrings.org/krautzberger/2014/11/03/tiny-blogging-challenge), I decided to spend 30 minutes thinking and writing about this...

I will allow myself some liberties in interpreting Friedman's open ended question. The celebrated solution of [Hilbert's Tenth Problem](http://en.wikipedia.org/wiki/Hilbert%27s_tenth_problem) by Davis, Matiyasevich, Putnam and Robinson shows that the existential theory of the finite cardinal numbers (even without exponentiation) is as complex as it could be: it is $$\Sigma_1$$-complete. I'll interpret Friedman's question as asking whether the existential theory of all cardinal numbers could be simpler than that of finite cardinals.

My gut instinct is: of course not! But this is not a trivial question. For example asking whether $$p^n + q^n = r^n$$ has a solution where $$2 \lt n$$ and $$0 \lt p,q,r$$ has [proven extremely challenging](http://en.wikipedia.org/wiki/Wiles%27_proof_of_Fermat%27s_Last_Theorem) for finite cardinals but there are plenty of solutions with infinite cardinals!

One plan of attack is to try to define the finite cardinals among all cardinalsusing an existential formula. To get started, I'll start with a rich language including constants $$0$$, $$1$$, relations $$=$$, $$\lt $$ as well as addition, multiplication and exponentiation. Assuming the Axiom of Choice, finite cardinals are defined by the simple quantifier-free formula 
^
$$\mathfrak{p} \lt \mathfrak{p}+1.$$
^
 Without assuming choice, this only defines the [Dedekind finite sets](http://en.wikipedia.org/wiki/Dedekind-infinite_set). Fortunately, if $$\mathfrak{p}$$ is infinite then $$2^{2^{\mathfrak{p}}}$$ is never Dedekind finite. So the finite sets are always described by the quantifier-free formula 
^
$$2^{2^{\mathfrak{p}}} \lt 2^{2^{\mathfrak{p}}} + 1.$$
^
 This shows that the existential theory of all cardinals in this rich language is as complex as that of finite cardinals.

Do things change if we restrict the language? Indeed, the first part of Friedman's question only mentions exponentiation. For finite cardinals, we can recover addition and multiplication using familiar rules of exponents: 
^
$$\begin{aligned} a \times b &= c &&\iff& (2^a)^b = 2^c; \\\ a + b &= c &&\iff& (2^{2^a})^{2^b} = 2^{2^c}. \\\ \end{aligned}$$
^
 We can even eliminate $$0$$ and $$1$$ since any finite base other than $$0$$ and $$1$$ will do instead of $$2$$. So, for example, 
^
$$a \times b = c \iff \exists x,y,z(x \lt y \land y \lt z \land (z^a)^b = z^c).$$
^
 Therefore, the existential theory of finite cardinals with just exponentiation is just as complex as that with addition and multiplication.

Of course, we can't use this to recover addition and multiplication of infinite cardinals using the methods we used above, but if we can define the class of finite cardinals then we can use the above to recover addition and multiplication for these cardinals. Can we define finite cardinals using only $$=$$, $$\lt $$ and exponentiation? Well, the finite cardinals are the only ones that satisfy the monstrous inequality 
^
$$2^{2^{2^{2^{\mathfrak{p}}}}} \lt \left(2^{2^{2^{2^{\mathfrak{p}}}}}\right)^2.$$
^
 We can then eliminate $$2$$ using the same trick as above to get an existential definition: 
^
$$\exists\mathfrak{q},\mathfrak{r},\mathfrak{s}\left(\mathfrak{q} \lt \mathfrak{r} \land \mathfrak{r} \lt \mathfrak{s} \land \mathfrak{s}^{\mathfrak{s}^{\mathfrak{s}^{\mathfrak{s}^{\mathfrak{p}}}}} \lt \left(\mathfrak{s}^{\mathfrak{s}^{\mathfrak{s}^{\mathfrak{s}^{\mathfrak{p}}}}}\right)^{\mathfrak{s}}\right).$$
^
 So my gut instinct was right: the existential theory of all cardinals using only $$=$$, $$\lt $$ and exponentiation is at least as complex as that of finite cardinals!

* * *

This took more than 30 minutes but it didn't take much more and it was a lot of fun! Hopefully, the time constraint didn't impact the content quality too much...

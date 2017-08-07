---
title: "HoTT Math 4: Local rings and fields"
date: 2013-12-10 01:13:28
permalink: /archives/1517/
published: true
topics: [type-theory]
tags: [Homotopy Type Theory]
---
It's been a while since the last edition of [HoTT Math]({{ "archives/1448" | relative_url }}). Fall is always very busy for me and I've been composing this installment one $$\varepsilon$$ at a time... We are finally arriving at our destination: fields!

The main issue with fields is to correctly handle the implicit negation in the term _nonzero_. Since the natural logic of HoTT is intuitionistic rather than classical, this is much more subtle than one would expect.

* * *

One issue with the basic commutative ring theory we developed last time is that there is a one-element ring. This is a feature of every equational theory since all identities are satisfied in the trivial algebra with one element. The problem is that equational logic doesn't have negation so there is no way to state a nontriviality axiom like $$\mathsf{O}\not\approx\mathsf{I}$$ in this context. These issues are not new and not special to HoTT but the problem is amplified since logic in HoTT is may have more truth values than just true and false. Consequently, negation in HoTT always needs a little more care.

The usual way to say $$\mathsf{O}\not\approx\mathsf{I}$$ is the strongest one, namely that $$\mathsf{O}=_R \mathsf{I}$$ is the empty type $$\mathbf{0},$$ or:
^
$${\small\fbox{\(\phantom{b}\)nontrivial\(\phantom{q}\)}} :\equiv(\mathsf{O}=_R \mathsf{I}) \to \mathbf{0}.$$
^
This is stronger than just saying that $$\mathsf{O}=_R \mathsf{I}$$ isn't inhabited and it may exclude more than just the one element ring in the absence of the law of excluded middle [§3.4].

In general, we define inequality by 
^
$$(x \neq_R y) :\equiv(x =_R y) \to \mathbf{0}.$$
^
 So we can simply write $$\mathsf{O}\neq_R \mathsf{I}$$ instead of $${\small\fbox{\(\phantom{b}\)nontrivial\(\phantom{q}\)}}.$$ To see this in action, let's look at nonunits. The usual definition gives 
^
$$\operatorname{\mathsf{nonunit}}(x) :\equiv\prod_{y:R} (x \cdot y \neq_R \mathsf{I}).$$
^
 The recursion and induction rules for $$\Sigma$$-types [§1.6] show that $$\operatorname{\mathsf{nonunit}}(x)$$ is equivalent to the negation $$\lnot\operatorname{\mathsf{unit}}(x) :\equiv\operatorname{\mathsf{unit}}(x) \to \mathbf{0}.$$[^1] In classical mathematics, a local ring is one where the nonunits form an ideal, which is then necessarily the unique maximal ideal of the ring. Assuming $${\small\fbox{\(\phantom{b}\)nontrivial\(\phantom{q}\)}},$$ we see that $$\operatorname{\mathsf{nonunit}}(\mathsf{O})$$ is inhabited. It is also easy to see that 
^
$$\prod_{x,y:R} (\operatorname{\mathsf{nonunit}}(x)+\operatorname{\mathsf{nonunit}}(y) \to \operatorname{\mathsf{nonunit}}(x \cdot y))$$
^
is always inhabited. Thus, all that is missing is the axiom:
^
$${\small\fbox{\(\phantom{b}\)local\(^-\!\!\phantom{q}\)}} :\equiv\prod_{x,y:R} (\operatorname{\mathsf{nonunit}}(x)\times\operatorname{\mathsf{nonunit}}(y) \to \operatorname{\mathsf{nonunit}}(x+y)).$$
^
Classically, fields are local rings where the maximal ideal has only one element $$\mathsf{O}.$$ So a reasonable axiom for fields is
^
$${\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}} :\equiv\prod_{x:R} (\operatorname{\mathsf{nonunit}}(x) \to x =_R \mathsf{O}).$$
^
(Note that $${\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}$$ implies $${\small\fbox{\(\phantom{b}\)local\(^-\!\!\phantom{q}\)}}.$$) Classically, these are indeed the fields we know and love but things break down in an intuitionistic setting. If these were fields, then we should be able to conclude that nonzero elements are units. However, from $${\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}$$ we can only conclude that $$x \neq_R \mathsf{O}\to \lnot\operatorname{\mathsf{nonunit}}(x)$$ and the conclusion there is the double negative $$\lnot\lnot\operatorname{\mathsf{unit}}(x)$$ rather than the positive statement $$\operatorname{\mathsf{unit}}(x).$$ The fact is that we cannot conclude that every nonzero element is a unit from this axiom without using the law of excluded middle! A similar issue arises with local rings as defined above: the axiom $${\small\fbox{\(\phantom{b}\)local\(^-\!\!\phantom{q}\)}}$$ does not imply the property that if $$x + y$$ is a unit then at least one of $$x$$ and $$y$$ is a unit.

The solution to this isssue is to reverse the relation between equality and inequality. What if instead of inequality being the negation of equality we had that equality was the negation of inequality? This may sound counterintuitive at first but this is often how things work. Consider the case of two computable real numbers $$a$$ and $$b,$$ that is real numbers for which we have an algorithm which on input $$k$$ gives us a rational approximation within $$2^{-k}$$ of the real number in question. How do I determine whether $$a$$ and $$b$$ are equal?

  * To show that they are different, I can use the two algorithms compute sufficiently good rational approximations to $$a$$ and $$b$$ to tell them apart.
  * To show that they are equal, I need to argue that they are not different: given any input $$k$$ the two algorithms give rational approximations that are within $$2^{1-k}$$ of each other.

So, for computable real numbers, inequality is more primitive than equality!

This leads us to [apartness relations](http://en.wikipedia.org/wiki/Apartness_relation): a binary relation $$\mathrel{\rlap{\neq\,}{\,\neq}_{}}$$ that satisfies the following two axioms 
^
$$\begin{gathered} \lnot(x \mathrel{\rlap{\neq\,}{\,\neq}_{}}x) \\\ x \mathrel{\rlap{\neq\,}{\,\neq}_{}}y \to x \mathrel{\rlap{\neq\,}{\,\neq}_{}}z \lor y \mathrel{\rlap{\neq\,}{\,\neq}_{}}z \end{gathered}$$
^
 These axioms ensure that the negation of $$x \mathrel{\rlap{\neq\,}{\,\neq}_{}}y$$ is an equivalence relation; a tight apartness relation is one where 
^
$$\lnot(x \mathrel{\rlap{\neq\,}{\,\neq}_{}}y) \to x = y$$
^
 and thus the negation of $$x \mathrel{\rlap{\neq\,}{\,\neq}_{}}y$$ is equality. In classical logic, every apartness relation is the negation of an equivalence relation but this is not true intuitionistically. In fact, the negation of equality is not necessarily an apartness relation!

Without further ado, let us state exactly how we can define local rings using apartness. For example, a more positive way to define local rings is that 
^
$$x \mathrel{\rlap{\neq\,}{\,\neq}_{R}} y :\equiv\operatorname{\mathsf{unit}}(x - y)$$
^
 is an apartness relation. The first apartness axiom $$\lnot(x \mathrel{\rlap{\neq\,}{\,\neq}_{R}} x)$$ actually follows from $${\small\fbox{\(\phantom{b}\)nontrivial\(\phantom{q}\)}}$$ since $$\operatorname{\mathsf{unit}}(\mathsf{O}) \to (\mathsf{O}=_R \mathsf{I}).$$ The second apartness axiom boils down to to the fact discussed above that if $$x+y$$ is a unit then at least one of $$x$$ and $$y$$ is a unit. It is tempting to use the type 
^
$$\prod_{x:R} (\operatorname{\mathsf{unit}}(x+y) \to \operatorname{\mathsf{unit}}(x) + \operatorname{\mathsf{unit}}(y))$$
^
to describe this but this doesn't work because of the exclusive nature of sum types. Instead, we must use the propositional truncation $$\Vert\operatorname{\mathsf{unit}}(x) + \operatorname{\mathsf{unit}}(y)\Vert,$$ which is how the logical disjunction $$\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)$$ is defined [§3.7]. Thus a strongly local ring is a a nontrivial ring that satisfies
^
$${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}} :\equiv\prod_{x,y:R} (\operatorname{\mathsf{unit}}(x+y) \to \operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)).$$
^

Before going further with these ideas, let's practice some our intuitionistic reasoning by verifying that
^
$${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}} \to {\small\fbox{\(\phantom{b}\)local\(^-\!\!\phantom{q}\)}}.$$
^
Actually, we won't be practicing our intuitionistic reasoning, we'll just verify our logic by thinking in terms of functions between types rather than logical implication between propositions. Although an implication is not always equivalent to its contrapositive in intuitionistic logic, we do always have that
^
$$(P \to Q) \to (\lnot Q \to \lnot P).$$
^
In terms of types and functions, this the special case of
^
$$(A \to B) \to ((B \to C) \to (A \to C)),$$
^
where $$A :\equiv{P},$$ $$B :\equiv{Q},$$ $$C :\equiv\mathbf{0}.$$ This looks even more familiar when uncurried: 
^
$$(A \to B) \times (B \to C) \to (A \to C).$$
^
Thus, we see that
^
$${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}} \to (\lnot(\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)) \to \lnot\operatorname{\mathsf{unit}}(x+y)).$$
^
Now recall that the disjunction $$\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)$$ is defined as the propositional truncation $$\Vert\operatorname{\mathsf{unit}}(x) + \operatorname{\mathsf{unit}}(y)\Vert$$ [§3.7]. This means that $$\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)$$ is a proposition such that 
^
$$\operatorname{\mathsf{unit}}(x) + \operatorname{\mathsf{unit}}(y)) \to P \quad\simeq\quad (\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)) \to P$$
^
for any proposition $$P.$$[^2] Since $$\mathbf{0}$$ is a proposition, we see that 
^
$$\lnot\operatorname{\mathsf{unit}}(x) \times\lnot\operatorname{\mathsf{unit}}(y) \ \simeq\ (\operatorname{\mathsf{unit}}(x) + \operatorname{\mathsf{unit}}(y)) \to \mathbf{0}\ \simeq\ \lnot(\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y)),$$
^
 where the left equivalence is the special case $$A :\equiv{P},$$ $$B :\equiv{Q},$$ $$C :\equiv\mathbf{0}$$ of 
^
$$(A + B) \to C \quad\simeq\quad (A \to C) \times (B \to C).$$
^
Finally, recombining the above, we obtain
^
$${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}} \to (\lnot\operatorname{\mathsf{unit}}(x)\times\lnot\operatorname{\mathsf{unit}}(y) \to \lnot\operatorname{\mathsf{unit}}(x+y)),$$
^
which is equivalent to $${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}} \to {\small\fbox{\(\phantom{b}\)local\(^-\!\!\phantom{q}\)}}$$ because $$\lnot\operatorname{\mathsf{unit}}(x) \leftrightarrow\operatorname{\mathsf{nonunit}}(x).$$

Analogously to positive axiom for local rings, the positive axiom for fields is
^
$${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}} :\equiv\prod_{x:R} (\operatorname{\mathsf{unit}}(x) \lor x =_R \mathsf{O}),$$
^
which implies both $${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}}$$ and $${\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}.$$ To see that $${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}} \to {\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}},$$ we will make use of the distributive law 
^
$$(P_1 \lor P_2) \land Q \quad\leftrightarrow\quad (P_1 \land Q) \lor (P_2 \land Q),$$
^
 which follows from the general equivalence 
^
$$(A_1 + A_2) \times B \quad\simeq\quad A_1 \times B + A_2 \times B$$
^
 by taking propositional truncations. In particular, 
^
$$(\operatorname{\mathsf{unit}}(x) \lor x =_R \mathsf{O}) \times \operatorname{\mathsf{unit}}(x+y) \leftrightarrow\operatorname{\mathsf{unit}}(x)\times\operatorname{\mathsf{unit}}(x+y) \lor (x =_R \mathsf{O}) \times \operatorname{\mathsf{unit}}(x+y).$$
^
 Since $$\operatorname{\mathsf{unit}}(x) \times \operatorname{\mathsf{unit}}(x+y) \to \operatorname{\mathsf{unit}}(x)$$ and $$(x =_R \mathsf{O}) \times \operatorname{\mathsf{unit}}(x+y) \to \operatorname{\mathsf{unit}}(y),$$ we see that 
^
$$(\operatorname{\mathsf{unit}}(x) \lor x =_R \mathsf{O}) \times \operatorname{\mathsf{unit}}(x+y) \to (\operatorname{\mathsf{unit}}(x) \lor \operatorname{\mathsf{unit}}(y))$$
^
 and it follows that $${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}} \to {\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}}.$$ To see that $${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}} \to {\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}},$$ we will make use of the fact that 
^
$$(P \lor Q) \land \lnot Q \to P.$$
^
 This also follows from the distributive law above. Indeed, 
^
$$(P \lor Q) \land \lnot Q \ \leftrightarrow\ (P \land \lnot Q) \lor (Q \land \lnot Q) \ \leftrightarrow\ P \land \lnot Q$$
^
because $$Q \land \lnot Q$$ is $$\mathbf{0}.$$ Note that $${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}}$$ is stronger than $${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}}\times{\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}$$ since it implies that 
^
$$\prod_{x,y:R} (x \mathrel{\rlap{\neq\,}{\,\neq}_{R}} y \lor x =_R y)$$
^
 and thus that $$R$$ has decidable equality [§3.4]. In other words, $${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}}$$ gives the equivalence 
^
$$x \neq_R y \leftrightarrow x \mathrel{\rlap{\neq\,}{\,\neq}_{R}} y,$$
^
 which means that $$\neq_R$$ is an apartness relation, whereas $${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}}\times{\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}$$ only gives that $$\mathrel{\rlap{\neq\,}{\,\neq}_{R}}$$ is a tight apartness relation: 
^
$$x =_R y \leftrightarrow\lnot(x \mathrel{\rlap{\neq\,}{\,\neq}_{R}} y).$$
^


The analysis above gives _three_ plausible definitions for fields:

  * A _residual field_ is a nontrivial ring that satisfies $${\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}.$$
  * A _Heyting field_ is a nontrivial ring that satisfies $${\small\fbox{\(\phantom{b}\)field\(^-\!\!\phantom{q}\)}}$$ and $${\small\fbox{\(\phantom{b}\)local\(^+\!\!\phantom{q}\)}}.$$
  * A _discrete field_ is a nontrivial ring that satisfies $${\small\fbox{\(\phantom{b}\)field\(^+\!\!\phantom{q}\)}}.$$

While each is stronger than the previous, they all have their uses and there is no choice which is always better than the others. Discrete fields behave the same as fields in classical logic since $$R$$ has decidable equality. Heyting fields are preferred in constructive circles and most definitions of the field of real numbers yield Heyting fields that are not necessarily discrete [§11.2, §11.3]. While residual fields are harder to work with, they do have their uses since the quotient of a nontrivial ring by a maximal ideal is a residual field which is not necessarily Heyting.

It is common for classical equivalences to break down in intuitionistic logic and therefore many natural concepts that are classically equivalent separate in intuitionistic settings. While this can be an annoyance, it is quite natural in the context of proof-relevant mathematics. Indeed, when we prove that a theorem about fields in a proof-relevant way, we cannot merely argue that every field satisfies the conclusion, we must proceed from known properties of fields and work our way to the desired conclusion. The precise properties used in this process naturally leads to a more refined understanding of the hypotheses of the theorem.

* * *

Before closing this installment of HoTT Math, let me draw your attention to an important lesson from the above:

_While the logic of HoTT is intuitionistic, knowledge of intuitionistic logic is not necessary to work in HoTT._

Thinking in terms of types and functions as we did above works very well. To illustrate once more, consider the following classical equivalences: 
^
$$\begin{aligned} P \to \lnot Q \quad&\leftrightarrow\quad Q \to \lnot P, \\\ \lnot P \to Q \quad&\leftrightarrow\quad \lnot Q \to P. \end{aligned}$$
^
 Which are valid in intuitionistic logic? When translated into types and functions, we get that these are the special cases of 
^
$$\begin{aligned} A \to (B \to C) \quad&\simeq\quad B \to (A \to C), \\\ (A \to C) \to B \quad&\simeq\quad (B \to C) \to A, \end{aligned}$$
^
 where $$A :\equiv{P},$$ $$B :\equiv{Q},$$ $$C :\equiv\mathbf{0}.$$ The first classical equivalence is intuitionistically valid. After uncurrying both sides of 
^
$$A \to (B \to C) \quad\simeq\quad B \to (A \to C),$$
^
 we obtain the obvious equivalence 
^
$$A \times B \to C \quad\simeq\quad B \times A \to C.$$
^
 On the other hand, the general form of the second equivalence makes no sense at all. Taking $$C$$ to be just about anything other than $$\mathbf{0}$$ leads to obviously false equivalences such as $$\mathbf{1}\to A \simeq\mathbf{1}\to B$$ when $$C :\equiv\mathbf{1}.$$ Indeed, the second classical equivalence is not intuitionistically valid since taking $$Q :\equiv\lnot P$$ leads to 
^
$$\lnot P \to \lnot P \quad\leftrightarrow\quad \lnot \lnot P \to P$$
^
 and double negation elimination is not intuitionistically valid.

---

[^1]: The equivalence of $$\textstyle\prod_{x:A} (B(x) \to C) \simeq \left({\textstyle\sum_{x:A} B(x)}\right)\to C$$ is the dependent type analogue of currying/uncurrying. Indeed, if instead of the dependent type $$B:A \to \mathcal{U}$$ we have a simple type $$B,$$ we obtain the familiar equivalence $$A \to (B \to C) \simeq (A \times B) \to C.$$ In full generality, we have the unwieldly equivalence $$\prod_{(a,b):\sum_{x:A} B(x)} C(a,b) \simeq \prod_{a:A} \prod_{b:B(a)} C(a,b),$$ where $$B:A \to \mathcal{U}$$ and $$C:\sum_{x:A} B(x) \to \mathcal{U}$$ [§2.15].

[^2]: This is the standard trick to work with propositional truncations: so long as $$P$$ is a proposition, $$\Vert A \Vert \to P$$ is equivalent to $$A \to P.$$ This is very important for handling disjunctions and existential quantifiers. Since $$P \lor Q$$ "forgets" which of $$P$$ and $$Q$$ holds, it is not generally possible to do a case analysis. However, if $$R$$ is a proposition then $$P \lor Q \to R$$ is equivalent to $$P + Q \to R$$ and the coproduct $$P + Q$$ does allow for case analysis. This explains why in addition to $$\lnot P \land \lnot Q \leftrightarrow \lnot(P \lor Q),$$ the following "halves" of De Morgan's laws hold in intuitionistic logic  $$P \land Q \to \lnot(\lnot P \lor \lnot Q),$$ $$P \lor Q \to \lnot(\lnot P \land \lnot Q),$$ $$\lnot P \lor \lnot Q \to \lnot(P \land Q),$$ while their converses do not.

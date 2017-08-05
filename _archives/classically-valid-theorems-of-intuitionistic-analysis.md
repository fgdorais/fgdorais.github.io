---
title: Classically valid theorems of intuitionistic analysis
date: 2011-10-30 18:14:30
permalink: /archives/448/
published: true
categories: [proof-theory, reverse-math]
tags: [Intuitionistic Logic, Realizability]
people: [Anne Troelstra, Carl Mummert, Jaap van Oosten, Jeff Hirst, L. E. J. Brouwer]
bibliography: [Bro23v, Dor11w, HirMum10k, Tro73r, Hei67y, Oos90m]
---
It is well-known that proofs in intuitionistic logic are more constructive than proofs in classical logic. Indeed, this is what the (informal) Brouwer–Heyting–Kolmogorov (BHK) interpretation leads to believe. Thus, intuitionistic proofs tend to have more information content than classical proofs, a fact that is well exploited in proof mining. 

This suggests that looking at intuitionistic proofs of classical results from classical analysis may yield some new insights on the constructive nature of these classical results. However, there is one major hurdle with this program: theorems and axioms of intuitionistic analysis are not necessarily classically valid. Thus, inuitionistic proofs must be inspected very closely before drawing any kind of classical conclusions from them. Often, this is done by only looking at intuitionistic proofs over weak systems of intuitionistic analysis whose axioms are all classically valid. This amounts to doing classical analysis with a very limited set of axioms and deduction rules and it basically prohibits the use of the most important methods and results from intuitionistic analysis. This is not very satisfactory, but there is another way. There is a rich class of statements for which intuitionistic analysis is conservative over some weak subtheory whose axioms are all classically valid. So long as we restrict our attention to statements from this class, we can use methods and results of intuitionistic analysis with impunity and draw classical conclusions from the mere existence of a proof in the weaker subsystem, without going through the pain of finding such a proof. 

One important result of intuitionistic analysis that is not classically valid is Brouwer's Continuity Theorem, which simply says that every function defined on the unit interval is (uniformly) continuous {% include p cite='Bro23v' %} (translated in {% include s cite='Hei67y' %}). The Continuity Theorem becomes especially powerful when combined with the Axiom of Choice, together they imply that if the statement $$\forall\xi\exists\zeta A(\xi,\zeta)$$ is true, then there must be a _continuous_ function $$F$$ such that $$\forall\xi A(\xi,F(\xi))$$. On the one hand, this combination captures the constructive strength of intuitionistic analysis, as it provides a uniform and effective way to obtain witnesses to existential statements. On the other hand, this combination has some disastrous consequences for classically minded mathematicians. For example, the only subsets of $$\R$$ that have complements are $$\emptyset$$ and $$\R$$. Indeed, if $$A \subseteq \R$$ has a complement then it has a characteristic function by the Axiom of Choice, which must then be continuous by the Continuity Theorem. Since $$\R$$ is connected, the only continuous $$\set{0,1}$$-valued functions on $$\R$$ are the two constant functions. Therefore, $$A$$ must either be empty or all of $$\R$$. In particular, it follows that equality for real numbers is undecidable: $$\forall\xi(\xi = 0 \lor \xi \neq 0)$$ cannot be true since we cannot partition $$\R$$ into the singleton zero and the set of nonzero real numbers. 

There are many ways to formalize all of this. In my paper {% include p cite='Dor11w' %}, I look at two related systems intuitionistic analysis and I exploit conservation results by {% include t cite='Tro73r' %} and {% include t cite='Oos90m' %} to draw some classical consequences in subsystems of second-order arithmetic commonly used in reverse mathematics. The main results are of the following form: if $$A$$ and $$B$$ satisfy certain syntactic constraints and 
^
$$\forall\xi(B(\xi) \lthen \exists\zeta A(\xi,\zeta))$$
^
 is provable in a certain formal system of intuitionistic analysis, then the sequential form 
^
$$\forall\xi(\forall n B(\xi_n) \lthen \exists\zeta\forall n A(\xi_n,\zeta_n))$$
^
 is provable in a corresponding classical subsystem of second-order arithmetic. Results of this kind had already been obtained by Jeff Hirst and Carl Mummert for a different class of intuitionistic systems {% include p cite='HirMum10k' %}. However, their systems only include classically valid axioms, so the fact that both systems I used prove Brouwer's Continuity Theorem and some form of the Axiom of Choice adds an interesting new twist to this picture.[^1]

$$\newcommand{\EL}{\mathsf{EL}}\newcommand{\GC}{\mathsf{GC}}\newcommand{\RCA}{\mathsf{RCA}}\newcommand{\krf}{\mathrel{\mathtt{rf}}}\newcommand{\cat}{\mathop{^\frown}}$$The basic intuitionistic system I will use is called $$\EL$$. The system $$\EL$$ has two sorts: natural numbers ($$\N$$) and functions from numbers to numbers ($$\N^\N$$). I will use roman letters for numbers and greek letters for functions. The details of $$\EL$$ can be found in {% include p cite='Tro73r' %} and {% include p cite='Dor11w' %}. The axioms of $$\EL$$ are classically valid. In fact, by adding the law of excluded middle to $$\EL$$, you obtain a classical system equivalent to the subsystem $$\RCA$$ of second-order arithmetic. To make this into a full-blown system for intuitionistic analysis, we can add Troelstra's Generalized Continuity ($$\GC$$) axiom scheme: 
^
$$\forall\xi(B(\xi) \lthen \exists\zeta A(\xi,\zeta)) \lthen \exists\alpha\forall\xi(B(\xi) \lthen \alpha\mathop{\vert}\xi{\downarrow} \land A(\xi,\alpha\mathop{\vert}\xi)),$$
^
 where $$B(\xi)$$ is restricted to the syntactic class $$\mathrm{N}_K$$ (defined below) but $$A(\xi,\zeta)$$ is arbitrary. The notation $$\alpha\mathop{\vert}\xi$$ is a clever way of coding partial continuous functions $$\N^\N\to\N^\N$$ due to Kleene that I will describe shortly. Since the class $$\mathrm{N}_K$$ includes the tautology $$0 = 0$$, $$\EL + \GC$$ directly implies the Axiom of Choice: if the set $$A_\xi = \set{\zeta \in \N^\N : A(\xi,\zeta)}$$ is nonempty for every $$\xi \in \N^\N$$, then there is an $$\alpha$$ such that $$\alpha\mathop{\vert}\xi$$ picks out a single element of $$A_\xi$$ for every $$\xi \in \N^\N$$. $$\EL + \GC$$ also implies Brouwer's Continuity Theorem: if $$A(\xi,\zeta)$$ describes the graph of a function $$F:\N^\N\to\N^\N$$, then there must be an $$\alpha$$ such that for every $$\xi$$, $$\alpha\mathop{\vert}\xi$$ is the unique $$\zeta$$ such that $$A(\xi,\zeta)$$. Since $$\xi \mapsto \alpha\mathop{\vert}\xi$$ is necessarily continuous, the function $$F$$ must be continuous. 

In order to talk about the relevant conservation result for $$\EL + \GC$$, I need to talk about Kleene's realizability with functions. The basic idea of realizability with functions is both natural and beautiful. Unfortunately, the beauty is hidden behind a thick wall of coding tricks. Three standard coding tricks are the following: 

  * Pairs of functions can be coded by alternately meshing their values: given functions $$\xi_0,\xi_1$$ there is a unique function $$\seq{\xi_0,\xi_1}$$ such that $$\seq{\xi_0,\xi_1}\pi_0 = \xi_0$$ and $$\seq{\xi_0,\xi_1}\pi_1 = \xi_1$$, where $$\pi_0 = \lambda n.2n$$ and $$\pi_1 = \lambda n.2n+1$$.
  * Number-function pairs can be coded by prefixing the number: given a number $$x$$ and a function $$\xi$$ there is a unique function $$x\cat\xi$$ such that $$(x\cat\xi)(0) = x$$ and $$(x\cat\xi)\sigma = \xi$$, where $$\sigma = \lambda n.n+1$$.
  * Every function $$\xi$$ can be thought of as encoding an infinite list of functions $$\xi_n = \lambda m.\xi(2^n(2m+1)-1)$$.
The next trick is a very clever way of encoding partial continuous functions $$\N^\N\to\N^\N$$ due to Kleene that I alluded to above. Given a function $$\xi$$ and a number $$\ell$$, let $$\bar{\xi}\ell$$ denote the finite initial segment $$\seq{\xi(0),\dots,\xi(\ell-1)}$$ coded as a number in some primitive recursive fashion. Kleene's encoding trick is best thought of as a two-step process. 
  1. A function $$\alpha \in \N^\N$$ encodes a partial continuous function $$\N^\N\to\N$$ as follows: to compute $$\alpha(\xi)$$ for some $$\xi \in \N^\N$$, look for the first number $$\ell$$ (if any) such that $$\alpha(\bar{\xi}\ell) \neq 0$$ and then set $$\alpha(\xi) = \alpha(\bar{\xi}\ell)-1$$. Write $$\alpha(\xi){\uparrow}$$ when no such $$\ell$$ can be found, and $$\alpha(\xi){\downarrow}$$ when $$\alpha(\xi)$$ is defined.
  2. Thinking of functions in $$\N^\N$$ as encoding number-function pairs $$n\cat\xi$$, the above scheme lets $$\alpha \in \N^\N$$ encode a partial continuous function $$\N\times\N^\N\to\N$$ via $$\alpha(n\cat\xi)$$. By currying, we obtain a partial continuous function $$\N^\N\to\N^\N$$. Thus, for each $$\xi \in \N^\N$$, the value $$\alpha\mathop{\vert}\xi$$ of the partial continuous function $$\N^\N\to\N^\N$$ coded by $$\alpha$$ is the function $$\lambda n.\alpha(n\cat\xi)$$ provided that $$\alpha(n\cat\xi){\downarrow}$$ for every $$n$$. Write $$\alpha\mathop{\vert}\xi{\uparrow}$$ when $$\alpha(n\cat\xi){\uparrow}$$ for some $$n$$, and $$\alpha\mathop{\vert}\xi{\downarrow}$$ when $$\alpha\mathop{\vert}\xi$$ is defined.
This encoding of partial continuous functions is rather dense at first sight, but it is actually quite natural after getting used to it. The $$\alpha\mathop{\vert}\xi$$ notation may seem strange, but it is actually well motivated. Thinking of $$\mathop{\vert}$$ as a partial binary operation on the set $$\N^\N$$, we obtain a partial combinatory algebra known as Kleene's second algebra. The post-modern approach to realizability goes through realizability topos, which can be constructed on top of any partial combinatory algebra. 

Kleene's realizability with functions is a syntactic transformation of formulas which uses all the tricks above to pack most existential quantifiers into an auxiliary function parameter. The transformation is built by induction on complexity as follows[^2]: 

  * $$\alpha \krf A$$ is $$A$$ for atomic $$A$$.
  * $$\alpha \krf (A \land B)$$ is $$\alpha\pi_0 \krf A \land \alpha\pi_1 \krf B$$.
  * $$\alpha \krf (A \lthen B)$$ is $$\forall\beta(\beta \krf A \lthen \alpha\mathop{\vert}\beta{\downarrow} \land \alpha\mathop{\vert}\beta \krf B)$$.
  * $$\alpha \krf \forall x A$$ is $$\forall x(\alpha_x \krf A)$$.[^3]
  * $$\alpha \krf \forall \xi A$$ is $$\forall \xi(\alpha\mathop{\vert}\xi{\downarrow} \land \alpha\mathop{\vert}\xi \krf A)$$.
  * $$\alpha \krf \exists x A$$ is $$\alpha\sigma \krf A[x/\alpha(0)]$$.
  * $$\alpha \krf \exists \xi A$$ is $$\alpha\pi_1 \krf A[\xi/\alpha\pi_0]$$.
Note that the translated formula $$\alpha \krf A$$ never involves existential quantifiers, except to say that $$\alpha\mathop{\vert}\xi{\downarrow}$$ and the scope of this implicit existential quantifiers is quantifier-free. Therefore, $$\alpha \krf A$$ always belongs to the class of formulas $$\mathrm{N}_K$$, which is defined as follows: 
  * If $$A$$ is quantifier-free, then $$A$$, $$\exists x A$$, $$\exists\xi A$$ are in $$\mathrm{N}_K$$.
  * If $$A, B$$ are in $$\mathrm{N}_K$$, then so are $$A \land B$$, $$A \lthen B$$, $$\forall x A$$, $$\forall \xi A$$.
It seems odd to include existential function quantifiers in the first clause but this is harmless since a quantifier-free formula $$A$$ can only use a finite initial segment of $$\xi$$ and thus $$\exists\xi A$$ is easily simulated by an existential number quantifier. 

Now that we have described the system $$\EL + \GC$$ and Kleene's realizability with functions, we can start tying everything together. The first step is to relate provability in $$\EL + \GC$$ with Kleene's realizability with functions. 

**Troelstra's Characterization Theorem.** _For every formula $$A$$_: 

  1. $$\EL + \GC \vdash A \liff \exists\alpha(\alpha \krf A)$$.
  2. $$\EL + \GC \vdash A \IFF \EL \vdash \exists\alpha(\alpha \krf A)$$.
An important consequence of this characterization of $$\krf$$ is that $$\EL + \GC$$ is relatively consistent with $$\EL$$. In particular, Brouwer's Continuity Theorem is relatively consistent with the Axiom of Choice so that the above discussion was not meaningless. 

The next step is to formulate the relevant conservation result. The class of formulas $$\Gamma_K$$ is defined as follows: 

  * Quantifier-free formulas are in $$\Gamma_K$$.
  * If $$A, B$$ are in $$\Gamma_K$$ then so are $$A \land B$$, $$\forall x A$$, $$\forall \xi A$$, $$\exists x A$$, $$\exists \xi A$$.
  * If $$A$$ is in $$\mathrm{N}_K$$ and $$B$$ is in $$\Gamma_K$$ then $$A \lthen B$$ is in $$\Gamma_K$$.
Although $$\Gamma_K$$ is far from including all formulas, it is actually a rather rich fragment which plays well with Kleene's realizability with functions. 

**Troelstra's Conservation Theorem.** _If $$A \in \Gamma_K$$ then $$\EL \vdash \exists\alpha(\alpha \krf A) \lthen A$$._

Combining this with the second part of Troelstra's Characterization Theorem, we see that if $$A \in \Gamma_K$$, then 
^
$$\EL + \GC \vdash A \quad\IFF\quad \EL \vdash A.$$
^
 In other words, $$\EL + \GC$$ is conservative over $$\EL$$ for formulas in $$\Gamma_K$$. 

What is this all good for? Well, suppose your friend Bertus (a hard-core intuitionist working in $$\EL + \GC$$) tells you (a hard-core classicist working in $$\mathsf{ZFC}$$) about his most recent result: 

_Every $$n \times n$$ real matrix with nonzero determinant is invertible._

A priory, you have no reason to believe your friend since he also believes in false statements like _every function is continuous_. After some thought, you realize that $$\det(A) \neq 0$$ can be formalized as a formula in $$\mathrm{N}_K$$ and that 
^
$$(\forall A \in M_{n\times n}(\R))(\det(A) \neq 0 \lthen (\exists B \in M_{n\times n}(\R))(AB = BA = I))$$
^
 can be formalized as a formula in $$\Gamma_K$$. You can then conclude that Bertus's result is classically true and, because of $$\GC$$, that there is a continuous function to compute the inverse of a $$n \times n$$ real matrix $$A$$ with nonzero determinant. Not only were you able to meaningfully communicate with your friend Bertus, but you also gained a new classical result that you can call your own![^4]

The system $$\EL + \GC$$ is not the only system for which the above scheme goes through. {% include t cite='Oos90m' %} proves a similar characterization result for an intuitionistic system that incorporates the Weak König Lemma. This system also proves Brouwer's Continuity Theorem. However, since the Weak König Lemma and Brouwer's Continuity Theorem are incompatible with the Axiom of Choice, van Oosten has to settle for a weaker form of choice that continuously selects a nonempty compact set of witnesses to existential statements instead of a single witness. These results of van Oosten are also exploited in my paper {% include p cite='Dor11w' %}.

---

[^1]: I think that it is probably safe to add certain intuitionistic principles like Brouwer's Continuity Theorem to the systems considered by Hirst and Mummert ([2010](#HirMum10k)), but I have not checked that.

[^2]: There is no clause for disjunction since because I prefer to think of $$A \lor B$$ as an abbreviation for $$\exists x((x = 0 \lthen A) \land (x \neq 0 \lthen B))$$. Since equality of numbers is decidable, this interpretation is intuitionistically correct.

[^3]: Troelstra ([1973](#Tro73r)) actually uses $$\forall x(\alpha\mathop{\vert}\lambda n.x{\downarrow} \land \alpha\mathop{\vert}\lambda n.x \krf A)$$ for this case. This amounts to the same idea except that $$\alpha_x$$ is always defined whereas $$\alpha\mathop{\vert}\lambda n.x$$ might not. There does not appear to be any need for the added complexity except to make this case more parallel to the other universal quantification case.

[^4]: Don't start writing that paper right away: this is not a new result... However, you can now captivate your friends for hours explaining how you discovered the existence of Cramer's Rule without opening a linear algebra textbook!


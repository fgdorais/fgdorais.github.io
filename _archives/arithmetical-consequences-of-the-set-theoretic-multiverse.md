---
title: Arithmetical consequences of the set-theoretic multiverse
date: 2013-02-10 21:33:06
permalink: /archives/1193/
published: true
categories: [mathematical-philosophy, set-theory]
tags: [Set-Theoretic Multiverse]
people: [Joel David Hamkins, Victoria Gitman]
bibliography:
  - authors: [V. Gitman, J. D. Hamkins] 
    year: 2010
    title: "A natural model of the multiverse axioms"
    cite: " Notre Dame Journal of Formal Logic 51, 475–484"
    arxiv: "1104.4450"
    doi: "10.1215/00294527-2010-030"
    mr: "2741838"
    zbl: "1214.03035"
  - authors: [J. D. Hamkins] 
    year: 2012
    title: "The set-theoretic multiverse"
    cite: "Review of Symbolic Logic 5, 416–449"
    arxiv: "1108.4223"
    doi: "10.1017/S1755020311000359"
    mr: "2970696"
    zbl: "1260.03103"
---
In (Hamkins 2012), Joel David Hamkins proposed a set of axioms for the set-theoretic multiverse. Several of these axioms reflect the typical world many set theorists live in, namely that generic extensions, inner models and the like are all legitimate universes. Some set theorists prefer the universe perspective where one such universe is singled out as more legitimate than others and other set theorists prefer to think that any universe is as legitimate as any other. Hamkins is of the latter view and, in many ways, his view is even radically opposed to the universe perspective. Indeed, some of Hamkins's axioms take the form of "mirages" that gradually eliminate the possibility of singling out a preferred universe. These can be formulated as follows.[^1]

Uncountability Mirage
: _Every universe is countable from the perspective of a larger universe._

Undefinability Mirage
: _Every universe is constructible from the perspective of a larger universe._

Wellfoundedness Mirage
: _Every universe is not wellfounded from the perspective of a larger universe._

Finiteness Mirage
: _Every universe has a nonstandard $$\omega$$ from the perspective of a larger universe._

The Undefinability Mirage is a fascinating axiom that I hope to talk about in the near future but it does not directly contradict the universe perspective. The Uncountability Mirage is startling but it isn't earth-shattering on its own. However, the last two mirages are fundamentally incompatible with the universe perspective. The Finiteness Mirage — which actually implies the Wellfoundedness Mirage — is especially striking since it asserts that no universe understands true finiteness. This is a chilling thought for most mathematicians, even those who do not espouse the classical universe view. After reading Hamkins's account, I wondered what kind of arithmetical consequences the multiverse axioms have. This is an important question since an arithmetical disagreement between the multiverse view and the universe view would make the divide much more than a different perspective. 

To answer this question, let's step outside the multiverse and take a divine perspective where we understand true finiteness. From this divine perspective, we will analyze the multiverse and see what we could possibly infer from these mirages. We will first reverse engineer the key ingredients in the consistency proof of Gitman and Hamkins (2010) and then rebuild the multiverse with minimal assumptions on our divine understanding. From this process, we will then see that the true consequences of the multiverse view cannot exceed these minimal assumptions. In order to carry this out, we will need to make a some additional assumptions how the multiverse relates to our divine world. The first of these is that while no individual universe understands true finiteness, they collectively do understand true finiteness. 

Divine Finiteness
: _Every truly nonstandard finite ordinal in some universe is nonstandard in some larger universe._

We will see later that this assumption is not as stringent as it may seem. 

Henceforth, the truly finite ordinals of a universe $$U$$ will be denoted $$\omega$$ while the internally finite ordinals of $$U$$ will be denoted $$\omega^U$$. The Finiteness Mirage says that $$\omega$$ is always a proper initial segment of $$\omega^U$$. Since the truly finite ordinals in any two universes are canonically isomorphic, there is no need for a different symbol $$\omega$$ for each universe and we will handle them as if these were all the same. The _standard system_ of a universe $$U$$ is the collection 
^
$$\newcommand{\SSy}{\operatorname{SSy}\nolimits}\SSy(U) = \set{x \cap \omega : x \in U}.$$
^
 This collection of subsets of $$\omega$$ is always a _Scott set_: 

  * If $$A, B$$ are in the collection then so is $$A \oplus B = \set{2m : m \in A} \cup \set{2n+1 : n \in B}$$.
  * If $$A$$ is computable relative to $$B$$ and $$B$$ is in the collection then so is $$A$$.
  * If $$T$$ is an infinite binary tree coded by a set in the collection then $$T$$ has a path in the collection.[^2]

The second additional assumption we will make is that these standard systems exhaust all subsets of $$\omega$$. 

Divine Comprehension
: _Every truly finite collection of subsets of $$\omega$$ is contained in the standard system of some universe._

Thus the divine subsets of $$\omega$$ also form a Scott set. 

Following the analysis of (Gitman-Hamkins 2010), we will now show that these standard systems are very strong invariants for universes. Let us say that two universes $$U$$ and $$U'$$ are _compatible_ if they are both elements of the same larger universe. 

**Compatibility Lemma.** _Any two compatible universes have the same standard system._

**Proof.** It is enough to show that if a universe $$U$$ is an element of another universe $$V$$ then $$\SSy(U) = \SSy(V)$$. First, note that $$\omega^V$$ is isomorphic to an initial segment of $$\omega^U$$ which is closed under addition, multiplication, exponentiation, etc. Without loss of generality, we may assume that $$\omega^V \subseteq \omega^U$$. Let $$n$$ be a nonstandard element of $$\omega^V$$. Every element of $$\SSy(U)$$ and $$\SSy(V)$$ is coded by a subset of $$n$$ which is in turn coded by the binary digits of some $$x \lt 2^n$$. The binary digits of such $$x$$ are the same whether computed in $$U$$ or in $$V$$, thus $$\SSy(U) = \SSy(V)$$. **QED**

**Saturation Lemma.** _Every universe $$U$$ is $$\SSy(U)$$-saturated._

**Proof.** Let $$V$$ be a universe containing $$U$$ as an element. Suppose $$t = \hat{t} \cap \omega$$ for some $$\hat{t} \in V$$. Without loss of generality, we may further assume that $$\hat{t} \subseteq \omega^V$$. Let $$\phi_i(\bar{v})$$ denote the $$i$$-th formula in the standard enumeration of all formulas with free variables among $$\bar{v}$$. Note that $$\phi_i(\bar{v})$$ is a standard formula for each $$i \in \omega$$ but $$\phi_i(\bar{v})$$ makes sense in $$U$$ even for nonstandard $$i \in \omega^V$$. Since $$U$$ is an element of $$V$$, the set 
^
$$s = \set{n \in \omega^V : (\exists \bar{a} \in U)(\forall i \in \hat{t}\cap n)(U \vDash \phi_i(a))}$$
^
 exists in $$V$$. If the true type $$\set{\phi_i(\bar{v}):i \in \omega}$$ is truly finitely realizable in $$U$$, then $$\omega \subseteq s$$. By overspill, there must be a nonstandard $$n \in s$$, which means that there is some $$\bar{a} \in U$$ such that $$U \vDash \phi_i(\bar{a})$$ for all $$i \in t$$ since $$t \subseteq \hat{t} \cap n$$. **QED**

**Isomorphism Lemma.** _Any two compatible universes that satisfy the same theory are isomorphic in some larger universe._

**Proof.** Suppose $$U$$ and $$U'$$ are compatible universes. By the Uncountability Mirage, we may assume that $$U$$ and $$U'$$ are both countable elements of some larger universes $$V$$. Moving to a still larger universe, we may assume that $$\SSy^V(U) = \SSy^V(U')$$ (i.e. that $$U$$ and $$U'$$ have the same standard system as computed in $$V$$). By the Divine Finiteness assumption, we may also assume that $$U$$ and $$U'$$ satisfy the same theory as computed in $$V$$.[^3] From the Saturation Lemma in $$V$$, we see that $$U$$ and $$U'$$ are countable structures that realize exactly the same types and we can build an isomorphism between them using the back & forth method. **QED**

From these lemmas, we get a very nice picture of the multiverse. The multiverse is divided into _trunks_ within which all universes have the same standard system. Different trunks are incompatible and each forms a multiverse on its own. Within a trunk, models are categorized by their theories. 

Hamkins (2012) is deliberately vague regarding what axioms universes need to satisfy. Whatever these axioms are, they should be enough to make sense of the multiverse axioms and the arguments above. For our purposes, let's assume these axioms form a recursively axiomatizable theory $$\mathcal{U}$$. 

**Theorem (Gitman–Hamkins 2010).** _If $$S$$ is a countable Scott set then the class of all countable $$S$$-saturated models of $$\mathcal{U}$$ with standard system $$S$$ satisfies the multiverse axioms if and only if this class is nonempty._

Moreover, with our two additional assumptions, every multiverse trunk consisting of truly countable models is precisely of this form.[^4]

What are the minimal assumptions on our divine world that suffice to carry out all of the above? 
^
$$\newcommand{\Con}{\operatorname{Con}\nolimits}\mathsf{WKL}_0 + \Con(\mathcal{U})$$
^
 This is the weakest subsystem of second-order arithmetic that proves that for every subset $$A$$ of $$\omega$$ there is a countable $$A$$-recursively saturated model of $$\mathcal{U}$$. The multiverse then consists of an essentially arbitrary collection of trunks from the collection of all recursively saturated models of $$\mathcal{U}$$ in this divine world.[^5] Therefore, we conclude that the multiverse axioms are conservative over $$\mathsf{WKL}_0 + \Con(\mathcal{U})$$ for true second-order arithmetic. Hence, the purely arithmetical consequences of the multiverse axioms are limited to $$\mathsf{I}\Sigma_1 + \Con(\mathcal{U})$$, the first-order part of $$\mathsf{WKL}_0 + \Con(\mathcal{U})$$. 

The universe view is also plausible assuming $$\mathsf{WKL}_0 + \Con(\mathcal{U})$$ since that is enough to show that $$\mathcal{U}$$ has a model. However, the universe view also assumes that the universe is a _standard_ model of $$\mathcal{U}$$: the finite ordinals in the universe are truly finite and all the sets in the universe are truly wellfounded. If one thinks of this as a requirement on the universe imposed by the divine world, then these are stronger assumptions than $$\mathsf{WKL}_0 + \Con(\mathcal{U})$$. For example, all of the arithmetical consequences of $$\mathcal{U}$$ must be true. However, if we view things the other way around and think that the universe is imposing these requirements on the divine world, then these are potentially weaker assumptions. For example, the universe could satisfy $$\mathcal{U} + \lnot\Con(\mathcal{U})$$. Needless to say that the latter position is difficult to justify ontologically. 

Personally, I find the multiverse picture much clearer since $$\mathsf{WKL}_0 + \Con(\mathcal{U})$$ is much easier to understand than the murkier picture that arises from the universe view. In any case, we can conclude that there are no essential incompatibilities between the two points of view so the choice is yours: 

_Do you prefer the universe or the multiverse?_

---

[^1]: These designations differ from (Hamkins 2012) since I wanted to use the emphasize how each one opposes the universe perspective. Hamkins refers to the _Uncountability Mirage_ as the _Countability Principle_ and to the _Undefinability Mirage_ as _Absorption into L_. The _Finiteness Mirage_ is not present in (Hamkins 2012) but the _Wellfoundedness Mirage_ takes this stronger form in (Gitman-Hamkins 2010).

[^2]: Any primitive recursive coding will do. For example, every binary sequence $$\sigma$$ of length $$\ell$$ can be coded by the number $$\#\sigma = 2^{\ell} + \sigma(\ell-1)\cdot2^{\ell-1}+\cdots+\sigma(1)\cdot2+\sigma(0)$$ and a binary tree $$T$$ can then be coded by the set $$\set{\#\sigma : \sigma \in T}$$. A path through $$T$$ is then a set $$P$$ such that $$2^{\ell} + \sum_{k \lt \ell, k \in P} 2^k \in T$$ for every $$\ell.$$

[^3]: Although $$U$$ and $$U'$$ are truly elementarily equivalent, they may not be elementarily equivalent in $$V$$. However, the first Gödel number in $$\omega^V$$ of a sentence where $$U$$ and $$U'$$ disagree must be nonstandard. By the Divine Finiteness assumption, there is a larger universe $$V'$$ that recognizes that this is a nonstandard Gödel number and in $$V'$$ the two models $$U$$ and $$U'$$ do satisfy the same theory.

[^4]: More possibilities arise if we remove the Divine Finiteness assumption. For example, assuming $$\Con(\mathcal{U})$$, the class of all countable recursively saturated models of $$\mathcal{U}+\lnot\Con(\mathcal{U})$$ satisfies the multiverse axioms but not Divine Finiteness.

[^5]: We only need to make sure that every subset of $$\omega$$ in our divine world is contained in the standard system of a selected trunk in order to satisfy the Divine Comprehension assumption.


---
title: A game-theoretic proof of Fraïssé's Theorem
date: 2011-10-14 04:44:33
permalink: /archives/72/
published: true
topics: [games, model-theory]
tags: [Ehrenfeucht-Fraïssé Games, Fraïssé's Theorem, Game Semantics]
people: [Andrzej Ehrenfeucht, Roland Fraïssé]
---
One of the important outcomes of the Fraïssé approach to model theory is that it is possible, in principle, to develop model theory from a strictly structural perspective, without ever mentioning formulas and their semantics. In practice, nobody really goes that far, but it is very useful to know about this radically different way to think about model theory. The key result that allows one to eliminate formulas is Fraïssé's Theorem, which gives a combinatorial way to characterize when two structures with the same signature satisfy the same sentences. Ehrenfeucht, a student of Fraïssé, came up with a particularly elegant way to formulate Fraïssé's ideas in terms of what are now called Ehrenfeucht–Fraïssé (EF) games (defined below). 

**Fraïssé's Theorem.** _Let $$A$$ and $$B$$ be two relational structures with the same signature. Duplicator has a winning strategy in the EF game $$G_n(A,B)$$ if and only if $$A$$ and $$B$$ satisfy the same sentences of quantifier depth at most $$n$$. Therefore, $$A$$ and $$B$$ are elementarily equivalent if and only if Duplicator has a winning strategy in all of the EF games $$G_n(A,B)$$._

There are now many proofs of Fraïssé's Theorem. Since the theorem mentions formulas and satisfaction, it is impossible to prove this result without talking about syntax and semantics. Most of the proofs I have seen use classical semantics à la Tarski. However, there are some alternatives to classical semantics. One such alternative are game semantics à la Hintikka. Since Fraïssé's Theorem is so elegantly stated in terms of games, this seems like a very suitable choice. 

It turns out that the game-theoretic proof of the forward implication of Fraïssé's Theorem is rather short and elegant, at least when compared to the classical proof.[^1] The the approach is certainly not new, but I don't remember if I got the idea from somewhere or if I pieced it together myself. In any case, since this proof is hard to find, I am posting it here for everyone to enjoy.[^2]

Let's start with some conventions. Fix a relational first-order language $$\mathcal{L}$$. (Constants can be added without trouble, but functions are a bit of a pain.) Throughout, $$A$$ and $$B$$ will denote two structures for the language $$\mathcal{L}$$. If $$R$$ is an atomic relation symbol, write $$R^A$$ and $$R^B$$ for the interpretation of $$R$$ in $$A$$ and $$B$$ respectively. 

First, recall the definition of the Ehrenfeucht–Fraïssé (EF) game $$G_n(A,B)$$. This is a $$n$$-round game between two players Spoiler and Duplicator. On the $$i$$-th round: 
  * Spoiler picks some $$a_i \in A$$ or some $$b_i \in B$$.
  * Duplicator picks some $$b_i \in B$$ or some $$a_i \in A$$ (the opposite of Spoiler's choice).
  
After the $$n$$ rounds have been played, Duplicator wins if the correspondence $$a_i \mapsto b_i$$ defines a finite partial isomorphism from $$A$$ to $$B$$; otherwise, Spoiler wins. In particular, we need that $$a_i = a_j \IFF b_i = b_j$$ for this map to be well-defined and injective. 

To simplify certain technical issues, we will use the fact that every formula $$\phi$$ is equivalent to a formula $$\phi'$$ with the same quantifier depth wherein negations only occur immediately before atomic relation symbols. It follows that it suffices to prove Fraïssé's Theorem for the class of formulas obtained by closing the literals (atomic relations and their negations) under conjunction, disjunction, universal and existential quantification. We will call these _restricted formulas_ of $$\mathcal{L}$$.[^3]

Let $$\phi$$ be a restricted formula of $$\mathcal{L}$$ with free variables in $$v_1,\dots,v_n$$ and let $$\lbrace v_1/a_1,\dots,v_n/a_n\rbrace$$ be a variable assignment in the structure $$A$$. The semantic game $$S_\phi(A)$$, between two players True and False, is defined by induction on the complexity of $$\phi$$. 

  * If $$\phi \equiv R(v_{i(1)},\dots,v_{i(k)})$$ where $$R$$ is a $$k$$-ary literal and $$i(1),\dots,i(k) \in \set{1,\dots,n}$$, then True wins if $$R^A(a_{i(1)},\dots,a_{i(k)})$$ holds, otherwise False wins.
  * If $$\phi \equiv (\psi_1 \land \psi_2)$$ then False chooses $$i \in \set{1,2}$$. Then the two players play the subgame $$S_{\psi_i}(A)$$.
  * If $$\phi \equiv (\psi_1 \lor \psi_2)$$ then True chooses $$i \in \set{1,2}$$. Then the two players play the subgame $$S_{\psi_i}(A)$$.
  * If $$\phi \equiv (\forall v\,\psi)$$ then False chooses $$a \in A$$ and adds $$\lbrace v/a \rbrace$$ to the variable assignment, replacing any previous assignment to $$v$$. Then the two players play the subgame $$S_{\psi}(A)$$.
  * If $$\phi \equiv (\exists v\,\psi)$$ then True chooses $$a \in A$$ and adds $$\lbrace v/a\rbrace$$ to the variable assignment, replacing any previous assignment to $$v$$. Then the two players play the subgame $$S_{\psi}(A)$$.

Note that the variable assignment is a tacit parameter to the game $$S_\phi(A)$$. It is easy to show that True has a winning strategy in the game $$S_\phi(A)$$ if and only if $$A \vDash \phi$$ (with the implicit variable assignment). 

We are now ready to prove the forward implication of Fraïssé's Theorem. Suppose that Duplicator has a winning strategy in the game $$G_n(A,B)$$. Let $$\sigma$$ be a restricted sentence of $$\mathcal{L}$$, with quantifier depth at most $$n$$, such that $$A \vDash \sigma$$. Then True has a winning strategy in the game $$S_\sigma(A)$$. We will use this strategy together with Duplicator's winning strategy in $$G_n(A,B)$$ to define a winning strategy for True in $$S_\phi(B)$$. The strategy is defined by deconstructing $$\sigma$$ and keeping track of a play of the EF game $$G_n(A,B)$$ on the side. 

Since $$\sigma$$ is a sentence, we start the games $$S_\sigma(A)$$ and $$S_\sigma(B)$$ with the empty variable assignment. We will play $$S_\sigma(A)$$ and $$S_\sigma(B)$$ in parallel in such a way that both games see the same formula at all times. Suppose we have reached the subformula $$\phi$$ of $$\sigma$$. 

  * If $$\phi \equiv (\psi_1 \land \psi_2)$$ then we let False play in $$S_\phi(B)$$ by choosing $$i \in \set{1,2}$$, and we copy False's move to $$S_\phi(A)$$.
  * If $$\phi \equiv (\psi_1 \lor \psi_2)$$ then we use True's strategy in $$S_\phi(A)$$ to choose $$i \in \set{1,2}$$, and we copy this move to $$S_\phi(B)$$ as part of True's strategy.
  * If $$\phi \equiv (\forall v\,\psi)$$ then we let False play in $$S_\phi(B)$$ by choosing $$b \in B$$. We let this $$b \in B$$ be Spoiler's next move in our EF game $$G_n(A,B)$$. We then use Duplicator's strategy in $$G_n(A,B)$$ to pick $$a \in A$$. We let this $$a \in A$$ be False's next move in $$S_\phi(A)$$.
  * If $$\phi \equiv (\exists v\,\psi)$$ then we use True's strategy in $$S_\phi(A)$$ to choose $$a \in A$$. We let this $$a \in A$$ be Spoiler's next move in our EF game $$G_n(A,B)$$.

We then use Duplicator's strategy in $$G_n(A,B)$$ to pick $$b \in B$$. We choose this $$b \in B$$ as the next move in True's strategy for $$S_\phi(B)$$.
The game ends when $$\phi$$ is a literal. Since $$\sigma$$ has quantifier depth at most $$n$$, we have played at most $$n$$ moves in the EF game $$G_n(A,B)$$. (If desired, finish this game by picking arbitrary moves for Spoiler and using Duplicator's winning strategy to respond.) Suppose $$\phi \equiv R(v_{i(1)},\dots,v_{i(k)})$$. Since we always used True's winning strategy to play in $$S_\sigma(A)$$, we know that $$R^A(a_{i(1)},\dots,a_{i(k)})$$ holds. 

Now observe that by the way we played the quantifier moves, we have the correspondences $$a_{i(1)} \mapsto b_{i(1)},\dots,a_{i(k)} \mapsto b_{i(k)}$$ in the play of the EF game $$G_n(A,B)$$. Since we always used Duplicator's winning strategy in $$G_n(A,B)$$, this correspondence is a finite partial isomorphism from $$A$$ to $$B$$, in particular $$R^A(a_{i(1)},\dots,a_{i(k)})$$ iff $$R^B(b_{i(1)},\dots,b_{i(k)})$$. Therefore, $$R^B(b_{i(1)},\dots,b_{i(k)})$$ and True wins the play of $$S_\sigma(B)$$. Since we always let False play freely in $$S_\sigma(B)$$, this shows that we have defined a winning strategy for True. Therefore, $$B \vDash \sigma$$, as required. 

---

[^1]: The original version of this post claimed to have a game-theoretic proof of the backward implication of Fraïssé's Theorem. Unfortunately, that proof was flawed and it has now been deleted.

[^2]: This proof was originally developed for a REU that I supervised at Cornell University in Summer 2008. It was originally posted on a blog that I used to maintain some years ago. Since I find this proof very interesting, I decided to salvage it and repost it here.

[^3]: The use of restricted formulas is a little bit of a cheat. The main reason for this was to simplify the definition of the semantic games. Negations can be incorporated in these games by adding the following clause to the definition of $$S_\phi$$: _if $$\phi \equiv \lnot\psi$$, then True and False swap roles and play the subgame $$S_\psi(A)$$_. The rest of the proof works exactly in the same way, except that because True and False swap roles every time they hit a negation, it becomes tricky to keep track of who is who.

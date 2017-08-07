---
title: Counting Birds...
date: 2011-10-15 17:35:30
permalink: /archives/335/
published: true
topics: [mathematical-philosophy]
tags: [Decidability, MathOverflow]
people: [Jorge Luis Borges, José Figueroa-O'Farrill, Mariano Suárez-Alvarez, Noam Elkies]
---
I've been thinking a bit more about the issues brought up in [Paris–Harrington and Typing]({{ "archives/107" | relative_url }}) and [Santa Exists!]({{ "/archives/317" | relative_url }})

These issues seem related to Borges's ornithological argument for the existence of God:[^1]

> Cierro los ojos y veo una bandada de pájaros. La visión dura un segundo o acaso menos; no sé cuántos pájaros vi. ¿Era definido o indefinido su número? El problema involucra el de la existencia de Dios. Si Dios existe, el número es definido, porque Dios sabe cuántos pájaros vi. Si Dios no existe, el número es indefinido, porque nadie pudo llevar la cuenta. En tal caso, vi menos de diez pájaros (digamos) y más de uno, pero no vi nueve, ocho, siete, seis, cinco, cuatro, tres o dos. Vi un número entre diez y uno, que no es nueve, ocho, siete, seis, cinco, etcétera. Ese número entero es inconcebible; ergo, Dios existe.[^2]

Although not intended to be taken seriously, Borges's argument rests on the decidability of equality for natural numbers. Here is a more mathematical example pointed out by Noam Elkies.[^3] Consider $$\R$$ as a vector space over $$\Q$$ and let $$V$$ be the subspace spanned by $$\set{1,e,\pi}$$. We know that $$\dim(V) = 2 \lor \dim(V) = 3$$, but which one is it? 

The Santa post raises the issue whether set membership should be decidable, which is even less clear than the issue with equality of natural numbers. However, the theorem there is easily modified to prove the existence of God in naïve set theory without assuming the decidability of set membership. 

The Paris–Harrington post raises a more subtle issue. It is pointed out there that the notion of relative largeness ($$\min(H) \leq \vert H \vert$$) used in the Paris–Harrington theorem is ill-typed in that it requires the comparison of two different types of natural numbers: the minimal element of a set of natural numbers and the cardinality of that set. In that case, type-theoretic reasons alone lead to the questionability of this comparison. 

Anyway, I don't have any new insights on decidability issues. I just wanted to point out the relationship between these posts, and I couldn't resist creating a tag for Jorge Luis Borges... 

---

[^1]: I would like to thank Mariano Suárez-Alvarez and José Figueroa-O'Farrill for reminding me of this argument in a [meta discussion](http://meta.mathoverflow.net/discussion/1158/) on MathOverflow regarding [question 77068](http://mathoverflow.net/questions/77068/).

[^2]: Translation by Mildred Boyer: "I close my eyes and see a flock of birds. The vision lasts a second or perhaps less; I don’t know how many birds I saw. Were they a definite or an indefinite number? This problem involves the question of the existence of God. If God exists, the number is definite, because how many birds I saw is known to God. If God does not exist, the number is indefinite, because nobody was able to take count. In this case, I saw fewer than ten birds (let’s say) and more than one; but I did not see nine, eight, seven, six, five, four, three, or two birds. I saw a number between ten and one, but not nine, eight, seven, six, five, etc. That number, as a whole number, is inconceivable; ergo, God exists."

[^3]: See the comment thread to the MathOverflow question [77068](http://mathoverflow.net/questions/77068/).

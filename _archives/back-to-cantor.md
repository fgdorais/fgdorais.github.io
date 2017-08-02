---
title: Back to Cantor?
date: 2012-12-28 19:05:07
permalink: /archives/1135/
published: true
categories: [category-theory, mathematical-philosophy, set-theory]
tags: [ETCS, ZFC]
people: [Bill Lawvere, Ernst Zermelo, Georg Cantor, Tom Leinster]
bibliography:
  - authors: [G. Cantor] 
    year: 1895
    title: "Beiträge zur Begründung der transfiniten Mengenlehre (Erster Artikel)"
    cite: "Math. Ann. 46, no. 4, 481-512"
    doi: "10.1007/BF02124929"
    zbl: "26.0081.01"
  - authors: [G. Cantor] 
    year: 1895
    title: "Beiträge zur Begründung der transfiniten Mengenlehre (Zweiter Artikel)" 
    cite: "Math. Ann. 49, no. 2, 207-246"
    doi: "10.1007/BF01444205"
    mr: "1510964"
    zbl: "28.0061.08"
  - authors: [F. W. Lawvere] 
    year: 1964
    title: "An elementary theory of the category of sets" 
    cite: "Proc. Nat. Acad. Sci. U.S.A. 52, no. 6, 1506–1511"
    doi: "10.1073/pnas.52.6.1506"
    mr: "0172807"
    zbl: "0141.00603"
    pmpermalink: /archives//"16591243"
    pmcpermalink: /archives//"PMC300477"
  - authors: [F. W. Lawvere]
    year: 2005
    title: "An elementary theory of the category of sets (long version) with commentary"
    cite: "Repr. Theory Appl. Categ. No. 11, 1-35"
    url: "http://www.tac.mta.ca/tac/reprints/articles/11/tr11abs.html"
    mr: "2177727"
  - authors: [T. Leinster]
    year: 2014
    title: "Rethinking set theory"
    cite: "Amer. Math. Monthly 121, no. 5, 403-415"
    arxiv: "1212.6543"
    doi: "10.4169/amer.math.monthly.121.05.403"
    mr: "3193723"
    zbl: "1345.03100"
  - authors: [E. Zermelo]
    year: 1908
    title: "Untersuchungen über die Grundlagen der Mengenlehre I"
    cite: "Math. Ann. 66, no. 2, 261–281"
    doi: "10.1007/BF01449999"
    zbl: "39.0097.03"
---
Set Theory has a fantastic and legendary history. At the end, it left us with ZFC, which is currently recognized as _the_ foundation of mathematics. This state of affairs is arguably one of the best possible outcomes for the foundational crisis that plagued mathematics in the early 20th century. However, the choice to adopt ZFC was by no means unanimous, dissent has always been present, often with good reason. Whether propelled by inertia or by sheer power, for better or for worse, ZFC is now approaching 100 years of reign as the foundation of mathematics. 

The most vocal opposition to ZFC has been from Category Theory (and its relatives). Indeed, the basic tenets of ZFC are very foreign to Category Theory and the various hoops that one has to go through to formalize Category Theory in ZFC quickly turn into major annoyances. The same issues arise elsewhere but Category Theory distinguishes itself from other areas by the fact that it regularly runs into genuine foundational issues, so the frictions that other areas feel become irritations for Category Theory. As expected, this irritation has led to a lot of heated debates and frustrations, but the more important outcome for a logician like me is a variety of interesting alternatives to ZFC. 

Tom Leinster (2014) recently wrote a nice account of one of these alternatives, Lawvere's Elementary Theory of the Category of Sets (ETCS) (Lawvere 1964, 2005). The paper is intended for a general mathematical audience; the goal is to show that foundations that are friendly to Category Theory aren't necessarily bad and may even be beneficial for everyone. Since discussions of this kind have been known to degenerate quickly, I wasn't sure whether to participate in the [discussion of this paper](http://golem.ph.utexas.edu/category/2012/12/rethinking_set_theory.html) at the n-Category Café. Tom was visibly intent on keeping the discussion civilized and so I decided to jump in. I'm glad I did since the discussion was very beneficial for me: it forced me to look more closely at ETCS (and other alternative foundations) and to think very carefully about what it takes to be a foundation of mathematics. 

The main difference between the two approaches is that ZFC is a material set theory whereas ETCS is a structural set theory. There is a lot to say about the differences, briefly: 

 * Material set theory is based on the membership relation, which is extensional. A difference between two sets must be explained by an element of one which is not in the other. Some material set theories allow atoms but in ZFC, everything is a set. Thus the fact that this element is not an element of the other is explained similarly by elements of that element, or elements of elements of the other set, and so on and so forth. The end result is that a large set in ZFC necessarily comes with a lot of extra baggage which is generally irrelevant to its intended use. The advantage of this approach is the elegant simplicity by which complexity is built from nothing using simple tools.

 * Structural set theory is based on external relationships between sets, whose elements are completely anonymous. In ETCS, sets don't even have elements per se, everything is expressed in terms of functions between sets. Instead, there is a distinguished singleton set $$1$$ and functions $$1 \to A$$ are used to point at the elements of $$A$$. Consequently, sets in ETCS cannot directly be used as data structures in the usual way since we can't put things in or take things out of a set (without additional bagage). However, since two sets of the same size are essentially indistinguishable, isomorphic structures may as well be equal, which is a definite advantage of this approach.
  
Note that both setups can be used for all the same basic tasks of everyday mathematics; it's the amount of baggage associated with each task that varies. There is much gain for a category theorist to work in ETCS and much pain to work in ZFC. Similarly, there is much gain for a set theorist to work in ZFC and much pain to work in ETCS. In general, mathematicians work with sets both materially and structurally depending on context, so both approaches capture some aspects of mathematical thought. 

Since ZFC lies at one extreme of the material-structural spectrum, there is a genuine need for alternative foundations to better accommodate the structural view. Thus came ETCS, which is at the other extreme of that spectrum. It's very fortunate that there is a very nice translation between ETCS+R (ETCS with replacement) and ZFC. Indeed, one would hope that both could cohabitate peacefully and provide mathematicians with sound foundations for the two points of view that they use every day. Though I was raised as a set theorist and I tend to think from the material point of view, I am sympathetic to my category theorist friends and I have been supportive of Tom and others in their effort to provide a sound structural alternative to ZFC. 

There are some problems with this sort of compromise where material and structural set theories cohabitate as equal alternative foundations. One of the important roles of a foundational theory is to act as a communication channel between mathematicians: agreement on a few basic concepts is necessary to exchange ideas. It's true that most communication happens between mathematicians with common ideas, but even category theorists and set theorists need to talk from time to time. I mentioned several consequences of this at the Café and stressed the fundamental importance of the translation between the material and structural perspectives. 

After thinking about this more, I realized that this kind of cohabitation model is actually not the best possible way to accommodate both the material and the structural perspective at the foundational level. Indeed, what we end up doing is moving all the annoyances from both sides into the translation between the two. I'm worried that the translation, even if it is very nice, would simply become an irritating barrier between materialists and structuralists and actually harm communication between both. Even worse is that centrists, who like to blend material and structural views, are now stuck with all the annoyances. 

Simultaneously with all this, I was looking back to the root of the problem and reread papers from the very beginning of set theory. The primary goal was to understand how the material perspective dominated at the outset and ultimately led to the general adoption of ZFC as _the_ foundation of mathematics. To my surprise, I realized that the structural perspective was actually present at that time, though not as sophisticated and clearly delineated as it is now. Cantor's original account of cardinal arithmetic (Cantor 1895, 1897) was actually very structural as can be seen in his definition of cardinal number: 

> Every set $$M$$ has a definite "power," which we will also call its "cardinal number." 
> 
> We will call by the name "power" or "cardinal number" of $$M$$ the general concept by which, by means of our active faculty of thought, arises from the set $$M$$ when we make abstraction of the nature of its various elements $$m$$ and of the order in which they are given. 
> 
> We denote the result of this double act of abstraction, the cardinal number or power of $$M$$, by $$\overline{\overline{M}}$$. 
> 
> Since every single element $$m$$, if we abstract from its nature, becomes a "unit," the cardinal number $$\overline{\overline{M}}$$ is a definite set composed of units, and this number has existence in our mind as an intellectual image or projection of the given set $$M$$.[^1]

Thus, to Cantor, the cardinal number of a set is just its purely structural view, where the elements lose their individual identity. Cantor's structural views are visible throughout. 

> Any element $$m$$ of a set $$M$$ can be thought to be bound up with any element $$n$$ of another set $$N$$ so as to form a new element $$(m,n)$$; we denote by $$(M.N)$$ the set of all these pairs $$(m,n)$$ and call it the "set of pairs of $$M$$ and $$N$$".[^2]

Cantor's pairs $$(m,n)$$ have no implied structure other than the two coordinates[^3] and the product $$(M.N)$$ is actually only defined up to isomorphism! 

It's still not clear to me exactly how the material view of sets came to dominate. Cantor structural views were criticized by others, such as Zermelo who proposed the first materialist account of Set Theory (Zermelo 1908). Perhaps the prevalence of the materialist view is a direct response to the foundational crisis, where the extra baggage carried by material sets brought additional comfort as each set came with the full history leading to its existence according to the iterative conception of material sets. Speculations aside, the predominance of the material view is becoming increasingly frustrating to many and it is time to think how to accommodate the structural view on an equal footing. 

Rather than having multiple alternate foundations with bridges between them, it would be much more satisfactory to have a greater overarching foundation similar to Cantor's universe that comprises both the material and structural views. This way, ZFC and ETCS can more easily be seen for what they really are: _formal reductions_ of the mathematical universe to a simplified context which are nevertheless strong enough to provide reasonable interpretations for all common mathematical constructs. Whenever they desire, category theorists could then preface their papers with a phrase like: "Without loss of generality, we work in **Set**, the purely structural part of the universe." Similarly, set theorists could opt to work in **V**, the purely material part of the universe. In fact, this is close to current practice where mathematicians freely borrow from one side or the other as they please. 

This kind of unified foundation is clearly one of the best possible outcomes for everyone. The problem is that it is not currently an option: there is no proposal for an alternative foundation that attempts to fully accommodate both the structural and the material points of view. I long thought that such a foundation would necessarily have to be too complex and therefore unusable. However, after rereading Cantor and seeing how he happily marries the two points of view in his universe, I now think that there might be a reasonably simple way to do this. I therefore conclude with a call to action, a call for structuralists, materialists and all other mathematicians in between to work together and find a reasonable unified foundation where structural sets and material sets happily live together as equals. 

---

[^1]: (Cantor 1895, pp. 481–-482)
      > Jeder Menge $$M$$ kommt eine bestimmte ,Mächtigkeit' zu, welche wir such ihre ,Cardinalzahl' nennen.
      > ,Mächtigkeit' oder ,Cardinalzahl' von $$M$$ nennen wit den Allgemeinbegriff, welcher mit Hülfe unseres activen Denkvermögens dadurch aus der Menge $$M$$ hervorgeht, dass von der Beschaffenheit ihrer verschiedenen Elemente $$m$$ und von der Ordnung ihres Gegebenseins abstrahirt wird.
      > Das Resultat dieses zweifachen Abstractionsacts, die Cardinalzahl oder Mächtigkeit von $$M$$, bezeichnen wit mit $$\overline{\overline{M}}$$.
      > Da aus jedem einzelnen Elemente $$m$$, wenn man yon seiner Beschaffenheit absieht, eine ,Eins' wird, so ist die Cardinalzahl $$\overline{\overline{M}}$$ selbst eine bestimmte aus lauter Einsen zusammengesetzte Menge, die als intellectuelles Abbild oder Projection der gegebenen Menge $$M$$ in unserm Geiste Existenz hat.

[^2]: (Cantor 1895, p. 485)
      > Jedes Element $$m$$ einer Menge $$M$$ lässt sich mit jedem Elemente $$n$$ einer andern Menge $$N$$ zu einem neuen Elemente $$(m, n)$$ verbinden; für die Menge aller dieser Verbindungen $$(m, n)$$ setzen wit die Bezeichnung $$(M.N)$$ fest. Wir nennen sie die ,Verbindungsmenge von $$M$$ und $$N$$'.

[^3]: The encoding of pairs in Set Theory was first done years later by Weiner and eventually simplified by Kuratowski into its now customary form $$(m,n) = \set{\set{m},\set{m,n}}$$. Even Zermelo didn't have such an encoding and he was only able to form the product of two disjoint sets in his original formulation of Set Theory (Zermelo 1908).


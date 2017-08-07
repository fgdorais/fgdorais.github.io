---
title: On computing complex square roots
date: 2011-10-22 16:15:34
permalink: /archives/377/
published: true
topics: [computability, reverse-math]
---
What could possibly be interesting about complex square roots? That's what I thought until very recently when I realized that complex square roots are significantly more difficult to compute than real square roots. Let me explain why by putting you in a context where you need to teach students how to compute complex square roots... 

There is not much to computing complex square roots; it just takes a little practice to get used to it. So you just need to assign a few homework problems to make sure that students practice enough. How many problems should you assign: one, two, five, twelve, or seventeen? There is no upper bound on how many practice problems are enough, so perhaps you should assign infinitely many problems? 

Now, you may find the very idea of an infinite problem set objectionable, but they are in fact very common. Here is one: 

_For every positive integer $$n$$, find a square root of $$n+i$$._

Some might find the following problem infinite too: 

_Find a square root of $$\pi + i\sqrt{17}$$._

Here, $$\pi + i\sqrt{17}$$ is a finite description of a complex number, the complex number being described is actually an infinite object. Hopefully this is enough to convince you that infinite problem sets are not completely unreasonable. Of course, you do need to set some ground rules so that students can at least understand the what the problem set is asking and that they know what a solution entails. Here are the rules: 

  * Real numbers are represented by rapidly convergent sequences of rational numbers. That is, a real number is a function $$x:\N\to\Q$$ such that $$\vert x(s) - x(t)\vert \leq 2^{-s}$$ for all natural numbers $$s \lt t$$.
  * Complex numbers are pairs $$z = x + iy$$, where $$x$$ and $$y$$ are real numbers represented by rapidly convergent sequences of rational numbers. The real and imaginary parts of $$z$$ will also be denoted $$\Re(z)$$ and $$\Im(z)$$ when convenient.
  * An infinite problem set is an uniformly computable sequence $$\seq{z_n}_{n=0}^\infty$$ of complex numbers. That is, there is a Turing machine which, on input $$n, s$$, will give me the rational numbers $$x_n(s)$$ and $$y_n(s)$$, where $$z_n = x_n + iy_n$$ as above.
  * A solution to the infinite problem set $$\seq{z_n}_{n=0}^\infty$$ is an uniformly computable sequence $$\seq{w_n}_{n=0}^\infty$$ of complex numbers such that $$z_n = w_n^2$$ for each $$n$$.

Grading such a problem set can be a daunting task, but let's not worry about the aftermath. A more interesting question is: 

_Does every infinite problem set have a solution?_

Indeed, it would be unreasonable to assign a problem set that students can't possibly solve! 

If the problem set were specifically asking for the principal square roots then you could easily devise an infinite problem set that has no solution. Recall that the principal square root of $$z = re^{i\theta}$$ is $$\sqrt{r}e^{i\theta/2}$$ where $$-\pi \lt \theta \leq \pi$$ and $$\sqrt{r}$$ is the nonnegative square root of the nonnegative real number $$r$$. In other words, the principal branch agrees with the positive square root on the positive real axis, and it has a branch cut along the negative real axis. 

**Theorem D.** _Given any computably enumerable set $$A$$, there is a uniformly computable sequence of nonzero complex numbers $$\seq{z_n}_{n=0}^\infty$$ such that the corresponding sequence $$\seq{w_n}_{n=0}^\infty$$ of principal square roots computes $$A$$._

Proof. Let's assume that $$A$$ is infinite and let $$\seq{a_m}_{m=0}^\infty$$ be a computable enumeration of $$A$$, without repetitions. Define the sequence $$\seq{z_n}_{n=0}^\infty$$ by
^
$$z_n = \begin{cases} -1 - 2^{-m}i & \text{when \(n = a_m\),} \cr -1 & \text{when \(n \notin A\).} \end{cases}$$ 
^
To see that this is uniformly computable, recall that $$z_n = x_n + iy_n$$ where $$x_n$$ and $$y_n$$ are two rapidly convergent sequences of rationals. The first sequence $$x_n$$ is constant with value $$-1$$, which is definitely computable. The second sequence $$y_n$$ can be defined by
^
$$y_n(s) = \begin{cases} 2^{-m} & \text{when \(m \leq s\) and \(a_m = n\),} \cr 0 & \text{otherwise.} \end{cases}$$
^
Because we require $$m \leq s$$, we only have finitely many possible $$m$$ to check in order to determine which case to use. So $$y_n$$ is computable too. Since this process is uniform in $$n$$, the sequence $$\seq{z_n}_{n=0}^\infty$$ is in fact uniformly computable. 

Now suppose $$\seq{w_n}_{n=0}^\infty$$ is the corresponding sequence of principal square roots. Then we must have $$\Im(w_n) \lt 0$$ when $$n \in A$$, and $$\Im(w_n) \gt 0$$ when $$n \notin A$$. So we can use the sign of $$\Im(w_n)$$ to determine whether or not $$n$$ is in the range of $$f$$. More precisely, if $$w_n = u_n + iv_n$$ then we can look at the terms of the rapidly convergent sequence $$v_n$$ until we find $$s$$ such that $$\vert v_n(s) \vert \gt 2^{-s}$$; such an $$s$$ will eventually be found since we know that $$v_n \neq 0$$. Then the sign of $$v_n(s)$$ will tell us whether $$n \in A$$ or not. Therefore, $$A$$ is computable from $$\seq{w_n}_{n=0}^\infty$$. QED 

Choosing $$A$$ to be the halting set will trick many students, but solutions to infinite problem sets do not require principal square roots. Some students might use a slightly different convention and define the principal square root of $$-1$$ to be $$-i$$ instead of $$i$$. In that case, the above trick doesn't work since such a student will give me a sequence of square roots $$\seq{w_n}_{n=0}^\infty$$ where $$\Im(w_n) \lt 0$$ for every $$n$$. However, it turns out that you can design an infinite problem set that will simultaneously deal with all such variations. Let us say that $$w$$ is a weakly principal square root of $$z$$ if $$w$$ is the principal square root, or $$z$$ is a negative real number in which case $$w$$ can be any of the two square roots. 

**Theorem C.** _For every pair $$A$$, $$B$$ of disjoint computably enumerable sets, there is a uniformly computable sequence $$\seq{z_n}_{n=0}^\infty$$ of nonzero complex numbers such that any corresponding sequence of weakly principal square roots computes a separating set for $$A$$ and $$B$$._

Proof. Let $$\seq{a_m}_{m=0}^\infty$$ and $$\seq{b_m}_{m=0}^\infty$$ be computable enumerations of $$A$$ and $$B$$, respectively. Similar to the proof of Theorem A, define
^
$$z_n = \begin{cases} -1 + 2^{-m}i & \text{when \(a_m = n\),} \cr -1 - 2^{-m}i & \text{when \(b_m = n\),} \cr -1 & \text{when \(n \notin A \cup B\).} \end{cases}$$
^
Suppose we have a corresponding sequence $$\seq{w_n}_{n=0}^\infty$$ of weakly principal square roots. It must be that $$\Im(w_n) \gt 0$$ (in fact, $$\Im(w_n) \approx 1$$) when $$n \in A$$, and $$\Im(w_n) \lt 0$$ (in fact, $$\Im(w_n) \approx -1$$) when $$n \in B$$. We could have $$w_n = \pm i$$ when $$n \notin A \cup B$$, but we still know that $$\Im(w_n) \neq 0$$. We can still use the sign of $$\Im(w_n)$$ to separate $$A$$ and $$B$$ since 
^
$$A \subseteq \set{n \in \N : \Im(w_n) \gt 0}, \quad B \subseteq \set{n \in \N : \Im(w_n) \lt 0},$$
^
and the two supersets are complementary $$\Sigma^0_1$$ sets. QED 

Choosing $$A$$ and $$B$$ to be an inseparable pair of computably enumerable sets, many of your students will be unable to solve this problem set. That is, you will trick all your students who don't realize that the choice of branch cut for square roots is completely arbitrary. Any student that chooses the branch cut at an angle of $$\pi/2$$ instead of $$\pi$$ will have no trouble solving this infinite problem set. 

It is not difficult to adapt the above to simultaneously deal with a bunch of plausible branch cuts $$\pi, \pi/2, -\pi/2, \pi/3, \ldots$$ However, you can't deal with all possible branch cuts. While there are only countably many computable branch cuts that students could choose from, but there is no computable enumeration of all of these choices. In fact, a clever student can always pick a branch cut that you haven't considered. 

**Theorem B.** _If $$\seq{z_n}_{n=0}^\infty$$ is a uniformly computable sequence of nonzero complex numbers, then there is a corresponding uniformly computable sequence $$\seq{w_n}_{n=0}^\infty$$ such that $$w_n^2 = z_n$$ for every $$n$$._

Proof. The trick is to select a branch cut angle $$\theta$$ that avoids all the numbers $$z_n$$. This can be done by a trisection argument. Initially set $$\theta_0^{-} = -1$$ and $$\theta_0^{+} = 1$$, say. Once $$\theta_n^{\pm}$$ have been chosen, set $$\delta_n = (\theta_n^{+}-\theta_n^{-})/3$$ and compute $$z_n$$ to enough precision that you can determine that $$z_n/\vert z_n \vert$$ does _not_ belong to one of the three sets 
^
$$\set{e^{i\theta} : \theta_n^{-} \leq \theta \leq \theta_n^{-} + \delta_n},$$
^
 
^
$$\set{e^{i\theta} : \theta_n^{-} + \delta_n \leq \theta \leq \theta_n^{+} - \delta_n},$$
^
 
^
$$\set{e^{i\theta} : \theta_n^{+} - \delta_n \leq \theta \leq \theta_n^{+}}.$$
^
 In the first case set $$\theta_{n+1}^{-} = \theta_n^{-}, \theta_{n+1}^{+} = \theta_n^{-} + \delta_n$$; in the second case set $$\theta_{n+1}^{-} = \theta_n^{-} + \delta_n, \theta_{n+1}^{+} = \theta_n^{+} - \delta_n$$; in the third case set $$\theta_{n+1}^{-} = \theta_n^{+} - \delta_n, \theta_{n+1}^{+} = \theta_n^{+}$$. 

This process defines two rapidly convergent sequences of rational numbers $$\seq{\theta_n^{\pm}}_{n=0}^\infty$$ that represent the same real number $$\theta$$. The branch angle $$\theta$$ so defined is computable and avoids all the numbers $$z_n$$. So there is no problem computing the principal square roots $$w'_n$$ of the numbers $$z'_n = z_n/e^{i\theta}$$. The solution to the infinite problem set $$\seq{z_n}_{n=0}^\infty$$ is then $$\seq{w'_ne^{i\theta/2}}_{n=0}^\infty$$. QED 

Now the fact that the complex numbers $$z_n$$ were nonzero was very important in this argument. A student using this strategy will stall at any stage $$n$$ where $$z_n = 0$$. However, some very clever students will anticipate this possibility and avoid this problem. 

**Theorem A.** _If $$\seq{z_n}_{n=0}^\infty$$ is a uniformly computable sequence of complex numbers, then there is a corresponding uniformly computable sequence $$\seq{w_n}_{n=0}^\infty$$ such that $$w_n^2 = z_n$$ for every $$n$$._

Proof. Although there may be no computable way to determine which $$z_n$$ are zero, the set $$A = \set{n \in \N : z_n \neq 0}$$ is computably enumerable since $$z_n \neq 0$$ is a $$\Sigma^0_1$$ statement. For simplicity, let's assume that this set is infinite and let $$\seq{a_k}_{k=0}^\infty$$ be a computable enumeration of this set (without repetitions). We can then use the method from Theorem B to compute a sequence of square roots $$\seq{w'_k}_{k=0}^\infty$$ for the subsequence $$\seq{z_{a_k}}_{k=0}^\infty$$. The desired sequence of square roots is then
^
$$w_n = \begin{cases} w_k & \text{when \(a_k = n\),} \cr 0 & \text{when \(n \notin A\).} \end{cases}$$
^ 

To see that the sequence $$\seq{w_n}_{n=0}^\infty$$ is uniformly computable, recall that $$w'_k = u'_k + iv'_k$$ where $$u'_k$$ and $$v'_k$$ are rapidly convergent sequences of rational numbers. So we can define $$w_n = u_n + iv_n$$ where 
^
$$(u_n(s),v_n(s)) = \begin{cases} (u'_k(s),v'_k(s)) & \text{when \(k \leq p(n,s)\) and \(a_k = n\),} \cr (0,0) & \text{otherwise.} \end{cases}$$
^
These will be a rapidly convergent sequences of rationals provided that the computable function $$p(n,s)$$ is suitably chosen. 

To define $$p(n,s)$$ we need to make sure that the first time $$s$$ where $$(u_n(s),v_n(s)) \neq (0,0)$$, we don't have $$\vert u_n(s) \vert \gt 2^{-s}$$ or $$\vert v_n(s) \vert \gt 2^{-s}$$. Should this happen, we necessarily have $$\vert z_n\vert \gt 4^{-s}$$. So we can look at $$z_n(2s+2) = x_n(2s+2) + iy_n(2s+2)$$. Since $$\vert z_n - z_n(2s+2) \vert \leq 4^{-s}/2$$, if $$\vert z_n(2s+2) \vert \leq 4^{-s}/2$$ then $$\vert z_n \vert \leq 4^{-s}$$ and we're safe to define $$(u_n(s),v_n(s)) = (0,0)$$. Otherwise, we know that $$z_n \neq 0$$ so that $$n = a_k$$ for some $$k$$. Therefore, we can define $$p(n,s) = 0$$ when $$\vert z_n(2s+2)\vert \leq 4^{-s}/2$$, and $$p(n,s) = k$$ such that $$a_k = n$$ when $$\vert z_n(2s+2)\vert \gt 4^{-s}/2$$. QED 

So every infinite problem set does have a solution! Moreover, any student that reaches the solution of Theorem A clearly understands complex square roots (and basic computability theory!), so infinite problem sets might not be such a bad idea after all... 

So what does this have to do with reverse mathematics? Well, the four theorems above can be used to show that: 

  * It is provable in $$\mathsf{RCA}_0$$ that every infinite sequence of complex numbers has a corresponding sequence of complex square roots.
  * It is not provable in $$\mathsf{RCA}_0$$ that every infinite sequence of complex numbers has a corresponding sequence of principal square roots. In fact, this $$\Pi^1_2$$ statement is equivalent to $$\Sigma^0_1$$-comprehension (i.e. $$\mathsf{ACA}_0$$).
  * It is also not provable in $$\mathsf{RCA}_0$$ that every infinite sequence of complex numbers has a corresponding sequence of weakly principal square roots. In fact, this $$\Pi^1_2$$ statement is equivalent to $$\Sigma^0_1$$-separation (i.e. $$\mathsf{WKL}_0$$).

In fact, there is nothing very special about square roots. The same applies to the inverse of any nonlinear polynomial over $$\C$$. Therefore, you must be very careful when using the Fundamental Theorem of Algebra in $$\mathsf{RCA}_0$$...

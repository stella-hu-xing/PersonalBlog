---
title: Big O Theory
date: 2017-08-07 12:58:33
tags: BigO
---
#Big O time is the language and metric we use to describe the effciency of algorithms.#

### Big O, Big Theta and Big Omega

Academics use big O, Θ (big theta) and Ω (big omega)to describe runtimes.

* O: 
In academia, big O describes an upper bound on the time.
For example: an algorithm that prints all values in an array could be described as O(N),but it could also be described as O(N^2),O(N^3). The algorithm is at least as fast as each of there, therefore tehy are upper bounds on the runtime. Similar to "less-than-or-equal-to" relationship.

首先，这是我们在学习工作中描述算法时间复杂度用的最普遍的符号。它是渐进上界，其作用是将我们得到的算法在最坏情况下（worst case）时间复杂度表达式简化成对应的多项式（比如n^2等）。所以在我们证明的过程中，目的是证明我们的式子要“小于等于”目标多项式。

* Ω(big-Omega)：
In academia, Ω is the equivalent concept but for lower bound.
Printing the values in an array is Ω(N) as well as Ω(logN) and Ω(1). But you know it won't be faster than those runtimes.
这个符号我们一般用的比较少，一个是因为我们一般不会去考虑算法运行时间的下界，另一个是因为下界时间也不好证明。没错，他就是渐进下界，其作用是将我们得到的算法在最好情况下（best case）时间复杂度表达式简化成对应的多项式（也比如n^2等）。所以在我们证明的过程中，目的是证明我们的式子要“大于等于”目标多项式。

* Θ(big-theta)：
In academia, Θ means both O and Ω. That is , an algorithm is Θ(N) if it is both O(N) and Ω(N). Θ gives a tight bound on runtime. 
如果O和Ω可以用同一个多项式表示，那么这个多项式就是我们所要求的渐进紧的界了。其作用是将我们可以较准确地得到算法的时间复杂度表达式对应的多项式（也比如n^2等）。所以在我们证明的过程中，目的是证明我们的式子要“等于”目标多项式。

#### Drop the constants
Big O just describes the rate of increase.
SO we drop the constants in runtime. An algorthm that one might hase described as O(2N) is actually O(N).
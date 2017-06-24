---
layout: post
title: "Cryptography Week 2: Psuedorandomness"
tag: [Cryptography, Coursera]
category: Learning
---

Randomness is not a property of a string, but a property of the set of strings
Distribution of strings that assign probability to each string
A particular string is pseudorandom iff it can't be distinguished from a uniform or a random string

BUT this doesnt make sense, you need psuedorandomNESS, a property of a distribution on strings

***

Historically:
Fix D on Nbit Strings
D is considered pseudorandom iff it passed statistical tests, essentially, when we sample X according to D, first bit of X should be 1 half the time

However, lets say the attacker chooses a different statistical test then whats in our battery of tests, one that CAN differentiate. In that case, its no longer secure.

The cryptography definition : Pseudorandomness iff passes all efficient statistical tests

Therefore:
For every value of security parameter n:
We're looking at distributions over string of length, over strings of length p(n)

for now, p(n)=n, but n^2 is better for future lectures

***

### Pseudorandom Generators: PRG

G= efficient deterministic algorithm that expands a short, uniform seed or input into a longer pseudorandom output.
Essentially: Given short input, convert to longer output that has properties of pseudorandomness.

useful if small amount of random bits but want lots of super random looking bits

G naturally defines a sequence of distributions

What this means is that for all A(PPT attackers), theres a negligible E such that "Given G(x), A cannot distinguish if it is G(x) or a uniform string y!
|Difference| < E

***
### The PsuedoRandom One-Time Pad

Key of Length N
Plug into G
Get out P (Longer then N)
Use P as the Key
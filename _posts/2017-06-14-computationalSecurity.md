---
layout: post
title: "Cryptography Week 2: Computational Security"
tag: [Cryptography, Coursera]
category: Learning
---

### Until now: Perfect Secrecy in face of Unlimited Computational power
Relax certain parameters to get a more realistic version, known as Computational Secrecy
Parameters that are weakened are:

Allow Security to fail with some tiny probability (leak the plaintext)
ex. 2^60 chance of failing, which would be once in a 100 billion years

Attackers have a limit on computer power (efficiency)
ex. say 1 test of a key per a clock cycle of a processor (Which is very optimistic)
then
desktop: searches 2^57 keys/year
supercomputer: searches 2^80 keys/year
a supercomputer thats been searching since big bang : 2^112 keys so far

Therefore restrict key space to 2^128

***

### Define Security as Perfect Indistinguishability:

Encryption Scheme &&&
m0      m1
choose either
encrypt with k to get C
give C to attacker, ask if it m0 or m1 orginally

If attacker can guess right only 1/2 of the time (has to take random guess) , then perfectly indistinguishable , which is an alternate way to define perfect secrecy

### Computer Secrecy:
Pr[Privka&&& =1]<0.5+E
You restrict the scheme to the time, and the chance to E
VERY sensitive to the type of computer being used
Asymptotic notion of security

***

### Security can fail at most with the probability Epsilon
time is at most t
Introduce n, a new security parameter
View it as allowing parties to choose a level of security
for now, just look at n as a keylength

Now assume attacker knows N
Check runtimes of all parties and success probability of attacker, in terms of n
How does the runtime change as n changes?

### All these different equations are polynomially bounded, but not necessarily polynomials themselves

For the success value of the attacker,
f is negligible iff for every p, there is a bound to N such that f(n)< 1/p(n) for all n larger then current

F is negligible if its asymptotically smaller then any inverse poly
ex poly n * 2^-cn

Notion of equations of efficient attackers with probabilistic polynomial time algorithms (PPT) comes from complexity theory

Problems that can be solved efficiently can be solved in polynomial times

#### Therefore scheme is secure if any poly function is bounded by 1/2 + negligible function

#### encryption doesn't hide plaintext length!

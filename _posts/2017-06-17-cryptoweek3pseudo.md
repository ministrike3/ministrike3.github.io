---
layout: post
title: "Cryptography Week 3: Pseudorandom Functions and Block Ciphers"
tag: [Cryptography, Coursera]
category: Learning
---

F is a pseudorandom function if Fk, for a uniform key k which is an element {0,1}^n, is indistinguishable from a uniform function Func_n.

Let F be a length preserving, keyed function:

F is a keyed permutation iff:
F_k is a bijection for every k
F_k^-1 is efficiently computable

F is a psuedorandom permutation if F_k, for a uniform key which is an element {0,1}^n, is indistinguishable from a uniform permutation.

### Block Cipher: Practical Construction of pseudorandom permutation

No asypmptotic, and hard to distinguish f_k from a uniform f element perm even for attackers running in time = 2^n

AES is a standardized block cipher
block length: 128 bit
key length: 128,192, and 256 bit (2^x security so even a key length of 128 is fine)

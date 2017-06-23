---
layout: post
title: "Cryptography Week 3: CPA-Secure Encryptions from PRF's"
tag: [Cryptography, Coursera]
category: Learning
---

### Notes on block ciphers:
For large enough n, random permutation is indistinguishable from random functions, therefore, block ciphers are good pseudo-random functions,
Assuming you have a n-bit  key k that you put into a block cipher, you can encrypt a n-bit message m. This is the same as the One Time Pad; the benefit here is that because the block cipher is pseudo-random, you can encrypt multiple messages with the same key.
******
### Currently the trouble with this encryption scheme is that encrypting an n-bit string results in a 2n-bit cipher text:

an n-bit R and n-bit key are plugged into the block cipher
the pseudo-random output of the block cipher is XOR'd with m
R & the output of the XOR are sent as the 2n-bit ciphertext
*****
You can mitigate this in several ways; the first step is to break the message into many small blocks to allow for an arbitrary length of message.
*****
### Modes of Operation:
Stream Ciphers (not covered in this course):
Synchronized and Unsynchronized

#### Block ciphers:

Counter Mode, or CTR:
I have a bunch of n-bit blocks
Define an n-bit number c0 (First block in cipher text)
c0+i is used as input for pseudo-random, where i is the # of the block in the message
so final message is original message+n bits long

Cipher Block Chaining, or CBC mode:
Define an n-bit number c0(first block in cipher text)
XOR with m1
Xor c1 with m2 -> c2, c2 with m3 ->c3, and so on

Never use Electronic Code book, EBC mode:
Was defined before true security notions were understood
use m1 to encrypt m2 and so forth
if two blocks are the same in a long plaintext, it won't work because in long amounts there will be repeated ciphertext
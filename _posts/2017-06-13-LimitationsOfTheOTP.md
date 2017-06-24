---
layout: post
title: "Cryptography Week 2: Limitations of the One Time Pad"
tag: [Cryptography, Coursera]
category: Learning
---

A real world application of the 1timepad is the Red Phone of the 1980's, with suitcases full of bits flown between moscow and DC

***

### Limitations:
Key is as long as message
Only secure if each key is used only once
Therefore
total length of keys shared must = total length of all messages ever want to send

***

### Break if 2 messages to encrypt using one key
m1 -> &1
m2 -> &2

&1 XOR &2 = m1 XOR m2

Although it might not be useful, it  rules out perfect secrecy

### However it is useful

this reveals where m1 and m2 differ
If plaintext are long can apply frequency analysis
All letters begin with 01
Space is 00
XOR of 2 letters, get a byte with 00 prefix
XOR of letter and space, get a byte with 01 prefix
XOR of 2 spaces, get 00, but not common
Therefore, can guess what is in each location
Punctuation can mess this up but its uncommon so don't worry about it

### Using this method letters are guessable
not just 1 time pad, but inherent to many schemes
One time pad is optimal as far as length of key goes
Now relax the definition of perfect secrecy, obtain much more applicable ideas 

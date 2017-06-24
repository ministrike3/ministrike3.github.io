---
layout: post
title: "Cryptography Week 3: Stronger Security Notions"
tag: [Cryptography, Coursera]
category: Learning
---

#### Recall the 2 limitations of perfect security:
Key must be as long as the message
Key can only be used once

The One Time Pad meets both of these limitations, but is clearly super inconvenient

#### Computer Security:
We lose the first limit of perfect security by going to compsec, which leads to the pseudo OTP, a long message with a short key.

How do we lose the second limitation?
Develop a security definition where multiple messages encrypt the same key
The minimum for modern cryptography is security against chosen plaintext attacks (CPA)

***

Encryption Scheme : pi
Key gen :                   k
Attacker:                   A
A submits m, gets back Cm encrypted with k by Oracle
Oracle outputs m0 and m1
Oracle encrypts 0 and 1 and outputs to A
Attacker tests Oracle somemore
A outputs 0 or 1 : this is a guess that m0 or m1 was encrypted

If the probability that this guess is right is 50 percent or less (ie a random guess) then that means the encryption scheme is secure

### CPA security is impossible to achieve using deterministic encryption schemes; it needs to be randomized